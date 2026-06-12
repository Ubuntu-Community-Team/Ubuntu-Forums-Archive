---
title: "Wired and wireless networks at the same time"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by aaginskiy on 2007-11-24
I can't seem to connect to both wireless and wired networks at the same time.  I currently connect to the internet through wired connection.  I also have a home server running to centralize data for my PC's.  I usually connect to both wired internet and wireless home network.  This works fine in Windows, doesn't even require any additional set up.  I just connect to both.  With Ubuntu I can't get it to work.  No matter what I do, it only connects to one or the other.

I can't connect the internet through the same hub as the network because the wired internet will only work on my network card (college connection).

Does anyone know how I can connect to both wired and wireless at the same time like on Vista?

---

### Post by kevdog on 2007-11-24
So wired is for WAN access, and the wireless is for LAN access??  Im not sure but I think you want the two different networking cards on two different subnets -- even still however Im not sure how you would tell the default application which network card to use.  I guess you would have to resolve by IP address.  I believe however there should be only one default gateway -- associated with the wired card or WAN card.

---

### Post by aaginskiy on 2007-11-24
Basically yes, wired is for WAN and wireless is for LAN.

Even on different subnets, it only connects either through my wired card or wireless card, not both.  I'm not really sure why it's so difficult to allow them both to run at once.  

Is there a guide detailing how to properly use /etc/network/interfaces?

---

### Post by gali98 on 2007-11-24
Okay try this. Not sure that it will work, but it won't hurt anything, and it makes sense to me.
```
sudo ifdown -a
```
This brings down all the network interfaces.
```
sudo ifup -a
```
and this should (keyword should) bring up all interfaces. Try this and see what happens.
Kory

---

### Post by jflaker on 2007-11-24
> **aaginskiy said:**
> I can't seem to connect to both wireless and wired networks at the same time.  I currently connect to the internet through wired connection.  I also have a home server running to centralize data for my PC's.  I usually connect to both wired internet and wireless home network.  This works fine in Windows, doesn't even require any additional set up.  I just connect to both.  With Ubuntu I can't get it to work.  No matter what I do, it only connects to one or the other.

I can't connect the internet through the same hub as the network because the wired internet will only work on my network card (college connection).

Does anyone know how I can connect to both wired and wireless at the same time like on Vista?

There is no benefit to connecting to the same network via wired and wireless.  You system will generally use the faster connection (only one connections).  It will not "shot-gun" over both connections to speed things up.  Even if you were able to shot-gun, you would still be limited to the bottleneck of the WAN or even the LAN connections which is slower than the 2 combined.  

In general, other systems (windows included) will disconnect the wireless and shut off the radio when a wired connection is established.

The only benefit to having both connections live is if you need to connect to 2 different networks with different resources during the same session.  This, however, is rare.  If this is your case, you can bridge your connections (how, I personally do not know) so the system sees both connections as a singe virtual connection.

---

### Post by aaginskiy on 2007-11-25
> **jflaker said:**
> There is no benefit to connecting to the same network via wired and wireless.  You system will generally use the faster connection (only one connections).  It will not "shot-gun" over both connections to speed things up.  Even if you were able to shot-gun, you would still be limited to the bottleneck of the WAN or even the LAN connections which is slower than the 2 combined.  

In general, other systems (windows included) will disconnect the wireless and shut off the radio when a wired connection is established.

The only benefit to having both connections live is if you need to connect to 2 different networks with different resources during the same session.  This, however, is rare.  If this is your case, you can bridge your connections (how, I personally do not know) so the system sees both connections as a singe virtual connection.

I'm not connecting to the same network twice, it's two different networks.  I don't know about systems in general, but I know for sure Windows can connect to multiple networks at once.  I will look into bridging.

Also, I did try turning all the adapters on and then back on.  It just turns them on, but it doesn't connect to both.

Rather odd, by the way I tested my set up on Vista and it works flawlessly, so I am positive that his doable.

---

### Post by kevdog on 2007-11-25
Can you connect to both different networks individually?

---

### Post by IamAcoconut on 2007-11-26
I might be wrong, but isn't this an issue with network-manager (nm-applet being it's frontend), which doesn't allow for more than one interface to be used at a time?

---

### Post by tact on 2007-11-26
> **IamAcoconut said:**
> I might be wrong, but isn't this an issue with network-manager (nm-applet being it's frontend), which doesn't allow for more than one interface to be used at a time?
Its not exactly an issue... it is how networkmanager is designed to work.

