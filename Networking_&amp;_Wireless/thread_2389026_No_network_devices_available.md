---
title: "No network devices available"
date: 2018-04-10
forum: Networking &amp; Wireless
---

### Post by turb03 on 2018-04-10
Hello everyone,

Recently I had some resolution problems, and I managed to fix them by  updating my Kernel version to the newest one (4.16). That fixed my  resolution but now I am not able to connect to the wifi, whereas before  that I was able to. After running **'lspci -nn -d 14e4:' **I get **'08:00.0 Network controller [0280]: Broadcom Limited BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)' **.  When I searched for drivers for this network card, I did not find any  that were for mine, especially for the (rev 01). I tried installing  bcmwl-kernel-source through the terminal and manually by downloading and  installing the package, but it didn't fix my error. Also the output of **'iwconfig' **is **'lo     no wireless extentions'**. 
If anyone has any idea on the solution please share it with me so I can try to fix that. Thank you very much in advance :smile:

- turb0

---

### Post by chili555 on 2018-04-10
> When I searched for drivers for this network card, I did not find any that were for mine, Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

> I tried installing bcmwl-kernel-source through the terminal and manually by downloading and installing the package, but it didn't fix my error.What exactly happened? I expect that with no networking devices at all, apt was unable to go out to the internet, find and install the package, right?

Do you still have the install DVD or USB? [https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619](https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619)

What is the exact response to the terminal command:```
sudo modprobe wl
```

---

### Post by turb03 on 2018-04-10
Hello, and thanks for the fast response :)
I already saw that list but there is no driver for **14e4:432b (rev 1)**, only for the 14e4:432b. I still tried installing it, and I think everything went well. I restarted my computer but there wasn't a difference.

I tried deleting the drivers with **'sudo apt-get purge bcmwl-kernel-source'**, and that was the output: 

[I]vladi@Hyperion:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for vladi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms fakeroot gcc gcc-7 libasan4 libatomic1 libc-dev-bin libc6-dev libcc1-0
  libcilkrts5 libfakeroot libgcc-7-dev libitm1 libmpx2 libubsan0
  linux-libc-dev manpages-dev
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] [/I]

After typing Y, the terminal outputs:

[I]Do you want to continue? [Y/n] y
(Reading database ... 169649 files and directories currently installed.)
Purging configuration files for bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.125ubuntu12.1) ...
update-initramfs: Generating /boot/initrd.img-4.16.0-041600-lowlatency
W: Possible missing firmware /lib/firmware/i915/skl_dmc_ver1_27.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_04.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_39.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver9_29.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver9_33.bin for module i915
[/I]
Also I use a usb flash card to connect to the wifi, so it doesn't have problems with it. I just connect it and the computer automatically finds all wifi networks. Here is the exact response for [B]'sudo modprobe wl'

[/B][I]modprobe: FATAL: Module wl not found in directory /lib/modules/4.16.0-041600-lowlatency

[/I]Thank you again for helping me out with this problem :)
- turb0

---

### Post by chili555 on 2018-04-10
We'd really rather see the result of:```
sudo apt-get install bcmwl-kernel-source
```We suspect that your kernel version isn't supported, but run the command anyway so we can confirm. Old Chili loves a good, big train wreck.

> 4.16.0-041600-lowlatencyIf you must, must have 4.16, I suspect that you can't have Broadcom wireless.

---

### Post by turb03 on 2018-04-10
Hello again Chili

Here is the output of [B]'sudo apt-get install bcmwl-kernel-source'

[/B][I]vladi@Hyperion:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for vladi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,520 kB of archives.
After this operation, 7,176 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 169650 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu3_i386.deb ...
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu3) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu3) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 4.16.0-041600-lowlatency
Building for architecture i686
Building initial module for 4.16.0-041600-lowlatency
ERROR (dkms apport): kernel package linux-headers-4.16.0-041600-lowlatency is not supported
Error! Bad return status for module build on kernel: 4.16.0-041600-lowlatency (i686)
Consult /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.16.0-041600-lowlatency
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.125ubuntu12.1) ...
update-initramfs: Generating /boot/initrd.img-4.16.0-041600-lowlatency
W: Possible missing firmware /lib/firmware/i915/skl_dmc_ver1_27.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_04.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_39.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver9_29.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver9_33.bin for module i915
vladi@Hyperion:~$ [/I]

Now that I read it more carefully it really looks like it may be a kernel problem, as I didn't have it with the old Kernel version (4.13). But I really need the new one, as I had resolution problems with the old one (couldn't recognize the real resolution of my machine). Do you think that going to Kernel 4.15 may fix my issue? Or should I install Lubuntu 16 or maybe 18?

Thank you for the help and the fast responses ;)
- turb0

---

### Post by chili555 on 2018-04-11
> ERROR (dkms apport): kernel package linux-headers-4.16.0-041600-lowlatency is not supported"As we suspected..." (Voice of Darth Sidious)

My first suggestion is to try a live session of Ubuntu 18.04 daily build. It uses kernel version 4.15 and has bcmwl-kernel-source on the DVD or USB. If it works for you in "Try Ubuntu" mode, install it. If not, post back and we'll try something else.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by turb03 on 2018-04-11
Alright Chili, thanks for the help!
Can I just ask you if you can send me a link to the 32bit version of it, because my machine is pretty old and is 32bit :(
Thank you again and hope you have a good day!

---

### Post by chili555 on 2018-04-12
Sorry. [https://www.omgubuntu.co.uk/2017/09/ubuntu-17-10-32-bit-builds-dropped](https://www.omgubuntu.co.uk/2017/09/ubuntu-17-10-32-bit-builds-dropped)

---

