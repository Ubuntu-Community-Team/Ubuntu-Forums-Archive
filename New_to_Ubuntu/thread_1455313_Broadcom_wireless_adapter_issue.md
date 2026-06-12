---
title: "Broadcom wireless adapter issue"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by sarahdee on 2010-04-15
Hey Everyone!

I just installed Ubuntu 9.10 on my Lenovo 3000 C100 and am having trouble connecting wirelessly.  The system came with a Broadcom 802.11 Multiband adapter which is still installed (the information below is from Windows System Information).  When I first restarted after the install I clicked on the NetworkManager to set up a new network.  My router (Netgear) is set to WPA-Personal and I entered all the information in the dialog box, but couldn't connect.  I followed the directions in the help section and ran the iwconfig command. The information that I got from it indicated that the adapter is disabled.  I know that it is not, primarily because my wireless LED was on.  I turned it off then on again to be sure.  I am currently connected using the Broadcom adapter through Windows XP so that I can get some info regarding this issue.  

Name    [00000011] Broadcom 802.11 Multiband Network Adapter
Adapter Type    Ethernet 802.3
Product Type    Broadcom 802.11 Multiband Network Adapter
Installed    Yes
PNP Device ID    PCI\VEN_14E4&DEV_4319&SUBSYS_044A14E4&REV_02\4&1D3F0FBB&0&10F0
Last Reset    4/15/2010 6:51 PM
Index    11
Service Name    BCM43XX
IP Address    192.168.1.4
IP Subnet    255.255.255.0
Default IP Gateway    192.168.1.1
DHCP Enabled    Yes
DHCP Server    192.168.1.1
DHCP Lease Expires    4/16/2010 6:53 PM
DHCP Lease Obtained    4/15/2010 6:53 PM
MAC Address    00:14:A5:8C:7C:3C
Memory Address    0xC0002000-0xC0003FFF
IRQ Channel    IRQ 22
Driver    c:\windows\system32\drivers\bcmwl5.sys (4.10.47.2, 415.25 KB (425,216 bytes), 11/23/2008 1:58 PM)

Any help would be greatly appreciated!  :confused:

---

### Post by ttshivers on 2010-04-15
You need to install a proprietary driver for it.

To do this:


[LIST=1]
[*]Click system
[*]Administration
[*]Hardware drivers
[*]Install the driver that applies to your hardware
[/LIST]

---

### Post by 2hot6ft2 on 2010-04-15
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")
And welcome to the forum.

---

### Post by kernelles on 2010-04-15
I just had the same problem. Turned out it was a firmware issue in my case. This fixed it for me:

1. Open System/Administration/Synaptic Package Manager
2. Search for b43-fwcutter
3. Mark for installation
4. Apply

What this utility does is locate the latest driver for the wireless adapter, then extract the firmware from it and install. 

Hope that helps!

---

### Post by sarahdee on 2010-04-15
> **kernelles said:**
> I just had the same problem. Turned out it was a firmware issue in my case. This fixed it for me:

1. Open System/Administration/Synaptic Package Manager
2. Search for b43-fwcutter
3. Mark for installation
4. Apply

What this utility does is locate the latest driver for the wireless adapter, then extract the firmware from it and install. 

Hope that helps!
Thanks for your suggestions, both 2hot6ft2 and kernells.  I checked out the Definitive 9.10 Broadcom Solution Guide and also tried to follow kernells suggestion but to no avail.  In the synaptic Package Manager I found the Broadcom modalias driver, but could never get the b43-fwcutter either in the installed packages or on the CD.  I think I am going to have to download b43-fwcutter from the link in the Broadcom guide.  The fact that I keep having to reboot to Windows doesn't help matters either.

---

### Post by kernelles on 2010-04-15
> **sarahdee said:**
> Thanks for your suggestions, both 2hot6ft2 and kernells.  I checked out the Definitive 9.10 Broadcom Solution Guide and also tried to follow kernells suggestion but to no avail.  In the synaptic Package Manager I found the Broadcom modalias driver, but could never get the b43-fwcutter either in the installed packages or on the CD.  I think I am going to have to download b43-fwcutter from the link in the Broadcom guide.  The fact that I keep having to reboot to Windows doesn't help matters either.

Sorry you're having such a hard time, Sarah. If it's any consolation, I'm new to Linux as well, and I've spent the last week trying to fix all kinds of little issues like this one after switching from Windows. I'm hoping once everything's finally set up, it will be worth it, lol. 

I hope you're able to fix the problem. Take care!

---