OP - if you have network manager installed its job is to detect which network interfaces are available and choose ONE...  the fastest ....  and connect to that, and if it loses that connection to automatically switchover and back again if the fast connection comes back up.

It does its job well.  :)     

You would need to uninstall or disable networkmanager (sorry I am not sure how as I have not had to do it).

Then you could easily use or edit a few start up scripts to bring both interfaces up whenever the computer is booted.  (again cannot help with this as i have not done it, but am sure its a trivial matter and maybe a dozen ways to do it).

---

### Post by IamAcoconut on 2007-11-27
The packages are** network-manager** and **nm-applet** (in gnome).
I have neither of them installed and everything's fine.

First go to Preferences->Sessions and disable nm-applet or any other entry associated with network-manager.
Then close nm-applet, and try using ifup / ifdown to configure both interfaces.

I'm not an expert, though I hope this will help.

It definitely can be done.

---

### Post by fwre01 on 2007-11-28
I was having exactly the same problem with network manager using both interfaces at once. However it can be done!!

From what iv tested (....and this is by no means extensive testing) both interfaces cannot be in roaming mode at the same time. So i switched my wireless interface to roaming and my wired interface to pick up a DHCP address (but not in roaming mode)

Then right click on the NM icon and you will notice both networking and wireless are ticked.

Then left click on the NM and connect to the wireless network, and the wired should get an address automatically if it is plugged in.

Even with both interfaces on the same subnet it works, if you look at your routing table by typing "route" from a terminal you will see you have two default routes, but one with a higher metric. you can change these values depending on how you want to manipulate your routing table. :grin:

---

### Post by tact on 2007-11-29
> **fwre01 said:**
> I was having exactly the same problem with network manager using both interfaces at once. However it can be done!!

From what iv tested (....and this is by no means extensive testing) both interfaces cannot be in roaming mode at the same time. So i switched my wireless interface to roaming and my wired interface to pick up a DHCP address (but not in roaming mode)

Then right click on the NM icon and you will notice both networking and wireless are ticked.

Then left click on the NM and connect to the wireless network, and the wired should get an address automatically if it is plugged in.

Even with both interfaces on the same subnet it works, if you look at your routing table by typing "route" from a terminal you will see you have two default routes, but one with a higher metric. you can change these values depending on how you want to manipulate your routing table. :grin:

Well it seems to work here too...  though once the wired network is no longer configured as "roaming" mode it is no longer controlled by networkmanager it seems and so does not appear on the nm-applet thing when you left click it.

So it seems that when you take an interface out of "roaming" mode - you remove it from networkmanager's control.  I guess that achieves (in a different way) what we were talking about when talking about disabling networkmanager.   No need to totally disable networkmanager, just remove one of the interfaces from its control.  :)

---

### Post by mlapaglia on 2007-12-12
the above mentioned idea also works for me on gutsy

---

### Post by alexei_colin on 2007-12-26
> **tact said:**
> Well it seems to work here too...  though once the wired network is no longer configured as "roaming" mode it is no longer controlled by networkmanager it seems and so does not appear on the nm-applet thing when you left click it.

So it seems that when you take an interface out of "roaming" mode - you remove it from networkmanager's control.  I guess that achieves (in a different way) what we were talking about when talking about disabling networkmanager.   No need to totally disable networkmanager, just remove one of the interfaces from its control.  :)

This is exactly what I am seeing. I have wired setup to use dhcp (via /etc/network/interfaces), and wireless to be in "roaming mode" (i.e. no entry in .../interfaces file). Things more-or-less work, but it is annoying that when set to dhcp the controller (in my case, wired) is outside of Net Manager's control. Does anyone know of how to include a controller into Net Manager without having to set it into "roaming mode"? 

Thank you!

---

### Post by seaq on 2007-12-29
the roaming trick worked like a charm, i was worried when i read the uninstall NM suggestions...  I added the network monitor applet in order to control the wired and wireless network, using wireless in roaming and wired without roaming and with dhcp.  Like this works as i want it to.

thanks

---

### Post by AKoine on 2008-01-03
@ Fwre01 :
That's exactly what I was desperately looking for ... Thanks a lot !!!

---

### Post by tarutaruomen on 2008-05-22
Definitely on the money!! Thanks for the suggestion.  Exactly what I needed.  Whew!

---

