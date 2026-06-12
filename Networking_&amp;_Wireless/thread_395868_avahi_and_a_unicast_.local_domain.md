---
title: "avahi and a unicast .local domain?"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Hangly on 2007-03-28
Feisty 7.06 Herd 5 I believe

Every time gnome starts up I get this popup:

"avahi-daemon disabled because there is a unicast .local domain"

I have no idea what that means, or how to fix it.  Googling revealed something about my domain having a .local entry that conflicts with avahi's or ubuntu's?  

To my knowledge I am not part of a domain, I only have a wireless router that occasionally hands out DHCP addresses.  So removing this conflict shouldn't cause any trouble.

In any case, I am unable to browse the local network, and I suspect this might be the cause.  Any advice on how to get avahi working again?

---

### Post by edonia on 2007-05-03
I have the same problem.

If i disable the DHCP function in my Netgear router, i do not get this popup. My Netgear router has the address 192.168.1.1 and the build in DHCP Server has no settings, which I can change.

---

### Post by gfowler on 2007-05-03
> **Hangly said:**
> Feisty 7.06 Herd 5 I believe

Every time gnome starts up I get this popup:

"avahi-daemon disabled because there is a unicast .local domain"

I have no idea what that means, or how to fix it.  Googling revealed something about my domain having a .local entry that conflicts with avahi's or ubuntu's?  

To my knowledge I am not part of a domain, I only have a wireless router that occasionally hands out DHCP addresses.  So removing this conflict shouldn't cause any trouble.

In any case, I am unable to browse the local network, and I suspect this might be the cause.  Any advice on how to get avahi working again?

I would imagine the wireless router is also setting up a .local domain by default.  If you can change this then your avahi should work.  Change it to .lan .private .uglyhomedomain, anything but .local

Jerry

---

### Post by edonia on 2007-05-04
> **gfowler said:**
> I would imagine the wireless router is also setting up a .local domain by default.  If you can change this then your avahi should work.  Change it to .lan .private .uglyhomedomain, anything but .local

Jerry
Any ideas, how to check, if the router has a .local domain?

---

### Post by gfowler on 2007-05-04
> **edonia said:**
> Any ideas, how to check, if the router has a .local domain?

Well, no.  Having said that, we could always wait until some Ubuntu/Debian/Linux network whiz comes along and throws a lifeline.  While waiting here is what I would try:

1.  Turn off router and let the machine boot up, note whether you get the avahi error.  You will no doubt have a 169.xxx.xxx.xxx IP address.

2.  Check your router's documentation, they most likely have some info on that. (no bets taken tho). 

You could drop to the command line and look at the /etc/resolv.conf and see what it shows i.e. cat /etc/resolv.conf  It should show your name server and search domain if the router is providing DNS services (likely) and is handing out this info via DHCP.

I've not been at this Ubuntu Linux stuff long, I just learned to spell Ubuntu last week :) 

Jerry

---

### Post by edonia on 2007-05-06
For just learning to spell Ubuntu, you have already a lot ideas about network issues :-)

So, no the docu tells nothing about. Without router or the DHCP in it, I get no ahavi error. The DNS is correct and shows the router address 192.168.1.1

For now, I disabled the NetworkManager, reserved my computer a static IP address on the router and start the network with the wpa_supplicat and WPA2 by hand with a small script I wrote.

Will see, if this problem get solved within the next few updates.

Anyway, if I gonna use the NetworkManager, it does not bring my interface up every time after resuming my machine from the suspend mode. After a few resuming, no Ubuntu GUIs is able to start ath0 anymore and so i could reboot, what I do not like. So set up all by hand with iwconfig, ifconfig wpa_supplicant and route.
Thats the way all is reliable working!


Uwe

---

### Post by gfowler on 2007-05-06
> **edonia said:**
> 

Anyway, if I gonna use the NetworkManager, it does not bring my interface up every time after resuming my machine from the suspend mode. After a few resuming, no Ubuntu GUIs is able to start ath0 anymore and so i could reboot, what I do not like. So set up all by hand with iwconfig, ifconfig wpa_supplicant and route.
Thats the way all is reliable working!

Uwe

I'm running a .local domain (an old SBS 2K thing) but I did not get the avahi error, DNS resolution was/is a bust.  I fixed that with an edit of nsswitch.  Network Manager went early on in the game, it did the same here, sometimes it would play well, other times, well I put it in permanent time out.  Found and installed WICD, that seems to work well (read having had big troubles yet).  It's over on SourceForge now I beleive.

I think the avahi/Network Manager was not quite ready for prime time, maybe it got rushed on stage a little early :) Hopefully updates will fix it before Gutsy comes out.

Jerry

---

### Post by edonia on 2007-05-06
> **gfowler said:**
> I'm running a .local domain (an old SBS 2K thing) but I did not get the avahi error, DNS resolution was/is a bust.  I fixed that with an edit of nsswitch.  Network Manager went early on in the game, it did the same here, sometimes it would play well, other times, well I put it in permanent time out.  Found and installed WICD, that seems to work well (read having had big troubles yet).  It's over on SourceForge now I beleive.

I think the avahi/Network Manager was not quite ready for prime time, maybe it got rushed on stage a little early :) Hopefully updates will fix it before Gutsy comes out.

Jerry
good hint, never had heard before from the WICD. The static stuff isn't working, it hangs on setting up the static DNS, but it works with DHCP, and I do not get the ahavi error message!?
strange behavior...
seems to be a NetworkManager issue, not the netgear router.

Do you have a applet symbol of the WICD? I haven't one.

Uwe

---

### Post by gfowler on 2007-05-06
> **edonia said:**
> 

Do you have a applet symbol of the WICD? I haven't one.

Uwe

Yes but I had to manually put it there, (gui.py).

Jerry

---

### Post by edonia on 2007-05-06
> **gfowler said:**
> Yes but I had to manually put it there, (gui.py).

Jerry
I just get a starter, but no applet symbol with mouse over functions :-(

---

### Post by gfowler on 2007-05-07
> **edonia said:**
> I just get a starter, but no applet symbol with mouse over functions :-(

Oh Oh, my bad, that should have been /opt/wicd/tray-edgy.py.  The gui.py is installed in the menu.
I'm running Kubuntu 7.04 but that shouldn't have any or much effect (I hope, after making that statement).

Jerry

---

### Post by edonia on 2007-05-11
> **gfowler said:**
> Oh Oh, my bad, that should have been /opt/wicd/tray-edgy.py.  The gui.py is installed in the menu.
I'm running Kubuntu 7.04 but that shouldn't have any or much effect (I hope, after making that statement).

Jerry
Yes, thank you it is working...nice to have the choice now :-)
Just found your answer, didn't recognized before, that this tread has now 2 pages...

---

