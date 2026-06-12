---
title: "Networking Basic"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by spoonman184 on 2007-08-24
Hi. I have been thinking of installing Linux for some time. But, my personal computer is on a network with several other computers, all of which are running Windows XP. 

I was wondering if I installed Ubuntu on my personal computer if it would still be able to connect to the internet, even though the rest of the network is running a different OS.

My network card is a Microsoft Wireless Notebook Adaptor MN-730. If any more information needs to be supplied, as router or modem model, let me know.

---

### Post by band-aid on 2007-08-24
The operating systems of the other computers on your network have no effect on how your computer accesses the internet. Accessing network shares will require you to have samba installed in linux, but this is so easy to do that its practically a non-issue.

sudo apt-get install samba.

---

### Post by spoonman184 on 2007-08-24
So then Ubuntu has a  built in networking system very similar to Windows XP and I should be able to connect to the network just fine?

---

### Post by spoonman184 on 2007-08-24
So I am going to be able to reconnect to my network once Ubuntu is installed, am I right?

---

### Post by Kaptain Chaos on 2007-08-24
Hi,
There shouldn't be any problem - if you want to check it out first, just pop the Ubuntu live CD into your PC and boot your system. Try it out from there before committing yourself. You'll be able to test drive the whole internet access issue; once your satisfied click on the 'install' icon.
If there are other PC's on the network you need to access files from then these 2 threads:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%20samba%20#9069058131484883352]("https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=%20samba%20#9069058131484883352")
and
[https://help.ubuntu.com/community/SettingUpSamba?highlight=%20samba%20#2661392104126874613]("https://help.ubuntu.com/community/SettingUpSamba?highlight=%20samba%20#2661392104126874613")
should help.

---

### Post by Kaptain Chaos on 2007-08-24
Just a quickie - here's an excellent visual demo for networking
[http://screencasts.ubuntu.com/videos/20070704_samba_filesharing_1280x720.html]("http://screencasts.ubuntu.com/videos/20070704_samba_filesharing_1280x720.html")
There's also several other guides at this site - explore!

---

### Post by spoonman184 on 2007-08-24
I donwloaded Ubuntu and ran it on a bootable cd. However, when I try to connect to the network in the upper right hand corner, it hangs after I try to connect and fails.

I have entered the essid correctly, because I checked the network name in Windows XP. I have entered the WEP key correctly as well. 

I also tried to connect to another available network within range without encryption. I couldn't connect to this network neither. 

Is my hardware supported in Ubuntu?

PCI Ethernet Card: Microsoft Wireless G PCI Adapter MN-730
Router: Microsoft Wireless G Base Station MN-700

Any other help would be appreciated.

---

### Post by spoonman184 on 2007-08-25
Full details-

I am working off of a bootable CD. My network card is of the Broadcam type. Is there any way I can get the drivers to work for the bootable CD version?

also, this is displayed when I type lshw in the terminal:
*-network:1 DISABLED
             description: Wireless interface
             product: BCM43xG 802.11b/g
             vendor: Broadcom Corporation
             physical id: 9
             bus info: pci@00:09.0
             logical name: eth1
             version: 02
             serial: 00:0d:3a:21:f2:f2
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:cfff8000-cfff9fff irq:5

---

### Post by Kaptain Chaos on 2007-08-25
Hello again,
It looks like you'll need to set up the wireless connection 'post-install' as the live CD doesn't connect you to the network. I have a wired home network so am unable to advise, however, have you tried the 'Official User Documentation' site? These 2 pages might give you a springboard in the right direction:

The main 'Community Documentation' page
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

and the 'Hardware Support' page
[https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

The second gives lists of hardware - specifically wireless network cards supported. My guess is that as the card and router are both Microsoft branded you may have problems getting them to work with any other OS.

Sorry, I'm unable to help you any further

---

