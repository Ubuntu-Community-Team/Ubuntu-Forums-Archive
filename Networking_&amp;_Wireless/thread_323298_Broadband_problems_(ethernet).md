---
title: "Broadband problems (ethernet?)"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by dyingsun on 2006-12-21
Hi all, Merry Christmas, or whatever seasonal festival you happen to be celebrating.
I recently got DSL going, via a USB connection, because my bundled ethernet seemed to have problems. When I got a DLINK wireless router, so I could run the laptop off it too, I had to use ethernet because it didn't have USB. I ended up buying a new ethernet card, which installed fine under Windoze, but the linux version won't install..I'm a linux newbie and stiull finding my way, but I've followed the instructions and when I try to make install it tells me the kernel source is not found, and aborts the install. As a result I can't get Ubuntu (dapper) to recognise my router. When I try to go to 10.1.1.1 it just tells me it can't find the server. So basically I can't connect to the internet through my router and it's driving me crazy...I'd set up home in Ubuntu and was very happy living there until I got cut off from the rest of the world...now Im trapped back in my old OS and I want out!

   I'm assuming the problem is with my inability to install the Ethernet drivers, and it's not some other simple thing I've overlooked?

'puter:  Dell Dimension desktop
Router: DSL-G604t
OS:      Dapper
Ethernet card: SOme generic thing, I don't think I have the box anymore, but the included driver is called "sl_linux.tgz"

Anyone got any suggestions? Are there any generic drivers I could try perhaps?

Thanks in advance,
Damien

---

### Post by Rippey on 2006-12-21
try doing this:
in console type: lspci | grep Ethernet

this should show you the ethernetcard you've installed, in my case it says:
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

RTL-8169 is the chipset of my card, when you know which chipset you have try:
modprobe RTL-8169

in most cases this will work, if you have to compile the driver that came with the card make sure you have the source code for your kernel unpacked in /usr/src with a soft link called linux to it in the same folder.

---

### Post by dyingsun on 2006-12-22
Hi Rippey, thanks for your reply..

> **Rippey said:**
> try doing this:
in console type: lspci | grep Ethernet


RTL-8169 is the chipset of my card, when you know which chipset you have try:
modprobe RTL-8169

lspci gave me this output:

0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
0000:02:0c.0 Ethernet controller: Unknown device 1904:8139 (rev 01)

...but I don't know which part the chipset is...I tried modprobing all the above strings in various combinations, but all i got was fatal: modules not found


> **Rippey said:**
> 
in most cases this will work, if you have to compile the driver that came with the card make sure you have the source code for your kernel unpacked in /usr/src with a soft link called linux to it in the same folder.

I know I sound stupid by asking this, but...how? When you say softlink, is that the same as an "ln" link? When I say I'm a newbie, I'm not kidding...a lot of this is alien to me! I'm usually happy to search around and find the answers I need on the web, but at the moment I have to keep switching between operating systems...boot up XP to do a search, then reboot into Ubuntu to try out the suggestions ](*,) 

Cheers!
Damien

---

### Post by Rippey on 2006-12-22
I think your new card is not recognised by ubuntu.
what you could try is downloading to kernel source for your kernel (uname -r to find out which kernel you're using) from kernel.org
then unpack it in /usr/src and make a link to the folder named linux using ln -s
than you should be able to compile the driver for your card.
I'm not completely sure if this will work since I never had to do this myself, but I think it should work

---

