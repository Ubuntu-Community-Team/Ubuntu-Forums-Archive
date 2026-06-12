---
title: "Ubuntu 16.10 kernel update broke network"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by davibo on 2017-03-18
Hi,

It appears that the latest system update has broken wifi on my Dell laptop:

I've booted up with kernel 4.8.0-41 and everything is happy (I'm posting this from my laptop)

```
davibo@lamut: ~$ sudo modprobe iwlwifidavibo@lamut: ~$ dmesg | grep iwl
[    5.521050] iwlwifi 0000:02:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    5.935729] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    5.937780] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.938020] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    6.181014] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   11.226403] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   11.226642] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   11.421856] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   11.422094] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
davibo@lamut: ~$ uname -a
Linux lamut 4.8.0-41-generic #44-Ubuntu SMP Fri Mar 3 15:27:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

but on the latest&greatest:

```

davibo@lamut: ~$ sudo modprobe iwlwifi
modprobe: ERROR: ../libkmod/libkmod-module.c:832 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Unknown symbol in module, or unknown parameter (see dmesg)
davibo@lamut: ~$ uname -a
Linux lamut 4.8.0-42-generic #45-Ubuntu SMP Wed Mar 8 20:06:06 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Wired network is broken on 4.8.0-42 too.

Two questions:

(1) - Is there a fix / newer kernel on the horizon that'd fix this?

(2) - Is it possible for me to safely revert back to my old configuration that works (booting up from grub and selecting 4.8.0-41 all the time is a bit tedious)

Thanks

---

### Post by Doug S on 2017-03-18
It seems as though kernel 4.8.0-42 may have been retracted. It isn't available for me. See also [here]("http://askubuntu.com/questions/893632/ubuntu-16-04-kernel-packages-have-been-kept-back"). And there are multiple reports of issues from people that did get it.

EDIT: I have searched the kernel team IRC logs and e-mail list archives and launchpad, and didn't find any specific information about issues with 4.8.0-42.
EDIT: I would suggest to purge kernel 4.8.0-42.

---

### Post by davibo on 2017-03-19
Thanks, that's a useful tip. Stupid question - how do I safely purge the bad kernel? I suppose I have to be booted with one that works (that's OK). What I found with some googling is:

```

[COLOR=#111111][FONT=Consolas]sudo apt-get purge linux-image-x.x.x.x-generic
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo update-grub2 [/FONT][/COLOR]
```

Sorry I just want to double-check; I want a working computer after all this and never done it before :)

---

### Post by Doug S on 2017-03-19
> **davibo said:**
> I suppose I have to be booted with one that works (that's OK).Yes, you must not be booted with the kernel you are trying to remove.

> **davibo said:**
> 
```

[COLOR=#111111][FONT=Consolas]sudo apt-get purge linux-image-x.x.x.x-generic
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo update-grub2 [/FONT][/COLOR]
```You also need to remove the headers. Example (using apt, instead of apt-get, and for a different kernel version):
```
$ sudo apt purge linux-image-4.8.0-26-generic linux-headers-4.8.0-26
...
The following packages will be REMOVED:
  linux-headers-4.8.0-26* linux-headers-4.8.0-26-generic* linux-image-4.8.0-26-generic* linux-image-extra-4.8.0-26-generic*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 314 MB disk space will be freed.
Do you want to continue? [Y/n] Y

```There is also a very cool selective kernel purge script (both a desktop and a server version) recently posted on [askubuntu.com]("http://askubuntu.com/questions/892076/how-to-selectively-purge-old-kernels-all-at-once").

---

