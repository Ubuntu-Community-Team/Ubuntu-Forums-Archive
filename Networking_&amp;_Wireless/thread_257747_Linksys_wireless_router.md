---
title: "Linksys wireless router"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by Big_J on 2006-09-14
I just got a Linksys wireless router, and tried to use it but I couldn't get connected... I didn't try the wireless, I simply connected the modem to it and connected my box to the first port, and rebooted, I thought it would work but I cannot get it to work.. How do I get it to work. 

Note that through my years of using computers, this is my very first wireless router, so give me details!

Model Number: WRT54GS

Please help, I really need to use it.. I also ordered a laptop (which hasn't arrived yet) and it has an Intel PRO/Wireless card, would I have trouble using that?

---

### Post by linuxusr50 on 2006-09-15
Assuming you went through the normal checks, cabling, indicators, etc; try the following.


```
ifconfig
```
> The ifconfig command will tell you if you are pulling an IP address from your router.  It should be in the range of 19.168.1.x where x is usually 100 or higher.

If you are not getting an address try:
```
sudo dhclient
```
from a terminal window.  This should cause your adapter to refresh its address from the router.

If it still does not work, please post the resusts of the following.

```
sudo ifconfig
```

```
less /etc/network/interfaces
```

```
sudo dhclient
```

Dan

---

### Post by Big_J on 2006-09-15
Nothing, I cannot connect. 

```
bigj@Condor3:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:24:B5:7D  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe24:b57d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1766 (1.7 KiB)  TX bytes:8779 (8.5 KiB)
          Interrupt:185 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

bigj@Condor3:~$ 
```


less /etc/network/interfaces gives me this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

/etc/network/interfaces (END) 

```

---

### Post by freiubtheit on 2006-09-15
Your wireless card is working with 192.168.1.100.

Type the following:

sudo route add default gw 192.168.1.1
sudo route add -host 193.168.1.1 eth1

edit /etc/resolve.conf and add the following line:

nameserver NameserverIPofYourISP


I hope the above helps

---

### Post by tturrisi on 2006-09-15
When first connecting a mode to a router you must do this sequence:
1. power OFF the modem
2. power OFF the router
3. power ON the modem
4. power ON the router

This is because the modem logs the mac address of the device it connects to.  So if connected to a nic then the nic's mac address is logged in the modem.  To clear out the stored nic mac address and use a router, the sequence above must be performed so that the modem will now log the mac address of the router. (the router imitates a nic.

---

### Post by Big_J on 2006-09-15
> **tturrisi said:**
> When first connecting a mode to a router you must do this sequence:
1. power OFF the modem
2. power OFF the router
3. power ON the modem
4. power ON the router

This is because the modem logs the mac address of the device it connects to.  So if connected to a nic then the nic's mac address is logged in the modem.  To clear out the stored nic mac address and use a router, the sequence above must be performed so that the modem will now log the mac address of the router. (the router imitates a nic.

Yes, that did it. I guess that info is on the installation guide, which is a windows cd :)
thank you

Again, this is my first wireless router (or even a wired one). 
I should get my laptop in about three or four days, and like I said above it has an Intel PRO wireless card (internal, which I paid an extra $45 for), will that work fine with ubuntu? 
And just incase there are some special procedures I need to do to connect, post them now..

---

### Post by linuxusr50 on 2006-09-15
Big_J:

You will want to make sure you can connect through a wired connection before you tackle wireless.  The proceedures for wireless are not complex.

First off just try inserting wireless card and booting and see if it will connect.  I would not set any WEP, MAC Filtering, or other security at first.  If you can connect, you will then proceed to the wireless security measures. If you cannot you can google and post here for assistance.

Are you connecting wired yet, or still having problems?

Dan

---

### Post by Big_J on 2006-09-16
Yes, I got the wired figured out, I set up wep but I will take it off when connecting the wireless laptop. The laptop is supposed to arrive on tuesday...

---

### Post by Big_J on 2006-09-19
Ok, I just got the laptop, tried to connect with windows and it automatically connected. Installed ubuntu and I'm having trouble connecting!

It detected network just fine, it can see the network name but I cannot go online...

I need to know how to connect, so I can do it in college without trouble. Keep in mind that this is the first time I set up a network. I've been using dialup for years, and just got highspeed less than three months ago!


/Edit

I forgot to dissable the security... Now it works, and I renabled the security and it still works. So all is good now; I'll post back if I have any problems
Thank you all

---

### Post by Big_J on 2006-09-19
Well, here I go again...
I cannot keep the connection for more than 10 minutes, even though I'm sitting right next to the router (I'm installing everything I will need) And getting the connection back after I lose it is a major pain. I have to deactivate and reactivate the connection.

What should I do?

---

### Post by Big_J on 2006-09-19
Somebody please help, I have no idea what's going on right now. I lost power for less than a second (but my laptop was on the battery so it continued running) and now I cannot connect at all. I've been trying to connect for about an hour now!!
I can't even get it to wire connect, I plug it in and I can go to the router settings but I cannot connect to anything.. I can't view sites, cant update can't do anything.. No connection at all!

The problem is that I don't even get an error page, firefox just loads for a couple of minutes then stops loading with a blank white page!

---

### Post by tturrisi on 2006-09-19
Lost power for a second...power outage or surge?
If so, repeat the above steps I posted.
A power loss or power off-on will power off the modem & router & sometimes the router won't grab the ip address from the modem until cycling the modem & router again.

tip:  to prevent the above get a decent battery backup unit: UPS w/ AVR (automatic voltage regulating) & plugin the modem & router.

---

### Post by Big_J on 2006-09-20
outage, there was a storm...

I got it at home now, but now I'm trying to connect at the college and I can't. I'm using windows right now and it connects automatically, but when I try to connect to the same network in ubuntu it just doesn't let me... There's no security on it, it's open and I can't figure out how to connect at all!
Any ideas?

---

### Post by Big_J on 2006-09-20
Edit//
I got it figured out now!
It apparently was connecting to another network, and I was trying to connect to the right on while it's connecting the other one.. I just had to diconnect the other one and connect to the right one and viola...

one :)

Thanks all


Incase anyone is wondering what I meant by that:
I'm using the program wireless radar, and had the connections in wrong priority. When I put it in the right priority everything became fine, and it automatically connects now.

---

