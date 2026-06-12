---
title: "Ubuntu 12.04LTS Wireless works but at boot waiting for network config...waiting 60 s"
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by Old_Brewer on 2014-02-06
Hi All  Wireless & wired now works, however at boot I get a message after the Ubuntu splash that says, Waiting for network configuration, then after about 30 to 60 seconds a new message appears, Waiting up to 60 more seconds.  Once I log in the Network Manager sometimes shows the network, most of the time it does not show the network.  I'm using the wireless network, and it does work.  I upgraded from 10.04LTS & was using Wicd.  I searched and found that these 2 links seemed to have usable info:  [http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html](http://www.techdrivein.com/2012/09/slow-erratic-wifi-ubuntu1204-fixed.html)  and  [https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)  I disabled Network Manager & tried Wicd.  I still have the same messages at boot.  The messages slow the boot time & I would like to fix this issue.  I will appreciate a fix if someone has one.
Thanks

---

### Post by chili555 on 2014-02-06
When you boot and it's not working, please run:```
lsmod | grep b43
dmesg | grep -e b43 -e ssb
```Thanks.

---

### Post by Old_Brewer on 2014-02-06
Thanks for the help.
The network seems to always work.  I'd like to fix the slow boot caused by the messages.  Also, the Network manager should be disabled if these commands worked:  
sudo stop network-managerCreate an override file for the upstart job: 

echo "manual" | sudo tee /etc/init/network-manager.override

Here is the output from the commands that you asked about, however the network is working:

joebelle@joebelle-laptop:~$ lsmod |grep b43
b43                   342801  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  2 b44,b43
joebelle@joebelle-laptop:~$ 
joebelle@joebelle-laptop:~$ dmesg |grep -e b43 -e ssb
[   40.324568] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   40.344117] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[   40.344131] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[   40.344141] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[   40.344150] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[   40.384154] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[   40.598768] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   40.829705] Registered led device: b43-phy0::tx
[   40.829740] Registered led device: b43-phy0::rx
[   40.829774] Registered led device: b43-phy0::radio
[   41.048108] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   41.048120] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   41.048129] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   41.088289] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   41.194955] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:14:22:97:9b:e3
[  164.764126] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[  172.804054] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[  173.453078] b44 ssb1:0: eth0: powering down PHY
[  174.008081] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
joebelle@joebelle-laptop:~$ 
Thanks for your reply & help

---

### Post by chili555 on 2014-02-06
It seems likely, doesn't it, that Wicd and NM are conflicting. Generally, NM works perfectly well. Wicd is often installed in desperation while the trouble lies elsewhere. I suggest you settle on one and remove the other. > echo "manual" | sudo tee /etc/init/network-manager.overrideDid you do this? Is NM running now?```
ps aux | grep -i network
```

Is Wicd set to connect automatically to your network?

---

### Post by Old_Brewer on 2014-02-06
Hi
Here is the output of the commands.  Also the Wireless is set to automatically connect to the network
I can uninstall wicd & enable Networkmanager.  Should I? (or did the folowing command do just that?)

joebelle@joebelle-laptop:~$  echo "manual" | sudo tee /etc/init/network-manager.override 
[sudo] password for joebelle: 
manual
joebelle@joebelle-laptop:~$ ps aux | grep -i network
joebelle 19465  0.0  0.0   4388   816 pts/1    S+   20:15   0:00 grep -i network
joebelle@joebelle-laptop:~$ wicd-gtk
Has notifications support True
Loading...
Connecting to daemon...
Connected.
displaytray True
Done loading.
refreshing...
ESSID : Nathan

---

### Post by chili555 on 2014-02-06
So Network Manager wasn't running. However, you had to start Wicd from the terminal:> joebelle@joebelle-laptop:~$ wicd-gtk
Has notifications support True
Loading...
Connecting to daemon...
Connected.
displaytray True
Done loading.
refreshing...
ESSID : Nathan It appears to me that on a fresh boot, *neither* is running! Therefor, you don't get a network connection. > Also the Wireless is set to automatically connect to the networkWhere? In NM that you have disabled? Or in Wicd?

Is this a stay-at-home computer that just connects to one access point, evidently 'Nathan?'

---

### Post by Old_Brewer on 2014-02-06
Yes, you are correct.  Network manager was not running, and I did start Wicd from a terminal.
I agree that neither is running.  I'll remove Wicd, as soon as I figure how to do it in 12.04!  I did have the automatic connect in Wicd.
The computer is a Dell Inspiron B130 laptop that usually stays at home, but I occasionally go remote with it.  Nathan is the Wireless router that is at home & is part of a wireless bridge & I also have a Wireless access point.

---

### Post by chili555 on 2014-02-06
>  I'll remove Wicd, as soon as I figure how to do it in 12.04! Simply do:```
sudo apt-get remove --purge wicd*
```Then reverse the echo:```
gksudo gedit /etc/init/network-manager.override 
```Remove the word manual. If it is the only thing there, simply remove the file altogether:```
sudo rm /etc/init/network-manager.override
```Now check a few other things:> gksudo gedit /etc/network/interfacesMake sure there are no wlan or eth entries; if so, remove them. Save and close gedit. Reboot. Now NM should be in control. Be sure to set it to connect automatically.

---

### Post by Old_Brewer on 2014-02-06
OK  Done except for the reboot.  I tried to remove Wicd with the GUI & it failled.  Here is the output from removing it with the terminal, several errors, but I think it is gone.
Also, from /etc/network/interfaces I removed:
auto eth0
iface eth0 inet dhcp
Did the above remoce my wired interface?
Here is all of the output:
joebelle@joebelle-laptop:~$ sudo apt-get remove --purge wicd*
[sudo] password for joebelle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'wicd-curses' for regex 'wicd*'
Note, selecting 'python-dulwich' for regex 'wicd*'
Note, selecting 'python2.7-dulwich' for regex 'wicd*'
Note, selecting 'wicd' for regex 'wicd*'
Note, selecting 'python2.7-dulwich-dbg' for regex 'wicd*'
Note, selecting 'python-wicd' for regex 'wicd*'
Note, selecting 'wicd-client' for regex 'wicd*'
Note, selecting 'wicd-cli' for regex 'wicd*'
Note, selecting 'wicd-daemon' for regex 'wicd*'
Note, selecting 'greenwich' for regex 'wicd*'
Note, selecting 'python-dulwich-dbg' for regex 'wicd*'
Note, selecting 'wicd-gtk' for regex 'wicd*'
Note, selecting 'r-cran-sandwich' for regex 'wicd*'
Note, selecting 'wicd-kde' for regex 'wicd*'
Note, selecting 'python-dulwich' instead of 'python2.7-dulwich'
Note, selecting 'python-dulwich-dbg' instead of 'python2.7-dulwich-dbg'
Package greenwich is not installed, so not removed
Package python-dulwich is not installed, so not removed
Package python-dulwich-dbg is not installed, so not removed
Package r-cran-sandwich is not installed, so not removed
Package wicd-kde is not installed, so not removed
Package wicd is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libguess1 audacious libbinio1ldbl libaudclient2 libresid-builder0c2a
  libtagc0 audacious-plugins-data libbs2b0 libcddb2 audacious-plugins kdesudo
  libcue1 python-urwid dkms libmowgli2 libfluidsynth1 libaudcore1 libsidplay2
  libdb4.8 update-manager-kde libgnome-desktop-2-17 acroread-common libpisync1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  python-wicd* wicd-cli* wicd-curses* wicd-daemon* wicd-gtk*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 2,438 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
(Reading database ... 235673 files and directories currently installed.)
Removing wicd-curses ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Purging configuration files for wicd-curses ...
Removing wicd-cli ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Purging configuration files for wicd-cli ...
Removing wicd-daemon ...
 * Stopping Network connection manager wicd                              [ OK ] 
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Purging configuration files for wicd-daemon ...
Removing python-wicd ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Removing wicd-gtk ...
Purging configuration files for wicd-gtk ...
find: `/usr/share/wicd/': No such file or directory
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42638 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 42639 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42546 package 'avg75fld':
 error in Version string '7.5.51_a1243': invalid character in version number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 42547 package 'avg75fld':
 error in Config-Version string '7.5.51_a1243': invalid character in version number
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
joebelle@joebelle-laptop:~$ 
joebelle@joebelle-laptop:~$ gksudo gedit /etc/init/network-manager.override
joebelle@joebelle-laptop:~$ 
joebelle@joebelle-laptop:~$ sudo rm /etc/init/network-manager.override
joebelle@joebelle-laptop:~$ 
joebelle@joebelle-laptop:~$ gksudo gedit /etc/network/interfaces 
joebelle@joebelle-laptop:~$

---

### Post by chili555 on 2014-02-06
> Did the above remoce my wired interface?No. It just turned over control to NM.

It looks like you have a samba problem. I'd ask over here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

How did the reboot go?

---

### Post by Old_Brewer on 2014-02-06
Many thanks, again!  All is well, except for the Samba issue.  I figured I'd wait until I got the network working.  Wireless & wired is working.
Many kudos
I'll mark the thread closed.
Old_Brewer :)

---

### Post by chili555 on 2014-02-06
Awesome! Glad it's working.

---

