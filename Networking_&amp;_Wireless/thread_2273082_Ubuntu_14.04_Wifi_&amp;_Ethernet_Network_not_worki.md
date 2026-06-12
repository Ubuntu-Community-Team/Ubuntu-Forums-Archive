---
title: "Ubuntu 14.04 Wifi &amp; Ethernet Network not working (II)  - Network Unclaimed"
date: 2015-04-10
forum: Networking &amp; Wireless
---

### Post by dancljohnson on 2015-04-10
Hi, 

I seem to be having a problem similar to the one in this thread: [Ubuntu 14.04 Wifi & Ethernet Network not working - Network Unclaimed]("http://ubuntuforums.org/showthread.php?t=2260232"), but since the thread was separated and re-merged, there are pieces missing and I don't know how the print out in the 'original' post was generated nor if the solution proposed will apply to me since I believe we have different wireless cards. 
 
Similar to the previous thread, both the wireless and ethernet have "*-network UNCLAIMED" and I am unable to access the internet by either means.  

```
daniel@Thomas:~$ sudo lshw -C network  
  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d01fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       version: 0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
```

Thanks.

---

### Post by chili555 on 2015-04-10
Both devices are driven by drivers included by default in all recent Ubuntu versions. If they didn't load, there is something else wrong. Please open a terminal and run:```
sudo modprobe r8169
sudo modprobe iwlwifi
```Any errors or complaints at the terminal? Any trouble here?```
dmesg | grep -e iwl -e r8169
```Thanks.

---

### Post by dancljohnson on 2015-04-10
Thanks for your help. It doesn't look like either were found. 

```
daniel@Thomas:~$ sudo modprobe r8169
modprobe: FATAL: Module r8169 not found.
daniel@Thomas:~$ sudo modprobe iwlwifi
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='iwlwifi'
modprobe: ERROR: could not insert 'iwlwifi': Function not implemented
daniel@Thomas:~$ dmesg | grep -e iwl -e r8169
daniel@Thomas:~$ 

```

---

### Post by chili555 on 2015-04-10
How about letting us see:```
lsb_release -a
uname -r
```That's a very weird problem you have there!

Thanks.

---

### Post by dancljohnson on 2015-04-11
```
daniel@Thomas:~$ lsb_release -aLSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
daniel@Thomas:~$ uname -r
3.13.0-49-generic
```

---

### Post by chili555 on 2015-04-11
> LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarchI must admit that I've never seen this in Ubuntu. SUSE and Red Hat, yes, but not here.

I could propose a number of solutions involving downloading, reinstalling kernels, etc., but, of course, you can do none of this. Do you have any older kernel versions on your system?```
ls /boot | grep init
```If you have a version earlier than 3.13.0-49-generic, then I suggest you reboot and interrupt the boot process with the shift key to get to the GRUB menu.

[ATTACH=CONFIG]261230[/ATTACH]

Select an earlier kernel version; that is, earlier than -49, and boot into it. Is your wireless working? If so, we'll work out reinstalling -49.

---

### Post by dancljohnson on 2015-04-11
Yes! I booted with version -48 and the wireless works just fine.

---

### Post by chili555 on 2015-04-12
Excellent! I fear that the copies of the deb files you have in cache may be corrupted. Let's remove them so that the system must download fresh copies. Please do:```
ls /var/cache/apt/archives | grep linux
```There will be a number of deb files with -49 in the name, here is an example from my machine:```
linux-generic_3.16.0.33.34_amd64.deb
linux-generic_3.16.0.34.35_amd64.deb
linux-headers-3.16.0-31_3.16.0-31.43_all.deb
linux-headers-3.16.0-31-generic_3.16.0-31.43_amd64.deb
linux-headers-3.16.0-33_3.16.0-33.44_all.deb
linux-headers-3.16.0-33-generic_3.16.0-33.44_amd64.deb
linux-headers-3.16.0-34_3.16.0-34.45_all.deb
linux-headers-3.16.0-34-generic_3.16.0-34.45_amd64.deb
linux-headers-generic_3.16.0.33.34_amd64.deb
linux-headers-generic_3.16.0.34.35_amd64.deb
linux-image-3.16.0-31-generic_3.16.0-31.43_amd64.deb
linux-image-3.16.0-33-generic_3.16.0-33.44_amd64.deb
linux-image-3.16.0-34-generic_3.16.0-34.45_amd64.deb
linux-image-extra-3.16.0-31-generic_3.16.0-31.43_amd64.deb
linux-image-extra-3.16.0-33-generic_3.16.0-33.44_amd64.deb
linux-image-extra-3.16.0-34-generic_3.16.0-34.45_amd64.deb
linux-image-generic_3.16.0.33.34_amd64.deb
linux-image-generic_3.16.0.34.35_amd64.deb
linux-libc-dev_3.16.0-31.43_amd64.deb
linux-libc-dev_3.16.0-33.44_amd64.deb
linux-libc-dev_3.16.0-34.45_amd64.deb

