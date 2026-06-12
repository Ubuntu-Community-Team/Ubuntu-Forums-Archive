---
title: "Swapped Hard Drives, now I can't connect to Internet"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Gh0stie on 2009-01-29
Hello, 

I did a dual-boot install of Ubuntu last weekend and everything went great. However sometime during the week my fan failed (pre existing condition) and I swapped my hard drive into a different identical box. 

The problem I'm having is I can't seem to connect to the web through my Time Warner modem (via ethernet) at home on either Windows or Ubuntu(works just fine at work)

On the Ubuntu side I get a msg in the title bar saying my Network Manager is disabled and I cannot seem to figure out how to enable. I already tried right clicking, as well as opening from the Application Menu

Any one experienced this or got a possible solution?

Thanks

PS: Both Boxes are Lenovo T-60s

---

### Post by Redache on 2009-01-29
Have you checked in Bios if any of the USB ports are turned off?

Does the modem actually light up when plugged in?.

I'd also check the BIOS to see if the Ethernet is enabled as this might be causing a problem with Network manager.

---

### Post by ranch hand on 2009-01-29
Are you sure that the modem is at the same address on both boxs?

---

### Post by sydbat on 2009-01-29
ranch hand might be onto something. You may have to set up the MAC address for the "new" box in the router/modem. 

Do you have the manual that came with the router? It will give you the information on how to access it via your browser...it will be something like typing 192.168.1.1 in the address bar of Firefox. This will get you into the router where you can change settings.

---

### Post by egalvan on 2009-01-29
> **ranch hand said:**
> Are you sure that the modem is at the same address on both boxs?

This is set by the OS network stack, it has nothing to do with the hardware it's running on.

UNLESS his modem uses MAC filtering; but if both boxes connected before, both MAC's should be registered.

Moving the hard drive *should* move everything, and given that they are identical Thinkpads, this should work out-of-box.

They *are* identical Thinkpads, right?

---

### Post by GepettoBR on 2009-01-29
Just to put it out there, the network hardware on the "new" box did work before, right? Since you're using the same hard drive it's obviously either a hardware issue on the new computer or a permission issue with the modem.

---

### Post by Gh0stie on 2009-01-30
thanks all......

Redache I will check the bios, but my usb ports work so I'm not sure this might help

@ everyone else, yes they are identical Ibms........just abit of more history

This current Lenovo box has been mine for a year or so, and connected fine at home on windows with no issues. Then a few months ago the fan started failing and my IT dept swapped me into a loaner while they repaired mine. I did the Ubuntu install on the Loaner and as it turns out, it started failing as well (known issue with those things). So I was swapped back into my original box which had now been fixed

This is the box which has refused to connect on either Ub or XP at home

I guess the only thing left to do is to explore the modem some more, I don;t have the manual for it but I'm sure it can be found pretty easily since it is TWC generic 
but again works fine at the office

thanks all

Also, I have another HP Notebook at home which works just fine on the same modem

---

