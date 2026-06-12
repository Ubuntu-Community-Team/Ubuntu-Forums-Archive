---
title: "Urgently need help with network &amp; Internet"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by iClouseau88 on 2009-05-09
Hello all,

Recently upgraded from Intrepid to Jaunty.  Has wired but lost wireless connection.  Followed the instruction from AnthraxMouthwash.  Downloaded wicd deb package and hit enter.  Completely removed Network Manager and network-manager-gnome.  Now I cannot get to the Internet, cannot update or do anything with Synaptic or Software Sources because I get error message like "cannot resolve archive.ubuntu.com" or "cannot locate google".

Please help me find the wicd package (wicd_1.5.9.2...all.deb) because I went to nearly all the folders but cannot locate it.  Where do I find any package that Gdebi just installed?

I appreciate your help.

:confused:

---

### Post by 73ckn797 on 2009-05-09
> **iClouseau88 said:**
> Hello all,

Recently upgraded from Intrepid to Jaunty.  Has wired but lost wireless connection.  Followed the instruction from AnthraxMouthwash.  Downloaded wicd deb package and hit enter.  Completely removed Network Manager and network-manager-gnome.  Now I cannot get to the Internet, cannot update or do anything with Synaptic or Software Sources because I get error message like "cannot resolve archive.ubuntu.com" or "cannot locate google".

Please help me find the wicd package (wicd_1.5.9.2...all.deb) because I went to nearly all the folders but cannot locate it.  Where do I find any package that Gdebi just installed?

I appreciate your help.

:confused:

Are you saying you first installed WICD then deleted Network Manager?

---

### Post by iClouseau88 on 2009-05-09
I am not sure exactly what happened.  When I downloaded the deb package some gdebi autoinstall menu item appears so I hit Enter.  Then I got a message saying to the effect Network manager is being intefered with, so I used Synaptic to completely remove both network manager and network-manager-gnome.  Now how can I do s system restore like in Windows and how do I find wicd_1.5.9-2_all.deb in my machine?

---

### Post by cariboo on 2009-05-09
Wicd will show up in synaptic if you do a search for it. Once you have uninstalled wicd you will need to reinstall network-manager-gnome and network-manager, if you have done a recent install and haven't used computer janitor or run apt-get clean and apt-get autoremove, the packages should still be in /var/cache/apt/archives.

---

### Post by richaoj on 2009-05-09
or just look in applications -> internet -> wicd

if you installed wicd it should be there

---

### Post by iClouseau88 on 2009-05-10
Hello my BC friend,

Update #1:

I am getting somewhere: Downloaded and saved the pkg to USB key then copied it to Home folder in Ubuntu machine. Installed wicd. Found it very difficult to set up. I cannot see a window to enter my passphrase unless I tick on "autoconnect..". Even when I finally get the screen to show connected (to wired network...IP 192.168.x.y" I still get page load error. This is way more difficult than it should be. I may have to consider re-installing network manager and wait for Canonical to fix NM.

Update #2:

I finally get wired connection to the net.  I still find wicd more clunky to set up than network manager.  May consider going back to NM.

---

### Post by superprash2003 on 2009-05-10
post output of **lshw -C network** from your terminal

---

### Post by iClouseau88 on 2009-05-10
Here's the output:

~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:8d:b4:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.10.102 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:e9:d9:d1:f0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:26:70:1c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 6.14 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:cb:85:69:fe:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by iClouseau88 on 2009-05-10
Still no wireless connection whether in NM or wicd (wired connection is OK).  

1) Should I stay with the current ath5k driver or should I try madwifi-0.9.4 driver?  Ath5k driver used to works in Intrepid, i.e. providing both wired and wireless connections up until upgrading to Jaunty.

2) How do I install madwifi-0.9.4 driver after downloading it?

Any suggestions would be much appreciated.

---

### Post by iClouseau88 on 2009-05-10
bump

---

### Post by Sef on 2009-05-10
> bump

Please don't bump unless 24 hours have gone by with no response.  It is frustrating to have to wait for help.

---

### Post by iClouseau88 on 2009-05-10
Sorry I didn't know the rule.

---

### Post by superprash2003 on 2009-05-11
you seem to have drivers.. try this [http://ubuntuforums.org/showthread.php?t=1028541](http://ubuntuforums.org/showthread.php?t=1028541)

---

### Post by iClouseau88 on 2009-05-11
Hi everyone,

Problem solved.  I check the router and found that type of encryption was TKIP+EAP, and radio broadcast was disabled.  I changed encryption to TKIP+PSK for WPA and ennabled radio broadcast so that wireless clients can pick up the signal.  Then I installed Network Manager through Synaptic which automatically shows option to remove Wicd.  After reboot, I have both autoconnection to either wired or wireless.

---

### Post by 73ckn797 on 2009-05-12
Go back to your first post and edit the title by inserting [SOLVED] in the title. It could be a help to others.

---

