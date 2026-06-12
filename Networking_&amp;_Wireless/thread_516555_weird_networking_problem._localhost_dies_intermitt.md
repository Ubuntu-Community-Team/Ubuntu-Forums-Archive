---
title: "weird networking problem. localhost dies intermittently"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by jay019 on 2007-08-03
Hi all,

Weird problem I am having... I have a wireless conection which works fine, but I cant seem to access localhost while I am connected to it. Also, if I switch off wireless and turn on wired connection it will work fine for some time then, without warning it will hang for a minute or two then resume as normal. 

Connecting to the router config page can also hang at times, yet the VNC to my windows box works flawlessly (albeit slow, but it is windows lol. couldnt believe how fast it was in the other direction)

Can anyone point me in the right direction to working out the problem and getting things back on track.

It was working fine till i tried wicd 1.3.3 but I have uninstalled (and deleted) that version and put version 1.3.1 back on. Suh a shame as 1.3.3 let me use both wireless and wired but the gui wouldn't work, but thats another issue for another day.

Jay019

---

### Post by noob12 on 2007-08-03
Can you post the results of

 ```

cat /etc/network/interfaces

cat /etc/nsswitch.conf

grep localhost /etc/hosts

``` 

and, during a period while you say that "localhost" disappears can you run
```
ifconfig -a
```
and post the result?

---

### Post by jay019 on 2007-08-03
OK. I'm on wireless / vnc at the moment...

cat /etc/network/interfaces...
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.30
netmask 255.255.255.0
gateway 192.168.0.30

iface ppp0 inet ppp
provider ppp0

```

(Yay, my first attempt at pasting over vnc. lol )

cat /etc/nsswitch.conf
```

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

grep /etc/hosts
```

127.0.0.1 localhost

```

ifconfig -a (while localhost on walkabout)
```

eth0      Link encap:Ethernet  HWaddr 00:A0:D1:51:8F:A7  
          inet6 addr: fe80::2a0:d1ff:fe51:8fa7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:6580 (6.4 KiB)
          Interrupt:233 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:28:06:96  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe28:696/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483146 errors:2 dropped:19995 overruns:0 frame:0
          TX packets:270932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:228708795 (218.1 MiB)  TX bytes:17934323 (17.1 MiB)
          Interrupt:177 Base address:0x4000 Memory:d0100000-d0100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11026 (10.7 KiB)  TX bytes:11026 (10.7 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

hmm, first time ive noticed that sit0, what is that for?

---

### Post by noob12 on 2007-08-03
What do you mean that localhost is on walkabout?

What happens in this condition if you run **ping 127.0.0.1**?  What about **ping localhost**?

---

### Post by jay019 on 2007-08-03
Walkabout - missing in action. Bad aussie slang.

ping wokrs fine, seems it is probably an issue with apache as I tried loading a page from localhost and it hung for a while but the ping was working fine.

I had a look at the apache logs (System->Administration->System Log) and the only error reported for apache was a missing favicon. But that shouldn't slow it down significantly should it?

Doh! Just as I got samba to work too.

---

### Post by noob12 on 2007-08-03
Yeah, I've seen Crocodile Dundee :-)  I just didn't know what you meant technically.

So localhost is back in town.  What are the actual symptoms?

I'm not sure I understand your situation.  You're connecting to a web server, the browser is running on the same box but you are doing this all over VNC?   Is that right?  

If this is the case I'd suspect that what's really going on is slowness of VNC over that link.  You could probably confirm this by setting the color resolution really low for the VNC connection and seeing if that magically speeds things up a lot.

---

### Post by jay019 on 2007-08-03
OK...
Its all on my laptop. I have the webserver on my laptop and while connected to the wireless router localhost goes down every now and then.

I am only using vnc as a way to connect to the internet. Weird, but it works. My desktop machine is running windows and windows ICS sucks and I only have dial up, so the only way to get online is via a vnc session. But that works fine, its the webserver on my laptop that has the issues.

---

### Post by noob12 on 2007-08-03
But localhost down means you can still ping localhost but browsing to [http://localhost](http://localhost) is very slow?

Can you try doing

```

cd /tmp
wget -v http://localhost

```

If you lack wget you would need to **aptitude install wget**

---

### Post by jay019 on 2007-08-03
Wget downloadsat 133+ MB/s

But, I think I may have found the problem...

Seems firefox was set to auto-detect proxy settings, which is silly as I have no proxies.  :oops:
However I do remember trying to use a proxy a few weeks ago before I settled for vnc to conect to the net.

Wont know if that has fixed it till tommorow (its nearly 2am here) but chances are it was something as silly as that setting.  lol.
](*,)<-:roll:

---

### Post by noob12 on 2007-08-03
Yes.  Testing with wget separates browser issues out.  Great.

---

### Post by imdano on 2007-08-03
> **jay019 said:**
> It was working fine till i tried wicd 1.3.3 but I have uninstalled (and deleted) that version and put version 1.3.1 back on. Suh a shame as 1.3.3 let me use both wireless and wired but the gui wouldn't work, but thats another issue for another day.

Jay019Now that your other problem seems to be solved, do you want to elaborate on this at all?

---