```Of course, since I run 14.10, the names are not the same but I hope you see the idea.

Remove the files with -49 in their names. You needn't include the version details; we'll use a wildcard for that. You also probably needn't do anything with libc.```
cd /var/cache/apt/archives
sudo rm linux-image-generic-3.13.0-49*
sudo rm linux-image-extra-3.13.0-49*
sudo rm linux-image-3.13.0-49*
sudo rm linux-headers-generic-3.13.0-49*
sudo rm linux-headers-3.13.0-49*

```Now reinstall them:```
sudo apt-get install --reinstall linux-image-generic-3.13.0-49
sudo apt-get install --reinstall linux-image-extra-3.13.0-49
sudo apt-get install --reinstall linux-image-3.13.0-49
sudo apt-get install --reinstall linux-headers-generic-3.13.0-49
sudo apt-get install --reinstall linux-headers-3.13.0-49
```Now reboot into -49 and let us hear your report.

---

### Post by dancljohnson on 2015-04-12
Ok great. I did as instructed above, though the when trying to reinstall the 'linux-headers-generic', the choices were 

```
[FONT=arial]daniel@Thomas:/var/cache/apt/[/FONT][FONT=arial]archives$ sudo apt-get install --reinstall linux-headers-g
[/FONT][FONT=arial]linux-headers-generic              linux-headers-generic-lts-saucy    linux-headers-generic-pae[/FONT]
[FONT=arial]linux-headers-generic-lts-quantal  linux-headers-generic-lts-trusty   linux-headers-goldfish[/FONT]
[FONT=arial]linux-headers-generic-lts-[/FONT][FONT=arial]raring   linux-headers-generic-lts-[/FONT][FONT=arial]utopic [/FONT]
```

and similarly for 'linux-image-generic'. I did not install any of those, but did install the other items in the list. As of now, I am showing:

```
[FONT=arial]daniel@Thomas:/var/cache/apt/[/FONT][FONT=arial]archives$ ls | grep linux
[/FONT][FONT=arial]linux-headers-3.13.0-48_3.13.0-48.80_all.deb[/FONT]
[FONT=arial]linux-headers-3.13.0-48-generic_3.13.0-48.80_amd64.deb[/FONT]
[FONT=arial]linux-headers-3.13.0-49_3.13.0-49.81_all.deb[/FONT]
[FONT=arial]linux-headers-3.13.0-49-generic_3.13.0-49.81_amd64.deb[/FONT]
[FONT=arial]linux-headers-generic_3.13.0.48.55_amd64.deb[/FONT]
[FONT=arial]linux-image-3.13.0-48-generic_3.13.0-48.80_amd64.deb[/FONT]
[FONT=arial]linux-image-3.13.0-49-generic_3.13.0-49.81_amd64.deb[/FONT]
[FONT=arial]linux-image-extra-3.13.0-48-generic_3.13.0-48.80_amd64.deb[/FONT]
[FONT=arial]linux-image-extra-3.13.0-49-generic_3.13.0-49.81_amd64.deb[/FONT]
[FONT=arial]linux-image-generic_3.13.0.48.55_amd64.deb[/FONT]
[FONT=arial]linux-libc-dev_3.13.0-48.80_amd64.deb[/FONT]
[FONT=arial]linux-libc-dev_3.13.0-49.81_[/FONT][FONT=arial]amd64.deb[/FONT]
```

After rebooting into -49 the wireless works, though I am clearly a novice and do not understand if the 'linux-headers-generic/linux-image-generic' files that were not reinstalled are still necessary. Thank you Chili for all of your help!

---

### Post by chili555 on 2015-04-12
The headers are really only needed if you intend to compile from source code. Usually, that is well beyond the skill and need of a novice. I wouldn't be concerned. Please use thread tools at the top to mark Solved.

---

### Post by dancljohnson on 2015-04-12
Great, thank you very much!

---

