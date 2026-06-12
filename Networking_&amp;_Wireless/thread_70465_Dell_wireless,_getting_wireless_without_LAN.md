---
title: "Dell wireless, getting wireless without LAN"
date: 2005-09-30
forum: Networking &amp; Wireless
---

### Post by laforge on 2005-09-30
Ok the problem is that my LAN slot does not work so i can only get wireless internet.  So all hte guides i have see have involved connecting to the internet to download something.  Well i can't do it.  I mean i can transfer things over from one comp to the next.  Is there a way to set up wireless only without haveing LAN working.  I would like this fixed ASAP i need internet for school tomorrow.

lspci
```

Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
Carbus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```
all i can see about wireless or networking in there.

I am running V5.04

---

### Post by davidknibb on 2005-09-30
If Ubuntu doesn't include the wireless drivers (there are some on 5.10 Breezy) then you will have to down load the driver and use Ndiswrapper.  I don't think that there is a way round it.

Unless you have a 'dial up modem' you can use to download the s/w ?

Or connect another m/c to the LAN, download, save to a USB memory stick and then copy to the m/c you want wireless on.

Or get a friend to connect their m/c and download etc

Cannot think of another way.

David

---

### Post by az on 2005-09-30
Ndiswrapper is included on your cd.  Actually, the driver is already in your kernel, but the utility is on the cd.  Just install the ndiswrapper-utils package.

Do you still have the windows driver from the wireless card (the cd that came with it?)  You will need that - that is how ndiswrapepr works.

---

### Post by laforge on 2005-09-30
So the windows driver wil work for linux?  I am pretty sure i kept it.
EDIT: Ok well i have them somewhere, i found one but i don't think it is the right one.  Also when i do find it how will it work if they are made for windows with .exe.  Would i have ot manually move them.  Will it work if I download them from dell.com or no?

---

### Post by az on 2005-10-02
[QUOTE=laforge]So the windows driver wil work for linux?  I am pretty sure i kept it.
EDIT: Ok well i have them somewhere, i found one but i don't think it is the right one.  Also when i do find it how will it work if they are made for windows with .exe.  Would i have ot manually move them.  Will it work if I download them from dell.com or no?[/QUOTE]

Read the documentation page about ndiswrapper on the wiki,

You need the .inf file.  The ndiswrapper utility can wrap itself around the windows driver and provide the functionality.

---

### Post by floyd27 on 2005-10-05
Not sure if this applies but my adsl modem allows for internet connection through USB.
Maybe you could access the net that way?

---

