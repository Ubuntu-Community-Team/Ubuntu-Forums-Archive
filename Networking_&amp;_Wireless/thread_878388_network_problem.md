---
title: "network problem"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by geraldvillorente on 2008-08-02
heya masters ang gurus here. i installed ubuntu 8.04 on my machine and it works well except of my network interface(on-board LAN). 

Hardware info's:

Motherboard: ASUS P5S02-VM (SATA)
Processor: INTEL CORE 2 DUO

tia and more power,

Gerald Villorente
Aklan State University, Philippines

---

### Post by pytheas22 on 2008-08-02
Please post the output of:
```

lspci
lshw -C Network
```

---

### Post by K2712 on 2008-08-02
Check the wired ethernet troubleshooting thread:

[http://ubuntuforums.org/showthread.php?t=87644](http://ubuntuforums.org/showthread.php?t=87644)

If that doesn't help, come back here and post the output of the following:

```
ifconfig -a
```

---

### Post by geraldvillorente on 2008-08-02
thanks i will try it now

---

### Post by geraldvillorente on 2008-08-02
> **pytheas22 said:**
> Please post the output of:
```

lspci
lshw -C Network
```

i tried this and i saw ethernet controller on the lists.

---

### Post by geraldvillorente on 2008-08-02
> **K2712 said:**
> Check the wired ethernet troubleshooting thread:

[http://ubuntuforums.org/showthread.php?t=87644](http://ubuntuforums.org/showthread.php?t=87644)

If that doesn't help, come back here and post the output of the following:

```
ifconfig -a
```

i tried this also and eth0 is available but there's an error on RX/TX and the base address: 0xdead

---

### Post by K2712 on 2008-08-02
Do you have a router, or firewall?  If you are getting RX/TX errors you're dropping packets somewhere.

---

### Post by geraldvillorente on 2008-08-02
here are the snapshots:

---

### Post by geraldvillorente on 2008-08-02
> **K2712 said:**
> Do you have a router, or firewall?  If you are getting RX/TX errors you're dropping packets somewhere.

Yeah i have a router. But my machine is dual boot. When i boot it on Windows my network is working well.

---

### Post by K2712 on 2008-08-02
Try removing the last two lines of your /etc/network/interfaces file and then restart the network.

---

### Post by pytheas22 on 2008-08-02
Yes, try what the poster above says (you can restart the networking with the command "sudo /etc/init.d/networking restart").  If that doesn't help, what happens when you run:
```

sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

And you're sure you're using dhcp, right, not static IPs?  If you use static IPs then you must have manually set the IP on Windows at one time; if you never did that, then you must be using dhcp.

---

### Post by geraldvillorente on 2008-08-02
thanks masters...you are great!

---

### Post by geraldvillorente on 2008-08-02
> **K2712 said:**
> Try removing the last two lines of your /etc/network/interfaces file and then restart the network.

here was the result after i removed the last two lines...

---

### Post by geraldvillorente on 2008-08-02
> **pytheas22 said:**
> Yes, try what the poster above says (you can restart the networking with the command "sudo /etc/init.d/networking restart").  If that doesn't help, what happens when you run:
```

sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up
sudo dhclient eth0
```

And you're sure you're using dhcp, right, not static IPs?  If you use static IPs then you must have manually set the IP on Windows at one time; if you never did that, then you must be using dhcp.

here are the results sir....

---

### Post by K2712 on 2008-08-02
In those last two shots you had:

```
sudo ifconfig eth**o** down
sudo ifconfig eth**o** up
```

Should have been:

```
sudo ifconfig eth**0** down
sudo ifconfig eth**0** up
```

A lot of times it's easier to copy/paste when there are a lot of commands to enter... :)

---

### Post by pytheas22 on 2008-08-03
Yes, there were some typos (dhclient was written once as dhcpclient, I think)...although I realize that copying and pasting is hard because you don't have any Internet on this computer, so you can't be reading these forums there.  You could always save the commands in a text file and transfer them to your Ubuntu machine using a USB disk, though.

Anyway, dhclient didn't get you an IP address, which is strange.  Does this help:
```

sudo rmmod sis190
sudo modprobe sis190
sudo ifconfig eth0 up
sudo dhclient eth0
sudo dhclient3 eth0
```

I'll also do some searches and see if maybe there's a bug with your driver.  Everything looks like it *should* be working, so I'm not sure why you're unable to get an IP address and connect.

I probably won't be back till tomorrow though.

---

### Post by pytheas22 on 2008-08-03
aha, I think I found the problem (see post six [here]("http://ubuntuforums.org/showthread.php?t=589034")--deals with the same model of ethernet card as you).  Run these commands and you should get an IP address and be able to get online:
```

sudo ifconfig eth0 mtu 1492
sudo dhclient eth0
```

If that works, we can make the fix permanent so you won't have to type those commands every time you need to get online, or think about this problem ever again.

---

### Post by geraldvillorente on 2008-08-03
thank you very much masters....

---

### Post by geraldvillorente on 2008-08-03
> **pytheas22 said:**
> aha, I think I found the problem (see post six [here]("http://ubuntuforums.org/showthread.php?t=589034")--deals with the same model of ethernet card as you).  Run these commands and you should get an IP address and be able to get online:
```

sudo ifconfig eth0 mtu 1492
sudo dhclient eth0
```

If that works, we can make the fix permanent so you won't have to type those commands every time you need to get online, or think about this problem ever again.

still not working....

---

### Post by geraldvillorente on 2008-08-03
im about to give up...i cant still fix my problem...

---

### Post by pytheas22 on 2008-08-03
I don't think you should give up because this problem should be easy enough to solve; we just need to figure out what the heart of the issue is.

I found this [thread]("http://ubuntuforums.org/showthread.php?t=628164&page=2"), also dealing with the same model of ethernet card as yours, which suggests (see last post) that the issue has something to do with Windows powering down the card.  I've heard of things like this--Windows puts ethernet cards in sleep mode or something when it shuts down, and Ubuntu can't bring them up.  So that may well be what's going on.

So try this: boot to Windows and check to make sure the ethernet works there.  Then shutdown the computer completely (choose shutdown, not restart).  Let it power off completely and unplug the power cable for a few seconds (or flip off the switch on your PSU).  Then restart the computer and boot to Ubuntu.  Does the ethernet connect?  If not, it may also help to reboot your router at this point.

---

### Post by fwre01 on 2008-08-03
i looked at the TX count one of the first screenshots and noticed it was at 0. and the nic was getting the eth0:avahi meaning ur not getting an offer sent to you by the DHCP server. before you give up, do a "ping 127.0.0.1" this will check ur TCP stack in software.

it would also be interesting to see the packet debug using tcpdump -i eth0 host "dhcp.server.ip.address" to make sure the DHCP negotiation is happening properly. you should a Discover, Offer, Request, Ack in that order.

...dont give up!! ;-)

**EDIT** or you could set your IP address manually to check its not a DHCP problem, make your /etc/network/interfaces file look like this (replacing the ip addresses for the ones you want)

auto eth0
iface eth0 inet static
address 192.168.1.x
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0

---

### Post by geraldvillorente on 2008-08-03
thanks guys....cheers

---

