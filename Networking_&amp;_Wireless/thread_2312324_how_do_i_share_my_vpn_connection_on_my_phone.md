---
title: "how do i share my vpn connection on my phone?"
date: 2016-02-03
forum: Networking &amp; Wireless
---

### Post by jose102 on 2016-02-03
Hi,

I am completely new to ubuntu and just freshly installed ubunto os on an old hp compaq 6515b

I wanted to share my phones vpn connection to it,i connect it to the pc but i cant surf,,

on windows,i used to use pdanet to do this,

for some reason i cant have clockwork mod tether to work,or ai cant even install it...
just says to decompile the file then run run.sh when i click on run doesnt do anything..

any other app that i might have missed similar to pdanet?

---

### Post by davehenson on 2016-02-03
So your problem is that you have ubuntu installed on your phone and you need an app (like pdanet) to enable tethering so you can use it as a hotspot. Is that correct?

---

### Post by Vladlenin5000 on 2016-02-03
> **davehenson said:**
> So your problem is that you have ubuntu installed on your phone and you need an app (like pdanet) to enable tethering so you can use it as a hotspot. Is that correct?

Incorrect. He wants to use USB tethering from his phone to the newly installed Ubuntu in the old HP notebook.

So...
VPN or direct is irrelevant here. The tethered device doesn't need to know / doesn't care how it gets the connection or where it comes from, provided the VPN is configured and works already in the phone and we can assume it is because it was working before with Windows.

The only relevant question is: **What phone?**

Any modern Android can do it for any modern (desktop) Linux without any app. Connect the USB cable, turn on tethering and in less than second a (virtual) Ethernet connection appears in the desktop. It just works.
If not (contemporary) Android, don't keep your hopes high.

---

### Post by davehenson on 2016-02-03
Vlad - if you're correct, and I believe you are, then an easier way would be for him to just turn on his wifi hotspot feature on his phone. I too at one time used PDAnet but now my phone doesn't need it. I just turn on the wireless hotspot (I guess its included in my plan now???) and connect anything I want.  I used to do the wired tether but got tired of dealing with cords.

---

### Post by Vladlenin5000 on 2016-02-03
Sure, that'll work too, provided the WiFi in the notebook is working (is it, José?) -and- the phone supports WiFi tethering (does it, José?).
Unfortunately I suspect the phone itself is the "problem". The use of PDANet somehow suggests "ancient" ;-) but I can be wrong (I better be wrong othewise this can easily turn into a troubleshooting nightmare).

---

