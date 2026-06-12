---
title: "D-Link DWL G510"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Mysteek on 2007-01-16
I am new to the community. And a mate of mine called PhibreOptix told me to install ubuntu mainly because Windows sucks.

Well anyways, that's the expression he used, so yeah.

Well, I am on my windows pc at the moment and was wondering if it is possible to run my D-Link DWL G510 wireless card with Ubuntu.

---

### Post by hal10000 on 2007-01-16
This Link may be the right one for you: [http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)

---

### Post by Mysteek on 2007-01-16
My cards is highlighted green, so, does that mean it has drivers already built into support it, or do I need to get the myself?

---

### Post by hal10000 on 2007-01-16
I guess you have to download the drivers from the links listed, but I'm not sure about.

---

### Post by hal10000 on 2007-01-16
Here you can see comments from other people using this card:
[http://www.linuxquestions.org/hcl/showproduct.php?product=2115&cat=133](http://www.linuxquestions.org/hcl/showproduct.php?product=2115&cat=133)

---

### Post by Mysteek on 2007-01-16
Wow, quite confusing for a person who is used to windows like me, anyone able to explain in easier terms?

---

### Post by tturrisi on 2007-01-16
>  Wow, quite confusing for a person who is used to windows like me, anyone able to explain in easier terms?
No, not yet!
What version of the card do you have?
There are different drivers for each version.

---

### Post by mysticrider92 on 2007-02-01
I just got the version B1 of this card, and once I got it in the computer properly, Ubuntu set it up for me and all I had to do was type in the SSID and encryption key to get it connected.

---

### Post by rafciu123 on 2007-02-09
> **tturrisi said:**
> No, not yet!
What version of the card do you have?
There are different drivers for each version.

Hi,

I am a new user of linux and I have same issue. Links provided in previous posts
are to ovewhelming for me as they are for the author of the original post.
I know I have D-Link DWL GS510, 

***
lspci outputs:
03:06.0 Ethernet controller: Atheros Communications, Inc AR500G 802.11abg NIC (rev 01)
***
iwconfig outputs:
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions
***
/etc/network/interfaces:
interfaces(5)
iface lo intet loopback


Do I need to install some drivers for my card or it is already installed?
If it is installed I don't understand why I don't see any wireless 
connections in Network tool.
I would really appreciate step by step guidance on setting up my WiFi.

Thanks

---

### Post by tturrisi on 2007-02-09
> **rafciu123 said:**
> Hi,

I am a new user of linux and I have same issue. Links provided in previous posts
are to ovewhelming for me as they are for the author of the original post.
I know I have D-Link DWL GS510, 

***
lspci outputs:
03:06.0 Ethernet controller: Atheros Communications, Inc AR500G 802.11abg NIC (rev 01)
***
iwconfig outputs:
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions
***
/etc/network/interfaces:
interfaces(5)
iface lo intet loopback


Do I need to install some drivers for my card or it is already installed?
If it is installed I don't understand why I don't see any wireless 
connections in Network tool.
I would really appreciate step by step guidance on setting up my WiFi.

Thanks
Your card has an atheros chipset, needs to use the madwifi drivers.
Run Synaptic, enable MultiUniverse repositors and install linux-restricted-modules that match your kernel.  They contain the madwifi drivers needed.

---

### Post by rafciu123 on 2007-02-10
I run synaptic and try to add those packages but it tries to get them from the internet instead of installation CD. I get the following message:

Failed to fetch [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu), ...... <-- url to the package
Temporaty failure resolving security.ubuntu.com

When I check Add Cd-ROM it scans installation CD and in panel where all packages are displayed it displays none without returning any error message.

How do I force synaptic to read packages from installation CD?

Thanks

---

### Post by rafciu123 on 2007-02-11
I figured out problems with synaptic and I installed the following packages:
linux-restricted-modules-2.6.17-10-generic
linux-restricted-modules-common
linux-restricted-modules-generic

Is it possible that those packages got uninstalled during update process or when I switched repositories in Synaptic?
Synaptic shows those packages as darkened.

I had wireless network for some time, then I downloaded updates through synaptic /I think/ and I stopped seeing wireless connection in Networking manager after reboot.

iwconfig outputs:
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

Please advice.

---

### Post by OldGaf on 2007-02-19
This card worked with no problems under Edgy 2.6.17-10. I had to upgrade to 2.6.17-11 for the latest nvidia drivers and now the card is gone.

---

### Post by OldGaf on 2007-02-20
OK, I got my D-Link DWL-G510 (Atheros chipset) to work again under 2.6.17.11. It seems that 2.6.17.10 had built in madwifi support in the restricted modules that are eather missing or are broken in -11.

The solution was to get the MADWIFI driver and compile it under -11. 
It is very simple to do, just follow these instructions.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

If you do not have an Atheros chipset, try ndiswrapper (NOT the one in the repos....... get 1.37 and compile it.) Here is a simple set of instructions.

**NOTE: At this time 1.37 is the latest ndiswrapper. You will also have to change the Winblows driver for the one that matches your card.

[http://www.ubuntuforums.org/showthread.php?t=342558](http://www.ubuntuforums.org/showthread.php?t=342558)

BTW...... This is a BIG pi$$ off and a pain in the @$$ to have to do. This should have been picked up on before the release of -11.

---

### Post by rafciu123 on 2007-02-20
Are you using 64 bit Ubuntu? Only the one for amd64 was causing problems. My card started working out of the box after I installed 32 bit version.  I just entered network key!

---

