---
title: "Ubuntu wireless problems"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by Vashu on 2007-01-31
I recently bought a HP Compaq NW9440 and wanted to install Ubuntu on it since I had successfully replaced my windows for ubuntu on my desktop for almost a year.

Since i knew Ubuntu and Linux all together had wireless issues I wanted to try out whether it would work before installing. Here's what I had: A Kubuntu 6.06 live cd and an Ubuntu 6.10 Alternate Installer. I don't like KDE but since that was my only live cd I booted it up and easily  got my wireless working and connecting to my router with just the wireless app kubuntu has, no extra drivers needed. 

Then I installed my 6.10 Ubuntu with the alternate only to discover it doesn't recognize my wireless card. Did I miss anything? how can an older version of a "variant" of Ubuntu have work perfectly and a newer version of the main distro not?

What are my choices if any?

Apparently i have an possible solution here [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) but I don't think i should install a 3rd party driver when i have already proven (K)Ubuntu has its own alternative.

---

### Post by renzokuken on 2007-01-31
ive seen this before in that livecds work and a proper installation doesnt when it comes to wireless hardware.

have you looked into ndiswrapper?

---

### Post by Vashu on 2007-01-31
Yes, it seems ndiswrapper works, but I wanted to keep it as a last choice, since I'm pretty sure that live cd wasn't using it.

---

### Post by hal10000 on 2007-01-31
Do I guess right, you are using an intel Pro/Wireless 3945 card?

If so, then the appropriate kernel module for this card is [COLOR="Red"]ipw3945[/COLOR]
So first try wether it is already loaded: [COLOR="Red"]lsmod | grep ipw3945[/COLOR]
if it is not loaded, then try [COLOR="Red"]sudo modprobe ipw3945[/COLOR]
and if successfully loaded configure you network.

---

### Post by Vashu on 2007-01-31
> **hal10000 said:**
> Do I guess right, you are using an intel Pro/Wireless 3945 card?

If so, then the appropriate kernel module for this card is [COLOR="Red"]ipw3945[/COLOR]
So first try wether it is already loaded: [COLOR="Red"]lsmod | grep ipw3945[/COLOR]
if it is not loaded, then try [COLOR="Red"]sudo modprobe ipw3945[/COLOR]
and if successfully loaded configure you network.

Alright, problem solved. While that was not the problem itself your advice led me the right way. turns out ipw3945 even thou it comes with the ubuntu package and is actually loaded at start up it seems not to really do anything until the restricted modules package is installed. After that i just restarted (i know i could have just reloaded the module) and it was working.

Thanks a lot for the help. :D

---

### Post by Balinsky on 2007-02-08
> **Vashu said:**
> Alright, problem solved. While that was not the problem itself your advice led me the right way. turns out ipw3945 even thou it comes with the ubuntu package and is actually loaded at start up it seems not to really do anything until the restricted modules package is installed. After that i just restarted (i know i could have just reloaded the module) and it was working.

Thanks a lot for the help. :D

I believe i am having the same problem you did. but i am a nub and dont know what the restricted modules package is. 

I think i am having the same problem because my 1pw3945 is recognized but refuses to work.

the wifi status light on my dell inspiron 7something is blinking and i know from using fedora that that light needs to be on constantly for it to work

---

