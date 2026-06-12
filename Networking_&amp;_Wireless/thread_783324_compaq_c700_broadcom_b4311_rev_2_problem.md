---
title: "compaq c700 broadcom b4311 rev 2 problem"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by jareddlc on 2008-05-05
has anyone succesfully got this chip working in hardy heron? ive tried many methods posted here on this forum but non so far? ive tried using b43-fmcutter and ndiswrapper, but i have the same problem when i click manual configuration, i don not have wireless network established, i have modem and wired network but not wireless, if i add an airlink usb adapter it works like a charm, but not with my b4311 rev2 any ideas or suggestions?

---

### Post by bonevg on 2008-08-25
> **jareddlc said:**
> has anyone succesfully got this chip working in hardy heron? ive tried many methods posted here on this forum but non so far? ive tried using b43-fmcutter and ndiswrapper, but i have the same problem when i click manual configuration, i don not have wireless network established, i have modem and wired network but not wireless, if i add an airlink usb adapter it works like a charm, but not with my b4311 rev2 any ideas or suggestions?

Well, hope I can get ya out of the tunel.
I`m using the same broadcom on hardy and I somehow manage to get it workin,but after hundred of post and s***s I read.
Here it comes:
 1st uninstall any ndiswrapper thingies you have previously installed. (dpkg --purge) them where possible.
 2nd apt-get remove b43-fwcutter (if you had it previously installed)
 3rd check if u have leftovers in /lib/firmware (like b43 or b43XXXX things and delete them manualy if there are such)
 4. Update to latest kernel with apt-get (mine is 2.6.24-19-generic)
 5. apt-get install b43-fwcutter (it will ask you if you wanna extract the firmware - confirm that)
 6. reboot your LapTop (and make sure you have the wireless card enabled in your BIOS).
 7. In my case I`m using Gnome (not that I don`t have kde packs too) but click on System -> Administration -> Hardware Drivers, and then check if you have the Broadcom b43 Wireless Driver`s check.. check it if it isn`t.

That should do the job. (but only with this kernel.. or newer)
I`ve also tested it with 2.6.25 -> works like a charm with the b43-fwcutter, but only when it`s installed manually.

P.S. the b43-fwcutter is firmware installer (extractor) for the Broadcom chips` firmware. I suspect cuz it is not opensource or/and generic driver there are some restrictions and EULAS u have to agree with.. That`s why those "chip makers" R makin` our life harder.. However Wish you GL with that :) Hope it will help you stop wondering - Why the hell regular Laptop with standard Broadcom won`t work with the best supported Distro..

Best Regards /FreeBSD & Linux Fan/

BIG NOTE: Sorry for the Edit.. Just reboot after Updating Kernel and Deleteing / Installing b43-fwcutter..
I just forgot to mention it /srry writing this from work/

---

