---
title: "Installing linksys wireless router?"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by drews_blunted on 2006-11-17
I just purchased a new linksys wireless router from newegg.com

My question is the product comes with a install cd im assuming its the windows install cd, but all over the package it says run cd first before anything!! Im not sure if this applys to me since its a windows cd but anyways im curious how to configure and setup a linksys router in linux? i hear the router itself is running linux, witch is cool! I supose there is a way to access the router through a web interface on your browser? anyone know much about these wireless routers. its my first time using anything wireless or a router.

Thanks in advance.

---

### Post by FrodoB on 2006-11-17
I can't remember the exact subnet it is on, it should be at one of these addresses.  Just point your brower at it:

192.168.1.1

or perhaps

192.168.0.1

do not enter a name and the default password is "admin"

Unless it is very old I do not think you will need the CD at all except for the PDF documentation that is on it.

Good luck

---

### Post by drews_blunted on 2006-11-17
Ok, let me see if i have this right? if i connect my cable modem to my router then the router to my pc. When i turn on the computer it doesnt show the internet as working. But now i can use my browse to go to that subnet you gave me and be able to configure the router to allow internet access?

Let me know if im on to this or not?

---

### Post by FrodoB on 2006-11-17
Without even involving your cable modem connect both your PC and the wireless router to a hub, or connect direct with a cross-over cable.

Read the quick install or the manual and it should tell you the default address for the device.

Set your PC to the static address 192.168.1.5 and then browse to 192.168.1.1

A password request page will appear. Leave the User Name field blank. In the Password field, enter the
password you have set (the default password is admin). Then click the OK button.

Once inside you can change the routers address to the one that you want to put it at.  If you change it out of the address range of 192.168.1.x as soon as you save that setting you will have to change the static IP of you machine to the network that you moved it to.

There is a good tutorial on this in the users manual for the WRT54GL, which I suspect you may have. At any rate the tutorial begins on page 32 of that manual.

---

### Post by rickyjones on 2006-11-17
My experience? Unpack router. Plug in power. Plug computer into LAN1. Plug cable modem into WAN. Set computer to DHCP. Browse to 192.168.1.1. Blank UN, "admin" for PW. Check to see if the router is getting an IP from the cable modem (it should, unless your cable company has something else going on.) Configure your wireless network settings to your desire.

Have fun!

---

### Post by drews_blunted on 2006-11-17
Ah Ha!! My internet is now working with my router. Suprisingly once i got into the setup program there wasnt many things to configure and after i accessed it. It started to work. :KS

---

### Post by Dragonlaw on 2008-04-12
> **rickyjones said:**
> My experience? Unpack router. Plug in power. Plug computer into LAN1. Plug cable modem into WAN. Set computer to DHCP. Browse to 192.168.1.1. Blank UN, "admin" for PW. Check to see if the router is getting an IP from the cable modem (it should, unless your cable company has something else going on.) Configure your wireless network settings to your desire.

Have fun!

THANKS!!! I FINALY MANAGED TO GET IN!!!

---

