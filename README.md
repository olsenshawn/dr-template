# dynamic-routing-capsule-template

## quickstart

Developing a capsule in codoecean is a lot like developing in a local git repository: 
- you can clone from a remote (github) to get started
- changes are tracked as commits, with commit messages
- changes can be pushed or pulled from a remote

This template sets up a starting point for DR analysis capsules, with pinned dependencies for [`npc_sessions`](https://github.com/AllenInstitute/npc_sessions) to make initial capsule building faster. 

It also contains a post-install script that updates to the latest version of `npc_sessions` **on every run or workstation launch**: the package is undergoing heavy development, so the latest version should always be used - just be aware that things may change (even within an NWB file).

### for throw-away analysis/exploration
get up and running quickly with DR analysis by *cloning this repo* in CodeOcean:
- open codeocean in a new tab [here](https://codeocean.allenneuraldynamics.org/).
- hit the `+` icon (top left) and select `"New Capsule" > "Clone from Git"` and paste the URL for this repo: `https://github.com/AllenNeuralDynamics/dynamic-routing-capsule-template`
- the capsule should open at this readme
- if you haven't done this before, follow the instructions in [`credentials`](#credentials)

### for more-permanent, collaborative capsule development
*create a new repo*, which can serve as the remote for one or more capsules:
- just hit the big green button to "`Use this template`": a new repo will be created after you decide its name
- follow the cloning instructions above and supply the link to your new repo
- the capsule can now pull changes from github, so you can add code files directly to the github repo and pull them in codeocean
- to push changes *from* codeocean:
    - generate a personal access token for your account in github
    - add it to your account in codeocean 

## credentials

we need to ensure two sets of credentials are available in the capsule:
1. AWS (to find and read files on S3)
2. Codeocean (to find processed data in "data assets" via the Codeocean API)

- right click on `Account` (bottom left, person icon) and open in a new window, so we can switch back and forth between these instructions
- click `User Secrets` - these are secrets than can be made available as environment variables in Codeocean capsules
- check that there's a secret with the type `AWS Cloud Credentials`: this should have been automatically added to your account, **if it's not there get in touch with Ben**

- next go to `Access Tokens` and click `Generate new token`
- enter the Token Name `Codeocean API (read)` and tick `read` on capsules and datasets
- a token will be generated: click copy (storing it in a password manager, if you use one), then head back to `User Secrets` where we'll paste it into a new secret via `Add secret` > `API credentials`
- description: `Codeocean API (read)`, API key: `CODE_OCEAN_API_KEY`, API secret: paste the copied secret from before (should begin `cop_...`)

- now, refresh the browser page with the capsule so that we can use the newly-added secrets

- in the capsule's file browser (left), click on `environment` under `Core Files` (cog icon) to open the `Environment` tab

- scroll down to the bottom of the page - we'll use `Add secret to capsule` to make secrets available as environment variables within the capsule

- first choose `AWS Cloud Credentials` and select the available option in the dropdown that appears (says `Select AWS Cloud Credentials`)

- `Add secret to capsule` should be blue again, click it and this time choose `API credentials` and, in the dropdown, select `[API credentials] Codeocean API (read)`
