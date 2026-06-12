---
title: "Dis/reappearing wireless machines"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by mrdale on 2007-11-12
I have a bunch of machines (16) running edgy  and using WPM54G wireless cards with fixed IP addresses.  These machines are on various moving objects in an atrium.  They typically access a database server every few minutes and many of them grab images off the web every 30 seconds or so.  Every so often they will disappear from the network with no trace of why.  The only way they reappear (short of a reboot which is generally quite difficult since they are 20-40 feet in the air) is to beat on them with ping (which can take seconds to hours to have an effect).  I can't find any logs of them going off or coming back online.  they just do.  There are certainly vaguarities in the wireless signal and given that these things are moving through the space a can imagine something going out of whack but without any trace of an event it is hard for me to carp at the wireless administrators.  A possible red herring is that we are sure that one of the IP addresses gets hijacked every once in a while and this seems to cause a similar symptom that is only cleared with a reboot.  

Any notion where I might find breadcrumbs in this spaghetti?

Dale.

---

### Post by x64Jimbo on 2007-11-12
So you have computers flying around in an atrium? Are they attached to birds?
Have you tried switching some small things to try and find the source of the problem? Like using a different kind of wireless card, upgrading to Gutsy, etc? How are the static IPs kept? If it's client side, you may want to set the clients to DHCP and instead establish a list of static IPs in the router that will assign IPs based on MAC address of the client card. As for the hijacking, is it one of your own machines or an outsider? If it's not one of your own, you should encrypt the network with WPA encryption so they can't swipe your IPs anymore. 
Just a few ideas to try...

---

### Post by mrdale on 2007-11-12
FWIW They are flying around inside [_[COLOR="Blue"]these things[/COLOR]_]("http://www.flickr.com/photos/onomylabs/881179358/"). Well, really those blob-y objects and the zipper signs are moving and the computers are inside of them.

Changing hardware would be very difficult at this point as would an OS upgrade, though that is more in the realm of possibilities but relies on a stable wireless network to happen. And the statistics of the problem would likely mean wholesale changes, which is really high risk in a public setting like this.   And for the most part everything works just fine.

Can you say more about why relying on DHCP for an IP address is preferable to hardcoding it on the machine?  I get that it should lower the probability of two machines ending up with the same address but it cedes another piece of control to a not-so-diligently maintained infrastructure.

I'd feel a whole lot better with some ideas about how to track the problem before I go making major changes to things that may cause a lot more problems than solving this one.

---

### Post by x64Jimbo on 2007-11-12
The root of the problem most likely lies in one of two areas: driver problems or signal strength. One thing you could try would be to add an access point and see if that alleviates the problem. If so, it is a signal strength issue. However, since this project appears to be in an open area, I would guess that signal strength does not play a part in the issues you are having. 
In my experience, having static IPs set on client machines leads to problems because the DHCP server does not always realize that there are machines with static IPs, and it can assign a "static" IP to a newcomer machine. As you might imagine, this can cause problems. In my opinion, most router operating systems are quite simple, and can be deemed more reliable than desktop/laptop operating systems, so I never bother setting up static IPs on my client machines, and opt to use the router as the IP Police. 
Another option that you may want to explore would be to add an "awareness" script to a cron job on the client machines. It would basically ping the router. If a response was not detected, it would restart the network interface ($/etc/init.d/networking restart) and try again.

---

