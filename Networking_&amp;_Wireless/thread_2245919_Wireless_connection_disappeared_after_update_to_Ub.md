---
title: "Wireless connection disappeared after update to Ubuntu 12.04"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by mikeavison on 2014-09-27
HI 

I have been using Ubuntu 12.04 happily for some time but I did need help getting the wireless to work in the first place.

Now because of shellshock I let ubuntu update and - oh no - the wireless has stopped again.

Following the original instructions again did not work, the instructions were:-

sudo apt-get purge bcmwl-kernel-source
sudo apt-get update
sudo apt-get install linux-firmware-nonfree

The wireless adapter is Broadcom BCM4311

Running lspci -nn -d 14e4: yields:-

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

Any help gratefully received

---

### Post by Hadaka on 2014-09-27
Hi, please do...

*These may error out or say,,no such file..but please do them anyway
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by mikeavison on 2014-09-27
Hi Hadaka

Thanks for trying to help. I am afraid it did not work. Have you any other ideas I could try? By the way, it is probably not relevant but I am using Gnome classic Fallback desktop.

Here are the results of running the commands you suggested:-

sudo apt-get remove --purge bcmwl-kernel-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libxrandr-ltss2 libwayland-ltss-client0 dkms libwayland-ltss-server0 libllvm3.3
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

sudo rm /etc/modprobe.d/blacklist-bcm43.conf

rm: cannot remove `/etc/modprobe.d/blacklist-bcm43.conf': No such file or directory

sudo apt-get install b43-fwcutter firmware-b43-installer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
b43-fwcutter set to manually installed.
firmware-b43-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  libxrandr-ltss2 libwayland-ltss-client0 dkms libwayland-ltss-server0 libllvm3.3
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

sudo modprobe b43

No report

---

### Post by Hadaka on 2014-09-27
Hi, lets give this a try..from a wired connection
please do..
```
sudo apt-get autoremove
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
thanks

---

### Post by mikeavison on 2014-09-27
Hi Hadaka 

I'm afraid that didn't fix it. Here are the results:-

sudo apt-get autoremove
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  dkms libllvm3.3 libwayland-ltss-client0 libwayland-ltss-server0
  libxrandr-ltss2
0 to upgrade, 0 to newly install, 5 to remove and 0 not to upgrade.
After this operation, 25.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 256048 files and directories currently installed.)
Removing dkms ...
Removing libllvm3.3 ...
Removing libwayland-ltss-client0 ...
Removing libwayland-ltss-server0 ...
Removing libxrandr-ltss2 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

sudo apt-get remove --purge linux-firmware-nonfree

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-firmware-nonfree*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 8,249 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 256002 files and directories currently installed.)
Removing linux-firmware-nonfree ...

sudo apt-get install b43-fwcutter firmware-b43-installer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

sudo modprobe -rf b43

sudo modprobe b43


Thanks for trying though

---

### Post by westie457 on 2014-09-27
Hi, unplug the cable if still connected and check the Network Manager icon for networks. If none showing reboot and recheck.

---

### Post by mikeavison on 2014-09-27
HI Westie
When I did that there were no network connections till I plugged the cable back in

---

### Post by westie457 on 2014-09-27
Heigh-ho something has broken slightly. Give this command a run ```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
``` followed by the last two commands posted by Hadaka.
Again unplug the cable as in my previous post.
Hpoefully it will now be working.

---

### Post by mikeavison on 2014-09-28
BRILLIANT that worked.

If you have the time can you explain
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer


Do you think I will have this problem again if I download updates to Ubuntu 12.04 ?

---

### Post by Hadaka on 2014-09-28
Hi, glad that worked for you, I think the first time you ran
the commands you didnt have the wired connection connected
and it needs to be. You should not have to re run these commands
after the next os update. Please take the time to mark this thread solved.
thanks.


@westie.thanks

---

### Post by westie457 on 2014-09-28
Great news that it is working. Thanks should also go to Hadaka because s/he did most of the work here.
> [COLOR=#000000]If you have the time can you explain[/COLOR]
[COLOR=#000000]sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer[/COLOR]

In simple terms the newer versions if linux-firmware-nonfree break the b43 driver and remove parts of the config/library files.
Even though apt-get was saying they were already at the newest version the important parts for your system were missing. The '--reinstall' option forces apt-get to rewrite those missing parts allowing your hardware to work.

> [COLOR=#000000]Do you think I will have this problem again if I download updates to Ubuntu 12.04 ?[/COLOR]

Possibly, things might break later. Probably not,so keep this thread handy for future use.

My older laptop has the same wireless chip in it. I have two versions of 12.04 on different hard drives, only one is fitted, the other is a spare if the fitted one dies.
The smaller capacity one is locked to the 3.2 series of kernel - mainly because it had not been in use when the point releases with HWE-stacks (hardware enablement). That one only uses the 'B43-firmware' driver. The larger capacity one has the newer point release. This one started with 'B43' transitioned through 'linux-firmware-nonfree' and back to 'B43-firmware.

Hope I have made this understandable.

ps Could you mark this as 'SOLVED' using 'Thread Tools' at the top of the page.

---

### Post by mikeavison on 2014-09-28
Thanks for all your help - really appreciated.

You may be right about the network cable I did find it lose at some stage.

---

