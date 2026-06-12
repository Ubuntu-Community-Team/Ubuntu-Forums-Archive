---
title: "No HW address + no SSH"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by aldegaz on 2008-02-17
Hi,

I have an Atheros wireless card that is showing a HW address of 00:00:00:00:00:00.

I really don't mind that specific thing about it but I think is messing my SSH connections when I try to get into other computers in my network.

Not only that, but I can't even ping computers in the same network and those computers can't ping me :(

Outbound SSH connections (that is SSH connections for servers not in my network) work fine, same as pinging outside sites.

Do you guys think this is related to the MAC address not showing or is there something wrong with the driver I am using?

I hope not, since this is a brand new Toshiba Satellite I have had for a week.

Thanks in advance!

---

### Post by psyburn on 2008-02-17
Where are you reading this MAC from?

Can you give a post of ```
ifconfig -a
```

---

### Post by aldegaz on 2008-02-18
I am reading it via ifconfig.

It clearly displays the long list of ceros in the HW address part.

---

### Post by psyburn on 2008-02-18
Is the name of this adapter that has the long list of zeros in it's MAC wmaster0 or wifi0?

Atheros cards show 2 interfaces from a "ifconfig -a"

the one to configure ALWAYS will be ath*X* (ath0, ath1, etc...)

EDIT: OOPS! I didn't answer your question!?
So It's normal for to have an ath*X* and a wmaster*X* or wifi*X*

ath*X* will have your real MAC address

wmaster*X* or wifi*X* will have your real mac with a bunch of -00-00 following

---

### Post by aldegaz on 2008-02-18
He he he

I am @ work now, so I will have to get back at you later on that one.

However, my HW problem is with "wlan0"

I am quite sure that is the only one for wireless.



Thanks for all the help!

---

### Post by psyburn on 2008-02-18
Just so you have an idea of what I'm talking about I'll post my "ifconfig -a"

Hopefully this is something close to what you get...
I'm using the standard Ubuntu madwifi drivers

Notice how the same MAC is their but wifi0 has [COLOR="Navy"]-00[/COLOR] apended to the MAC
```
ath1      Link encap:Ethernet  HWaddr [COLOR="DarkRed"]00:16:41:XX:XX:95[/COLOR]  
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:255.255.255.XXX
          inet6 addr: fe80::216:41ff:fe19:1d95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1165163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695546 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1391162272 (1.2 GB)  TX bytes:222780795 (212.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2200 (2.1 KB)  TX bytes:2200 (2.1 KB)

wifi0     Link encap:UNSPEC  HWaddr [COLOR="DarkRed"]00-16-41-XX-XX-95[/COLOR][COLOR="Navy"]-00-00-00-00-00-00-00-00-00-00[/COLOR]  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1359833 errors:0 dropped:0 overruns:0 frame:3648
          TX packets:697700 errors:8 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1462442319 (1.3 GB)  TX bytes:249347065 (237.7 MB)
          Interrupt:11
```

EDIT: You wouldn't happen to be using NDISwrapper?

---

### Post by aldegaz on 2008-02-18
Hey there.. this is what ifconfig -a looks like for me:

```

alfredo@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xe000 

eth0:avah Link encap:Ethernet  HWaddr 00:A0:xx:xx:xx:xx  
          inet addr:xxx.2x.xxx.xx5  Bcast:xxx.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.0.xxx  Bcast:192.168.0.xxx  Mask:255.255.255.0
          inet6 addr: fe80::xxxx:xx:xxxx:0/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2493906 (2.3 MB)  TX bytes:384131 (375.1 KB)
          Interrupt:18 Memory:f8200000-f8210000 

```

As you can see, the only related items are eth0 and eth0:avahi :(

What do you think?

---

### Post by psyburn on 2008-02-19
The order of interfaces "brought up" makes a difference.

Looks to me like you need to "bring down" eth0 since things might be trying to leave via eth0 instead of wlan0

FYI run this command in the console:
```
sudo ifdown -v eth0
```

If it still doesn't work then you should first try "bring down and up" wlan0
```
sudo ifdown -v wlan0 && sudo ifup -v wlan0
```

To rectify the "No MAC address" issue I'd look up what the sticker says it should be.
Then I'd run this before "bringing up" wlan0
```
sudo ifconfig wlan0 hw ether [COLOR="DarkRed"]XX:XX:XX:XX:XX:XX[/COLOR]
```
Changing the XX to what the sticker says or making up a valid one.
That or use an MAC address from an adapter you have thats dead or your not using **(especially not being used at the same time!!)**

MAC Lookup:
[http://www.coffer.com/mac_find/]("http://www.coffer.com/mac_find/")
Use this to see if your made up one is valid.

---

### Post by aldegaz on 2008-02-20
I will try these solutions tonight.

The only thing that I tried before is using macchanger:  sudo apt-get install macchanger

And then trying to perform a change in the Mac address with no results.

Thanks for all the help!

---

### Post by aldegaz on 2008-02-20
NO WAAAAAAAAAAAAAAAAY!
:guitar:

That was the solution!

```
 sudo ifdown -v eth0
```

Thank you so much for your patience and guidance. Although I am a Linux admin myself I was knocking my head to the wall!

Where is  the "thank you" button ?

Now that everything is working, could you please breakdown the solution for me?

WHy exactly is that ifdown helping me?
Am I going to have to do it every single time I boot?
What is the next step for a permanent solution?


THanks again!

---

### Post by aldegaz on 2008-02-25
:(

I can't believe this, but yesterday the problem came back again, no MAC address and couldn't get in the network with other computers.

The internet was working fine though.

I tried the "ifdown/ifup" to get rid of the eth0 but to no avail.

Any ideas?

---

