---
title: "update kernel 2.6.20-17 than wifi got problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by wsetyonugroho on 2008-08-26
every time I did update to new kernel 2.6.20-17 as suggested in update manager, my wifi cannot connect to my wifi router. 

my laptop is compaq presario M2000 with broadcom chipset.
curently i'm using 2.6.20-16

also I notice that my internal card reader cannot read memory stick pro duo from the adaptor, since I upgrade to 2.6.20-16

please help
thanks

---

### Post by coffeecat on 2008-08-26
To have got the -20 kernel must mean you have enabled the Proposed Updates repository. [You need to read this]("https://help.ubuntu.com/community/UbuntuUpdates"). Particularly:

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.Check in Synaptic under Settings > Repositories > Updates and untick Proposed updates if it is selected. If it was, and you have now unticked it, close the Software Sources window, click on Reload, then 'Mark all Updates' and then 'Apply'. Hopefully, that will uninstall all the proposed packages. Reboot into your -19 kernel and post back if you have any problems.

**Edit:** Sorry - I didn't see you were still using the -16 kernel. What I have just said will (hopefully) remove all the broken stuff, but also bring you up to date with the -19 kernel. That is a stable kernel and shouldn't give you any problems - unless, did you have to compile the Broadcomm driver against the kernel? If so, you have to recompile it each time you do a kernel upgrade, so you may have to recompile it against the -19 kernel for it to work. Nevertheless, that doesn't diminish anything I said about avoiding proposed updates.

---

### Post by wsetyonugroho on 2008-08-26
thanks coffecat.
it was untick. and I never enabled it.

and I dont have problem with my wifi curently with 2.6.20-16.
the problem only occure if I do update to -17

is there any problem solving to read my memory stick with curent kernel ?
I dont use it very often though, but knowing that one of my card reader does not working, it bugging me.

---

### Post by coffeecat on 2008-08-26
> **wsetyonugroho said:**
> and I dont have problem with my wifi curently with 2.6.20-16.
the problem only occure if I do update to -17

**wsetyonugroho**, I must apologise. I misread you first post, assuming you were using Hardy Heron (8.04). You are obviously using an earlier version. I saw the 20 and didn't read the kernel version carefully enough. Ignore what I said about the Proposed Repository, except: never enable it. :)

But I think your problem is down to the Broadcomm driver needing to be recompiled against the -17 kernel. I have no experience of broadcomm wireless, so please post a link to the method you used to get your wireless going in the first place, and I or someone might be able to help you with that.

And - what version of Ubuntu are you using?

And I don't know about the card reader. Please post some details of the hardware you are using.

---

### Post by wsetyonugroho on 2008-08-26
I'm using feisty 7.04.
And I was using  "HOWTO: Broadcom 4318 Wireless Cards" to setup my broadcom. forgot the link, because I saved the web instead of the link.

When I update to -17 my wifi still be able to detect the hotspot, but unabled to connect. It was connecting in progress all the time.

---

