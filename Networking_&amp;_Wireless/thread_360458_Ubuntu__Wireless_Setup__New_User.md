---
title: "Ubuntu / Wireless Setup / New User"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by spooter on 2007-02-13
Hi all,

I have taken the plunge and installed ubuntu-6.10-desktop-amd64.iso on (Edgy) on my PC, I am completely new to this.  The install went quite well and was pretty simple but I have a couple of questions regarding my wirless setup which I will require if im going to carry on with Linux.

I have the Linksys WMP54G Wireless-G PCI Adapter which appear to have been installed as WLAN0 Wirless adapter is displayed in the Networking program.

After noticing the install I ran the Wireless Connection manager in sudo mode installed by default and displayed under applications/internet.
I can select WLAN0 (I also have a choice of WLANMaster, not sure why?)  WLAN0 scans for my Router wirless connection and finds it but when I click to connect and enter my WEP kep its fails to connect?  I have try connecting with WEP disabled but it still doesnt work.   I have the setting set to DHCP.

After thinking it could be the program I installed gtkwifi.  This program also detected my wirless network (cannot display signal strength for some reason) but also failed to connect either with or without WEP.  It does however say it failed to use DHCP?

Could someone please help me setup my wireles or explain what could be wrong?  Maybe the wirless card isnt installed properly? even though its displayed in networking and can detect my network?
Many thanks for your help.

---

### Post by teaker1s on 2007-02-13
you could install
[COLOR="Red"]network-manager-gnome[/COLOR]
to assist with connecting to networks

---

### Post by spooter on 2007-02-13
Hi,

Thanks for your reply, I believe I am already using the Network manager to try and connect to my Wireless router but it fails to connect.

---

### Post by derryk on 2007-02-13
I can't even see any networks at all, in my Ubuntu...

Seems like I have the same network configuration as you, however. One device is called wlan0 and another wmaster0 - but I cannot get an IP from my router, nor access it. What kind of router are you using?

Also, I tried that gnome-network dilly but it wouldn't let me install it. I did however install a program called "wifi-radar" which is availible in the Ubuntu community pages. Perhaps it will be a little more useful to you that it was for me.

Maybe try to open terminal and type in ifconfig - this will show all of your network devices and give you a readout to see if you have an IP at all - If not then you are getting the same problem as me. :mad:

---

