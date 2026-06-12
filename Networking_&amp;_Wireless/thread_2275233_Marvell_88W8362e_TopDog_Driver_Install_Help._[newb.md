---
title: "Marvell 88W8362e TopDog Driver Install Help. [newbie]"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by alan59 on 2015-04-24
I am looking for some assistance in the proper procedure for installing the missing wireless driver for my laptop. I recently wiped Vista from a Gateway model MT6458 and installed lubuntu 32 bit 15.04. I copied the oem1.inf, netmw147.inf and MRVWN.sys files that the Vista driver was using to a flash drive before I changed the OS.


I am not sure if I can use NDIS wrapper to use this driver from Vista, or if the Marvell driver for linux kernel 2.6+ is the best method. The later involves recompiling my kernel and I did not know if that is normal for a driver install. [REF: [http://www.marvell.com/support/downloads/search.do](http://www.marvell.com/support/downloads/search.do) ]

Thank you in advance for the assistance!

Here is what I have for system details:

Strong driver name [From Vista]
oem1.inf:Marvell.NTx86:W8385_11abgn_PCIx86.ndi:1.0.2.53:pci\ven_11ab&dev_2a08&subsys_2a0811ab

alan@alan-GW:~$ lspci
 05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8362e [TopDog] 802.11a/b/g/n Wireless (rev 03)

alan@alan-GW:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


alan@alan-GW:~$

---

### Post by kunitoki2 on 2015-04-24
Hope this helps: 2 or 3 months ago I helped a friend to get rid of Windows and hook his laptop up with Lubuntu. Everything went smooth except Marvell Wifi wasn't recognized of course. But the NDIS + INF file method worked very well. Well at first. The passphrase windows kept popping up even when already connected. Turns out WEP was the problem. Switched to WPA (which is recommended anyway since WEP is crackable) and now everything's perfect. So you already saved the driver (INF files etc) which is great. Now duckduckgo ubuntu marvell topdog to find the commands you need to enter for the NDIS wrapping procedure. These are just three or four so don't worry, it's not that complicated. Please keep posting (even if it works and maybe how you got it to work).

---

### Post by alan59 on 2015-04-25
I found a link with some instillation instructions, [[http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu]](http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu]), I followed all the steps and the wireless is not yet working.

I copied two inf files from the Vista install so I went back through the steps listed in the link above, but I am now getting an error stating
[SIZE=3]**"module configuration already contains alias directive"**[/SIZE]
When I run "sudo ndiswrapper -m"

What do I need to do to undue links to the first inf file?

Here is a log I made of the terminal output, if that may be of some assistance.
[ATTACH]261508[/ATTACH]

---

### Post by alan59 on 2015-04-25
Just a quick update, I followed [this]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Compiling_the_latest_version_of_ndiswrapper") ubuntu guide on ndiswrapper and removed it and rebuilt it, however I get some errors when using make build.

I went back through each step in this [other]("http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu") guide, and tried the other inf file taken from the Vista install.

All the commands seem to be working, but when I have entered them all in and I check iwconfig it still shows no wireless extensions.

---

### Post by alan59 on 2015-04-27
So it turns out the driver I was trying to use from the vista install is not going to work. I decided to just try the drivers that were linked in the how to post and it worked. I can see the wireless adapter now. 

References,
HOW TO GUIDE: [http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu](http://kevintechnology.com/post/841536945/installing-gateway-m6755-wifi-drivers-for-ubuntu)
Drivers: [http://www.kevinschicken.com/downloads/NetMW14x.zip](http://www.kevinschicken.com/downloads/NetMW14x.zip)

---

