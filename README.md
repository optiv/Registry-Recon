# Registry-Recon
Cobalt Strike Aggressor Script that Performs System/AV/EDR Recon.

Author: Jess Hires

## Description
As a red-team practitioner, we are often using tools that attempt to fingerprint details about a compromised system, preferably in the most stealthy way possible. Some of our usual tooling for this started getting flagged by EDR products, due to the use of Windows CLI commands. This aggressor script aims to solve that problem by only probing the system using native registry queries, no CLI commands.

## Setup
Simply load `reg.cna` into Cobalt Strike using the Script Manager. Then right-click on the beacon you want to run registry recon on, and choose `RegEnum`.

## How does this work?
Primarily, using Cobalt Strike's `breg_query` and `breg_queryv` functions. Then, all beacon output is hijacked with `beacon_output`, looking for specific values. When a positive match is made, the output will be highlighted in the beacon output. Since there is no `beacon_output_reg` or something similar, like `beacon_output_ls` and `beacon_output_ps`, all output must be captured for parsing.

## What if my AV/EDR product isn't detected? / How can I help?
This is expected. We couldn't test for every AV/EDR solution, and we knew that many would be missing. You can help us out by submitting a GitHub issue including the following info:
* If this is a System/AV/EDR entry
* The name of the product
* Relevant registry entries that can be used to positively ID the product
