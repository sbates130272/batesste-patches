# batesste-patches

A simple repo that contains many of my patchsets for open-source
projects that us a mailing list for patch submission.

## Overview

This repo uses a [bash script called ```gen-patches```](./gen-patches)
to construct a call to ```git format-patch``` for a given
(open-source) project. It uses a branch name and a count to generate
the set of patches. The user should also provide a version. A
cover-letter is also generated.

## Example Uages
```
batesste-patches$ BRANCH=events PROJECT=blktrace ./gen-patches 
<snip>/batesste-patches/blktrace/events/v1/v1-0000-cover-letter.patch
<snip>/batesste-patches/blktrace/events/v1/v1-0001-blktrace-events-Add-an-option-to-stop-blktrace-up.patch
```
In this example we generate one patch and a cover letter based on the
[blktrace][ref-blktrace] project.

## Emailing Patches

Since I already have an Ansible role that [sets up
mutt][ref-ansible-mutt]  on my systems I can use mutt with something
like:
```
mutt -H - < <patch-name>.patch
```
[ref-blktrace]: https://git.kernel.dk/blktrace.git
[ref-ansible-mutt]:https://github.com/sbates130272/batesste-ansible/tree/main/roles/mutt_setup
