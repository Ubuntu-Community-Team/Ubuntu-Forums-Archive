---
title: "new user HELP!"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by keoni428 on 2010-04-09
I just got my new laptop and right when I get it I instilled Ubuntu 9.10
but I can't get the wireless work, I been searching the way to fix it but no luck
I still have window 7 in the laptop if I deleted it would it work?
 
I never use linux before I'm really exciting, feel like I been driving automutic car(window)my whole life
finally I got a stick car(Ubuntu) I believe it's not that hard but I need your help 
thanks

---

### Post by e4uforums on 2010-04-09
Deleting Windows 7 will not fix your wireless in Ubuntu.

You probably need wireless drivers to make it work properly.  What wireless card is in your laptop?

---

### Post by WinterRain on 2010-04-09
Check for drivers (with network cable connected to router or modem) in System>Administration>Hardware Drivers

---

### Post by hhlp on 2010-04-09
well we need more information example chip of the wireless card is usb or pci :

you can find this information using the follow command:

open a terminal and type :

Aplication -> accesory - terminal

lspci or lsusb or lshw

and post this information here

---

### Post by philinux on 2010-04-09
The way I got a laptop wireless going was to connect wired on install. Do an update through update manager or terminal and then try wireless.

That worked for me.

---

### Post by albert s on 2010-04-09
> **philinux said:**
> The way I got a laptop wireless going was to connect wired on install. Do an update through update manager or terminal and then try wireless.

That worked for me.


+1
that worked for me too,
also sorted out a few issues I had with my desktop and I just left it hardwired.  :)

---

### Post by norm7446 on 2010-04-10
As a last resort you could try installing ndisgtk. Full details are available at the below address.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

