---
title: "Wireless Laptop as Ethernet Bridge"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by allnightarockin on 2007-12-05
I have a wifi a card in my laptop. I would like to take the signal i get from my wireless access point and connect my PS2 or my other laptop up to the internet/network through the ethernet cord on my laptop
So it would look like this
Modem>Router>Ubuntu WiFi> Ethernet/Cat5 Device

Any help would be appreciated..
I suppose i could bridge the connection between my wifi and ethernet cord but im not 100% sure how to do that..
i am semi-new to Ubuntu but i know the basics and a little bit more, so any hints you could give me would be amazing =]]

Thank you, and hope to hear back soon.
-Robert

---

### Post by Friek on 2007-12-05
That shouldn't be too hard. I've done it once too.
You need to install bridge-utils. Then you'll have to do something like:
```
brctl addif br0
ifconfig br0 up
```

Delete the IP from your wlan interface and add it to your bridge interface, for example:
```
ip addr del 192.168.11.14/24 dev wlan0
ip addr add 192.168.11.24/24 dev br0
route add default gw 192.168.11.1
```

Now you've lost your network connectivity, and you have to configure the bridge:
```
brctl addif br0 wlan0
brctl addif br0 eth0
```

That should restore the connectivity _and_ add your non-wireless nic to the bridge. With this configuration it should be working. I haven't tested it, but it should go fine.

Good luck :)
(ofcourse you need to replace the interface names and ip's if their named/numbered differently)

---

### Post by allnightarockin on 2007-12-05
Thank you for replying so quick Friek..

I had a bunch of stuff here but it doesnt apply anymore so i am just gonna edit it out =]

Please read next post though, im still having issues.

---

### Post by allnightarockin on 2007-12-05
I decided to try and figure it out myself..didnt workout so well
br1= My bridge
192.168.1.147 = My Local IP


How i thought to make a bridge in BRCTL [Bridge-Utils]
you type ```
 sudo addbr br1
```
followed by
```
 ifconfig br1 up
```
followed by
```

ip addr del 192.168.1.127/24 dev eth1
ip addr add 192.168.1.24/24 dev br1
route add default gw 192.168.1.1
```
then
```
brctl addif br1 eth1
brctl addif brq eth0
```

Does this look correct?? it didnt seem to work for me, br1 became unrecognizable and i couldnt connect to anything

i fixed it by typing ifconfig br1 down.
then deleting the bridge in BRCTL


Do you know what could be going on??
Screen Shot with ip info:
[IMG]http://img530.imageshack.us/img530/5122/screenshotconnectioninffu1.png[/IMG]

My routing configuration after my last attempt (when i deleted it all)
Terminal:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         DD-WRT          0.0.0.0         UG    0      0        0 eth1

```
Please let me know if you need more information. This would be so useful for me..
im just not 100% sure how to set it up

---

### Post by Friek on 2007-12-06
Hmm, the way I did it work alright. However, I now read that some wireless nics don't do the job. Read [this site](http://www.linux-foundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21) for some explanation.

---

### Post by allnightarockin on 2007-12-10
Good Link, thank you!
Will read more into it tonight 
=]

---

### Post by antineutrinos on 2008-07-17
> **Friek said:**
> Hmm, the way I did it work alright. However, I now read that some wireless nics don't do the job. Read [this site](http://www.linux-foundation.org/en/Net:Bridge#It_doesn.27t_work_with_my_Wireless_card.21) for some explanation.

Friek, many thanks for pointing this link out ! 
I tried to do all this bridging thing yesterday, did what you told (but before I found this thread). Off course it didn't work, but I didn't understand why... now I have a real, true final answer (rare in Linux world sometimes).

thanks also to allnightarockin for the perfect title ;-)

Cheers

---

