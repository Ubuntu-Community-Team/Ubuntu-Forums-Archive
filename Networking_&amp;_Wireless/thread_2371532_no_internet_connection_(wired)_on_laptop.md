---
title: "no internet connection (wired) on laptop"
date: 2017-09-15
forum: Networking &amp; Wireless
---

### Post by wwdwgs on 2017-09-15
My laptop lost wired internet connection. When I plug in ethernet cable, steady green light is on. No orange/yellow light, no blinking.
I re-set all - modem, router, switch. Still, there's no connection.
I used another laptop to connect to internet (via the same cable) and there is connection (that's why I'm here).
I read a few posts on checking internet specs, after which I suspect that the motherboard (network part) is faulty.
I need to confirm my suspicion with you, guys.
BTW, the ethernet port of lap I'm using now shows only steady amber and blinking amber lights (blinking amber, where green usually is).
So, presently the modem is working, the router is good, the switch is also working. The lights on switch are green (left position).
The router is linksys, the switch is netgear GS108.
Let me know how I must diagnose the problem (from terminal?). Please note that I'm "an end user".
Thanks is advance.

---

### Post by aromo2 on 2017-09-15
You have proven all the network equipment (including the cable) to be okay. So the problem is on your laptop.

Do you have DHCP enabled? (you won't be able to access the network if you use a static IP address that does not belong to the local subnet, or conflicts with another device in that subnet)
Are you getting the same speed as your test laptop? (if you force your network card at 1Gbps, but your switch's max speed is 100Mbps, you won't be able to connect)
Can you test your laptop on another network?

That's what I'd do before pointing to a defective network interface. Good luck!

---

### Post by wwdwgs on 2017-09-15
Aromo2,
DHCP was enabled. Currently (on working computer) DHCP is set to "automatic".
Speeds: 
looking at the switch - the cable connected to current (working computer) displays both lights in green (1000M bps), the cat5 cable running to the switch shows left green (100M bps). Even with these speeds, my current computer connects to the internet.
ip static or not - the same set up worked yesterday on the old laptop (which doesn't connect now), normally, IP is not static.
Testing my old laptop on another network is not possible.
I just installed network printer and it works, therefore the network functions.

Conclusion: my old laptop is bad, at the least, it's network "chip/card".
I could:
get a USB to RJ45 adapter and try to connect via usb port or
get another motherboard, or
get another laptop.

I'll try USB-RJ45 adapter first (not today - I'll need to order it).

Let me know if I miss something.

---

