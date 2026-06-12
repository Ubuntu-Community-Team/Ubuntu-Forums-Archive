---
title: "video breaks wireless?"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by jbeiter on 2007-01-09
okay this is frustrating.

After fighting with Ubuntu to figure out how to rip out the mis-matched remains of nvidia drivers that were conflicting with the updated install my video finally works...

... only to discover it broke wireless. eth1 no longer shows up in the system when it was working just fine prior to un-installing nvidia 17something. There is no mistaking the cause and effect here. Just as soon as I removed that old nvidia-kernel app, video worked, and wireless was hosed.

Any clues? I would *really not* like to re-install ubuntu from scratch again. If this were redhat, I'd be cursing kudzu... what is the hardware detection equivalent in ubuntu?

root@jwb-laptop:/opt/src# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

root@jwb-laptop:/opt/src# 
-----------------------------------------------------------------
dmesg|grep eth1:
root@jwb-laptop:/opt/src# dmesg|grep eth1
[17179598.376000] bridge-eth1: peer interface eth1 not found, will wait for it to come up
[17179598.380000] bridge-eth1: attached
-----------------------------------------------------------------

dmesg|grep 3945:
root@jwb-laptop:/opt/src# dmesg|grep 3945
[17179583.100000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179583.100000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179583.104000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
root@jwb-laptop:/opt/src# 
------------------------------------------------------------------
root@jwb-laptop:/opt/src# lspci|grep 3945
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
root@jwb-laptop:/opt/src# 
-------------------------------------------------------------------

root@jwb-laptop:/opt/src# ifconfig eth1
eth1: error fetching interface information: Device not found
root@jwb-laptop:/opt/src# 
--------------------------------------------------------------------


And I just got wpa_supplicant to connect to my company's wireless network yesterday! Grrrrr

any help would be appreciated. I tried to recompile/install ipw3945 but it's complaining about ieee80211's version or something. How do you kick Ubuntu into connecting the hardware again? Obviously it is there but its not showing up in the system.

system-administration->networking doesn't awknowledge eth1 either.. I don't see a way to add the interface either (would be a nice feature to have.)
](*,)

---

### Post by jbeiter on 2007-01-09
okay I know what is breaking it.. when I retraced my steps to get it working, this step:

-------------------------------------------------
sudo apt-get install linux-restricted-modules-generic
-------------------------------------------------

fixed wireless and broke my video again. Can anyone tell me how to remove the nvidia parts and keep the wireless parts? Is there a way to list what is in this pack of modules and remove them selectively? I think when I removed the nvidia-kernel package last night, it took out everything, including whatever is making my wireless to work.

messages:
x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
Jan  9 11:01:02 jwb-laptop kernel: [17179654.552000] NVRM: make sure that this kernel module and all NVIDIA driver
Jan  9 11:01:19 jwb-laptop kernel: [17179672.280000] NVRM: make sure that this kernel module and all NVIDIA driver
Jan  9 11:01:50 jwb-laptop kernel: [17179703.392000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006


I've tried installing the NVIDIA.run file but it doesn't seem to overwrite the nvidia-kernel package. Likewise, re-installing this module package (via apt-get or via automatix) doesn't overwrite my NVIDIA.run installation.... removing the linux-restricted-modules-generic fixes video and breaks wireless.

I get the feeling the fix is insanely easy but I just can't find it.

---

### Post by jbeiter on 2007-01-09
okay it was insanely easy but not trivial.

From another post:

-------------------------------------------------------------------------------------------------------
sudo nano /etc/default/linux-restricted-modules-common

#The last line of this file should read DISABLED_MODULES="", add nv to it to it reads DISABLED_MODULES="nv"

#This will make it so the xserver loads the nvidia module you compiled instead of the one that come with the restricted modules package.
--------------------------------------------------------------------------------------------------------

I updated Nvidia with the latest and greatest driver from the nvidia website. Adding that last line to the file indicated tells the system to use the new installed driver.

Video works, wireless works  - wheeee!

---

