---
title: "won't change default gateway"
date: 2005-09-12
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2005-09-12
Usually, the Ubuntu system in the living room is connected through the wireless connection..

it always is "Default gateway device: ath0"..  but, now, it just says "Default gateway device:  " and doesn't select my device..  So, I click the pull down menu, and ath0 is there.  so when i select it, and click OK, i still can't get on the internet.  so I open Network Settings again, and guess what, it deselected ath0, and selected nothing..

why won't it save, and why did it just all of a sudden do this?

it says in the connections list "The interface ath0 is active", and it shows it has a signal and is getting data from the router, but it's not showing it sending anything at all...

please help, this is VERY important...  i tried restarting, and it still fails..

---

### Post by X5-655 on 2005-09-12
is there a command line to set the default gateway device?  this is getting annoying, and I seriously need the help!  this happens on my laptop quite a lot, but NEVER on my desktop..

---

### Post by KaiO on 2005-09-15
You can open a terminal window to change the gateway:
$ sudo route add default gw 192.168.0.1

---

### Post by X5-655 on 2005-09-15
[QUOTE=KaiO]You can open a terminal window to change the gateway:
$ sudo route add default gw 192.168.0.1[/QUOTE]
that doesn't help though, it's not THAT gateway...

this gateway the network control panel is talking about is which network adapter to use by default, and it won't select ath0, and I need it too, otherwise I have no connection at all.

---

### Post by cwaldbieser on 2005-09-16
[QUOTE=X5-655]that doesn't help though, it's not THAT gateway...

this gateway the network control panel is talking about is which network adapter to use by default, and it won't select ath0, and I need it too, otherwise I have no connection at all.[/QUOTE]
I think KaiO is correct.  Your system routing table determines where network packets are sent.  The default route in the table is the very last match that will be tried, and therefore any destination not explicitly specified in the table will be sent to that gateway by default.

In a typical home LAN situation, you would not have multiple NICs going to the same network.  Each network card will be on a different network.  So if your default route is set to 192.168.0.1 (which is your wireless router?), and your ath0 device is on the 192.168.0.0/24 network, then by default, any packets not specifically told to go somewhere else in the routing table will head out across your ath0 device.

If you type:
```

$ route

``` 
you will see the your routing table.

---

### Post by X5-655 on 2005-09-28
[QUOTE=cwaldbieser]I think KaiO is correct.  Your system routing table determines where network packets are sent.  The default route in the table is the very last match that will be tried, and therefore any destination not explicitly specified in the table will be sent to that gateway by default.

In a typical home LAN situation, you would not have multiple NICs going to the same network.  Each network card will be on a different network.  So if your default route is set to 192.168.0.1 (which is your wireless router?), and your ath0 device is on the 192.168.0.0/24 network, then by default, any packets not specifically told to go somewhere else in the routing table will head out across your ath0 device.

If you type:
```

$ route

``` 
you will see the your routing table.[/QUOTE]
but my question isn't being understood.

i was trying to tell ubuntu to use ath0, but everytime i click apply, it would forget and show no networking interface as default in the GUI...

---

### Post by leezer3 on 2005-09-28
First things first- Is your wireless device acutally active? 
Second, I assume from your post that it was working previously, so what have you changed/ updated? (Maybe you need to update the wireless drivers to keep up?)
If none of these work, then open up a terminal, and run > ifupdown eth0 to manually bring up the wireless card and post results. (I assume you mean eth0, not ath0)

Oh, finally are you SURE eth0 is your wireless device- My ipw2100 is on eth1

Cheers

-Leezer-

---

### Post by X5-655 on 2005-09-28
[QUOTE=leezer3]First things first- Is your wireless device acutally active? 
Second, I assume from your post that it was working previously, so what have you changed/ updated? (Maybe you need to update the wireless drivers to keep up?)
If none of these work, then open up a terminal, and run  to manually bring up the wireless card and post results. (I assume you mean eth0, not ath0)

Oh, finally are you SURE eth0 is your wireless device- My ipw2100 is on eth1

Cheers

-Leezer-[/QUOTE]
yes, I am sure it is Ath0, not Eth0..  Eth0 is the wired interface on this system..  i can't post the results right now as this system is right now under a livingroom table, as I took the RAM temporarily for a Macintosh that needed it for the time being..

---

