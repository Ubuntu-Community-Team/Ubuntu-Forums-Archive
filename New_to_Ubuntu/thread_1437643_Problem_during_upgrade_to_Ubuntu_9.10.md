---
title: "Problem during upgrade to Ubuntu 9.10"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by alciono on 2010-03-24
I tried to upgrade to Ubuntu 9.10. During the restart, the computer hangs. I tried the recovery mode, and this is what I see:

render error detected, EIR: 0x00000010
[drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
render error detected, EIR: 0x00000010
[drm] DAC-5: set mode 1440x900 17
Console: switching to colour frame buffer device 180x56
Begin: Loading essential drivers ... ...
xor: automatically using best checksumming function: pIII_sse
    pIII_sse  :  3044.000 MB/sec
xor: using function: pIII_sse (3044.000 MB/sec)
device-mapper: dm-raid45: initialized v0.2594b
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root filesystem... ...
Done.
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules: ls /dev)
Alert! /dev/disk/by-uuid/766befc5-d053-4e8f-8e44-6253346c74f4 does not exist. Dropping to a shell!

Then I get a shell prompt
(initramfs)

Any help in how I should proceed in starting the boot process would be helpful.

---

### Post by alciono on 2010-03-24
A listing of the /dev/disk/by-uuid gives
78fca3cf-1fec-489f-b894-1cdfcd294fee

When I check the environment variables:
resume=UUID=78fca3cf-1fec-489f-b894-1cdfcd294fee
...
ROOT=/dev/disk/by-uuid/766befc5-d053-4e8f-8e44-6253346c74f4

I tried to reboot, and got message:
Waiting for root file system...
and crashed.

---

### Post by alciono on 2010-03-24
I tried to boot in another recovery mode:

Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t(/dev/disk/by-uuid/78fca3cf-1fec-489f-b894-1cdfcd294fee) = ...
kinit: trying to resume from /dev/disk/by-uuid/78fca3cf-1fec-489f-b894-1cdfcd294fee
[17179575.408000] Attempting manual resume
kinit: No resume image, doing normal boot...
Done.
[17179575.432000] kjournald starting. Commit interval 5 seconds.
[17179575.432000] EXT3-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
init: ureadahead main process (2371) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2374) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root:~#

Any ideas how to proceed from here?

---

### Post by Don1500 on 2010-03-24
How have you set up your partitions?

A suggested setup is
1 partition for /
1 partition for /home
1 swap = 2X your RAM

Load from the live CD and go to  SYSTEM => ADMINISTRATION => GPARTED
Set up your partitions and then try to reinstall Karmic.

Next step is to download the Karmic ISO again and make a new disk.

---

### Post by alciono on 2010-03-24
I was running Jaunty and attempted an upgrade. It crashed during the restart process. The partitions should be as before, I am not using multiple boots. I do not have a live CD, but I guess I will need one now.

---

