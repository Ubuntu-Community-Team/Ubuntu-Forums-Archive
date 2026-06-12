---
title: "Rt2561 / Rt61 / Wpa"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by johnsjt on 2007-10-23
I have the MSI PC60G. LSPCI says its a RaLink RT2561/RT61 PCI card. This card has never worked out of the box with any linux distro. I had it working on Feisty, Linux Mint, and Xubuntu (Feisty) after screwing with the /etc/network/interfaces file for hours trying to figure out the right commands.

All of the guides I have found are outdated, and use old instructions, etc. I followed one guide here for 7.10 that used a 2500 chipset, to no avail. Also note that Network Manager finds the card, finds a list of nearby networks, including mine which is WPA TKIP, but will not connect to any of them. My SSID is not broadcast, so I usually have to manually specify this.

Right now I get the following:

ioctl[SIOCSIWAUTH]: Operation not permitted.
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not permitted
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120

The last msg is easy, I can just remove the pid, reboot, or stop the dhcp client.

I have never had to use any special driver, nor ndiswrapper. 

It is just aggravating that its 2007 and wireless support is still a command line deal, and a hope and pray situation.

Anyone have any suggestions, let me know. I have to type this from my laptop because it is my only other internet connection, so its hard to paste you multi-line config files. I'd have to type it out by hand because the ubuntu box is not online.

---

### Post by wieman01 on 2007-10-24
So you have tried the tutorial in my signature (the sticky one)? Did you do every step? Which module did you blacklist?

---

### Post by johnsjt on 2007-10-24
Yes, you also say use ndiswrapper. Why? never had to with Feisty(ubuntu,xubuntu), Linux Mint versions, SuSE, or Fedora. Of course all of these required edit to /etc/network/interfaces before they would work.

Also windows ralink drivers come in a setup program that has all the data inside some setup files that I can't see to decompress (unzip, unrar, etc). No way to get a .inf file. See the second post right under your tutorial. I am not the only one with this issue. I have not tried the MSI driver, but reading #3 post doesn't really make me want to.

The wireless is working it just wont work with my network. I'm using WPA1 with AES encrpytion. Something that has been around for a long time. I've used this setup with othe distros too. Network Manager shows other wireless networks in the area, all use WEP. I refuse to use anything less than WPA, and I wish my verizon router would support WPA2.

Looks like I might have to just break down and run cat5 into this room and throw away the wireless card. Will these things ever just work in linux? Granted they don't just work in any other OS, I guess its all in due time?

---

### Post by wieman01 on 2007-10-24
Then you'll have to be a bit more patient. The current Ralink driver is flawed. 

You are saying you cannot find the right Windows driver for your card? What about this for instance:

[http://www.driverstock.com/MSI-PC60G-driver-download/14-28-12540/index.html]("http://www.driverstock.com/MSI-PC60G-driver-download/14-28-12540/index.html")

Just do a bit of googling and you will find the right files for your card. Promise.

Anyway, not forcing you of course. It's entirely up to you.

---

### Post by johnsjt on 2007-10-24
I just don't understand how something can work, then doesn't. Is there any quality control? Testing? This chipset is listed as support hence why I bought it.

ndiswrapper is just a band-aid. I guess its nice if your chipset doesn't have any opensource drivers because your hardware vendor won't open its specs.

Actucally looking now it must be something with 2.6.22 kernel and/or a new beta driver being used. People have reported that going back to the feisty kernel fixed their problems, or using the legacy driver from the serialmonkey website.

If I felt like taking the time to make it work (again) im sure I could. But again, I shouldn't have to. It should just work... at least when the vendor has open drivers. Granted, on a Windows install, you have to install the drivers before the card will work, once you do... gasp, it just works. I might have to config WPA and such, but otherwise its up and ready to go. I am not trying to get into a war about whats better or not, just making a gripe that it should just work. And its more frustrating when it worked before, and you upgrade from one 'release' OS to the next 'release' and it stops working.

I thank you for the detailed ndiswrapper howto, but if im going to use Windows drivers, im just going to use Windows for now.

In short, I give up, back to the Evil Empire.

---

### Post by wieman01 on 2007-10-24
Good luck then.

---

