---
title: "Ubuntu 15.04 + BCM4322 + Included bcmwl-kernel-source  = Broken Wifi"
date: 2015-06-16
forum: Networking &amp; Wireless
---

### Post by josh139 on 2015-06-16
Just installed Ubuntu 15.04 on my Macbook Pro mid-2010 along side OS X Yosemite.  As the title says, I can't seem to get wifi going.   Network controller is as follows:   ```
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
``` In Ubuntu's "Additional Drivers" Application under the "Additional Drivers" tab, it lists the Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary), but enabling it makes no difference.  Can anyone help?

---

### Post by chili555 on 2015-06-16
Please help us help you: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by josh139 on 2015-06-16
Okay, I ran the script and attached the resulting .txt.

Thanks for your help so far!

---

### Post by chili555 on 2015-06-16
There are some very mysterious things in the report. Please run:```
sudo modprobe -r wl  &&  sudo modprobe wl
dmesg | grep 02:00
```Please post the result.

---

### Post by josh139 on 2015-06-16
Here is the result:

```
josh@Hal:~$ sudo modprobe -r wl && sudo modprobe wl
[sudo] password for josh: 
josh@Hal:~$ dmesg | grep 02:00
[    0.168261] pci 0000:02:00.0: [14e4:432b] type 00 class 0x028000
[    0.168284] pci 0000:02:00.0: reg 0x10: [mem 0xd3200000-0xd3203fff 64bit]
[    0.168402] pci 0000:02:00.0: supports D1 D2
[    0.168404] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.168439] pci 0000:02:00.0: System wakeup disabled by ACPI
[    2.495909] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
josh@Hal:~$ 

```

The "sudo modprobe -r wl && sudo modprobe wl" didn't appear to do anything.

---

### Post by chili555 on 2015-06-17
> [    2.495909] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0We wonder why the module ssb loads and probably interferes when it is blacklisted...twice!

The fact that it is blacklisted in two different files makes me wonder if there is a conflict going. Please check:```
sudo dpkg -s bcmwl-kernel-source | grep Status
sudo dpkg -s broadcom-sta-dkms | grep Status
```Is one installed or both? Which?

In the meantime, please try:```
sudo modprobe -r wl
sudo modprobe -r ssb
sudo modprobe wl
iwconfig
```Does wlan0 now appear?> The "sudo modprobe -r wl && sudo modprobe wl" didn't appear to do anything.That's a good thing! No errors, warnings or other disturbing output!

---

### Post by josh139 on 2015-06-17
Done:

```
josh@Hal:~$ sudo dpkg -s bcmwl-kernel-source | grep Status
[sudo] password for josh: 
Status: install ok installed
josh@Hal:~$ sudo dpkg -s broadcom-sta-dkms | grep Status
Status: install ok installed
```

```
josh@Hal:~$ sudo modprobe -r wl
josh@Hal:~$ sudo modprobe -r ssb
josh@Hal:~$ sudo modprobe wl
josh@Hal:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Edited"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: Edited   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

josh@Hal:~
```

---

### Post by chili555 on 2015-06-17
Let's see if there is a conflict we can fix. Please do:```
sudo apt-get purge broadcom-sta-dkms
```Reboot and see what is now loaded:```
lsmod | grep -e wl -e ssb
```And see if you have a wireless interface:```
iwconfig
```If so, can you click the Network Manager icon, see networks and connect?

---

### Post by josh139 on 2015-06-17
Purged broadcom-sta-dkms successfully.

The other commands yielded the following:

```
josh@Hal:~$ lsmod | grep -e wl -e ssb
wl                   6369280  0 
cfg80211              540672  1 wl
ssb                    65536  0 
josh@Hal:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


```

Needless to say, no Networks found via Network Manager.

---

### Post by chili555 on 2015-06-17
Please do:```
gksudo gedit /etc/modules
```Use nano or kate or leafpad if you don't have the text editor gedit. If you find ssb or b43 listed there, remove it or them. Proofread carefully, save and close the text editor. Next, do:```
gksudo gedit /etc/rc.local
```Above the last line, exit 0, please add a single line:```
modprobe -rf ssb
```Proofread carefully, save and close the text editor. Reboot and let us see again:```
lsmod | grep -e wl -e ssb
```
And see if you have a wireless interface:

```
iwconfig
```
If so, can you click the Network Manager icon, see networks and connect?

---

### Post by josh139 on 2015-06-17
First I had to install the program "gksudo" as it wasn't yet installed.

```
josh@Hal:~$ gksudo gedit /etc/modules
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
josh@Hal:~$ sudo apt-get install gksu
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  iucode-tool
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 124 kB of archives.
After this operation, 1,041 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu7 [72.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid/universe gksu amd64 2.0.2-9ubuntu1 [51.5 kB]
Fetched 124 kB in 0s (176 kB/s) 
Selecting previously unselected package libgksu2-0.
(Reading database ... 203596 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu7_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-9ubuntu1_amd64.deb ...
Unpacking gksu (2.0.2-9ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.1+15.04.20150202-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.58ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu7) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
josh@Hal:~$
```

Then, when I opened /etc/modules via the included geddit, it's completely blank aside from comments:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
```

I think I might try to reinstall this 15.04 since I was utilizing two different guides when I did it and may have made an unknown error in setting things up.  For instance, on my rEFInd screen after restart there is 3 ubuntu logos to boot into from, two of which do not produce a solid boot.  The other, kernel .13 or something, works.  I think from here I'll start fresh.  Maybe even scale back to 14.04.2 to see how smooth things go.

---

