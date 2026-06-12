---
title: "Identifying which NIC is which"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by anvilsoup on 2007-10-30
I've got 10 ethernet ports on a computer. How do I identify which port is which? 

In Windows, if I unplug a cable it tells me which cable was unplugged.

In FreeBSD and Cisco routers, it tells me the Line Protocol is down if I unplug a cable.

How do I do this in linux? Or is there another way that doesn't involve another computer?

Edward
P.S. ifconfig doesn't seem to show the Line Protocol in Linux, and I don't know how to bring the interface down completely

---

### Post by kevdog on 2007-10-30
sudo ifdown <interface name>

That brings the interface down where interace name is eth0, eth1, eth2 etc.

---

### Post by Cypfer on 2007-10-30
This isn't and elegant solution but it will work.

to bring down and interface the command is, via command line
```
sudo ifconfig ethX down
```

where X is the number after the eth listed when you run ifconfig -a

once all your interfaces are down you can run dhclient after unplugging the ethernet port you want to identify and the interface that doesn't get an ip address is the one that is un-pugged.

syntax via command line for dhclient is

```
sudo dhclient ethX
```

the eth is optional if you don't specify the interface it attempts to get and ip address via dhcp for all interfaces at once.

---

### Post by anvilsoup on 2007-10-31
Interesting ideas. 

ifdown and ifconfig down won't turn off the interface (unlike with a Cisco router or in Windows). That is, the little lights are still on.

I don't really want to connect another device to the system. It's more of a theoretical challenge really.

Ed

---

### Post by kevdog on 2007-10-31
Do you really care if the light is on??  Short of taking the interface down (ifdown, ifconfig), the next step would be to unload the card's drivers (modproble -r).  Not sure if this is going to turn the light off for you!

---

### Post by anvilsoup on 2007-10-31
Thanks for the tips. I still wish there was a way to tell the line status. 

May be if I had the time to install ifplug it would tell me when I unplugged a cable. This probably is a good way, except I have dependency problems when I try to install it.

Eventually I finally figured out that:

```
/etc/iftab
```

maps the MAC addresses to the ethernet addresses. This fixed another problem that I was having - the NICs no longer change their names on reboot.

So all I needed to do is to map them manually and everything is now good.

---

### Post by Whiffle on 2007-10-31
ethtool ethX

---

### Post by anvilsoup on 2007-11-04
Cool. 

ethtool ethX

works for me. I can make the lights blink for the onboard card, but I can't make the lights blink for the other nics so I'm using the line state that's reported (yank a cable and it says the line state is "off").

Thanks Whiffle.

---

