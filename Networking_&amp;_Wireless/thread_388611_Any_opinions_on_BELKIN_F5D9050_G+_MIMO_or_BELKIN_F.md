---
title: "Any opinions on BELKIN F5D9050 G+ MIMO or BELKIN F5D8051 N1"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by bhutz on 2007-03-19
I was using the F5D7050 wirless USB but I'm not happy with it's range...has anyone tried

**BELKIN F5D9050 G+ MIMO** 
[IMG]http://www.pcworld.co.uk/images/186533_01_huge.jpg[/IMG]
or **BELKIN F5D8051 N1**?
[IMG]http://www.pcworld.co.uk/images/325877_01_huge.jpg[/IMG]


Also, are they supported out of the box?

I checked here [http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)
and there seems to be a driver for F5D9050 and an open source project for the drivers [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

Any info on F5D8051? The fact it's twice the price and doesn't seem to have much help available for it might keep me away from that one.

---

### Post by kenbuntu on 2007-04-01
hey, i tried that first wireless usb adapter.

it was very poor, 
in size, and in function.

so i switched over to the card version of it..

can you tell me a couple of things please..? im new.

alright, how do i make a new post?

and i have the wireless card version instead of the usb, so is that "f5d9050" number the same for both?

any help would be much apprectiated..

i just need to make a post on how to get that card to work.

unless you know how..?

thanks.

---

### Post by mikawber on 2007-04-06
does anyone know if the Belkin F5D8051 N1 USB card will work? I want to install Ubuntu on my old desktop but thats my network card for it. Anybody?

---

### Post by bhutz on 2007-04-18
I bought the BELKIN F5D9050 G+ MIMO in the end (Top image) and it's working well, I would recommend it...unfortunately I have no idea how to get the card version working, sorry

---

### Post by craigsn on 2007-04-24
Hello bhutz,
you say you got the Belkin f5d905 usb adapter working for you. I just installed Feisty Fawn, would you point me to the driver you are using? In your first post you mention 2 places, but neither of them seem to have the drivers for ubuntu. Or do I need to do something with them to make them work?

Thanks
Craig

---

### Post by Christopher Chadwick 1985 on 2007-04-24
I am hopeing to get a belkin card on tuesday, I will let you know how it gose I looked around and there is a wireless G network card for belkin that work's out the box but it is for a old distrobution anyone know how it work's in feisty fawn? I have the older version of Ubuntu Dapper Drake and it is supported by that distro so if feisty it won't be to bad.

---

### Post by craigsn on 2007-04-24
Sounds good. thanks for the update. Keep me/us posted.

Craig

---

### Post by Christopher Chadwick 1985 on 2007-04-24
Will do, I am also looking at a Netgear card it depend's what is in the shop at the time but I will let you all know when I have it working :)

---

### Post by bhutz on 2007-04-24
I'll have a gander tomorrow when I get back to my Ubuntu box...I think the console commands I used should be in my bash .history so should be able to figure out what I did from that :)

---

### Post by Persian_Sniper2000 on 2007-09-25
> **mikawber said:**
> does anyone know if the Belkin F5D8051 N1 USB card will work? I want to install Ubuntu on my old desktop but thats my network card for it. Anybody?

i have this **** ... not supported by linux ... i donno what can i do ... i searching for drivers but can't find :-(   that's sucked

---

### Post by hpotar on 2007-10-10
I just bought one today --an F5D8051 N1 and managed to get it working with ndiswrapper.  The netmw245.inf file is on the installation CD. You can simply do the following: 

plug the card directly into the slot (without the base and the long cable) 
apt-get install ndiswrapper-common ndiswrapper-utils-1.9;
ndiswrapper -i netmw245.inf; 
modprobe ndiswrapper;
 vi /etc/modules and add ndiswrapper on a new line. 

Had a hard time finding the chipset listed anywhere, .. (I ended up on the Marvell Semiconductor site, etc..) Either way, ndiswrapper will have to do and it's working fine.

---

### Post by madmatrixz3000 on 2007-10-12
How were you able to get the F5D7050 to work.  I am going mad trying to get it working.

---

### Post by hpotar on 2007-10-12
I didn't buy the 7050, but it looks like it uses an ralink chipset..  uses rt73.. 

I found this link for Gentoo that you may want to try out.. 
[http://gentoo-wiki.com/Belkin_F5D7050](http://gentoo-wiki.com/Belkin_F5D7050)

What have you tried so far?

---

### Post by madmatrixz3000 on 2007-10-12
I have tried reinstalls, ndiswrapper, GTKwifi and thats it.

---

