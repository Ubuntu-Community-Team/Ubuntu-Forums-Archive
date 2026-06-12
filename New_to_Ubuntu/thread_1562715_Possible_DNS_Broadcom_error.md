---
title: "Possible DNS Broadcom error"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by thomasdsc on 2010-08-28
Hello all. 
I installed the Broadcom driver on my dell, it worked nice, it could detect my wireless network and it showed it was connected to my wireless network.
But as soon as I browse, I cannot load any pages. I searched on the forums and got many different complicated solutions. However, they dont seem to be applicable for me cause I am not using wireless connection through a wireless router.
My configuration is:
Modem--> Router (not wireless) --> Aztech Wireless N Adapter (its compatible with g and other signals too). 
And the 192.168.1.1 doesn't work on my ubuntu.
I uses the TL-R402M router by the way.
Any help for me to get back on internet is appreciated.

---

### Post by thomasdsc on 2010-08-29
A little help... please?

---

### Post by MattBD on 2010-08-29
Hmm, that's a bit odd - you should be able to connect to your router at least (I presume 192.168.1.1 is the normal IP address you use to access your router's web interface). It doesn't sound like a DNS error if the IP address won't resolve.

Have you tried pinging the router's IP address from the terminal? Something like:
```
ping 192.168.1.1
```
And maybe pinging a few external sites:
```
ping www.google.com
```
That way you should be able to establish whether you have a network connection and whether domain names are being successfully resolved to external IP addresses.

---

### Post by thomasdsc on 2010-08-29
Oi, its just keeps going on like a mummified penguin when I ping my router! And I cannot ping google or other sites. unknown host.
```
me@me-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.32 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=2.80 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=36.8 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=2.37 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=2.63 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=3.77 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=2.33 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.845 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=2.31 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=2.83 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=4.04 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=1.25 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.849 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=2.63 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=2.32 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=5.41 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=1.59 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=5.95 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=2.67 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=4.66 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=1.34 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=2.47 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=1.16 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=2.32 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=2.52 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=3.29 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=2.31 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=0.918 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=4.39 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=2.48 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=1.74 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=2.48 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=1.18 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=2.37 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=1.07 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=64 time=2.73 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=64 time=2.57 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=64 time=0.910 ms
64 bytes from 192.168.1.1: icmp_seq=39 ttl=64 time=4.62 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=64 time=1.63 ms
64 bytes from 192.168.1.1: icmp_seq=41 ttl=64 time=2.41 ms
64 bytes from 192.168.1.1: icmp_seq=42 ttl=64 time=2.29 ms
64 bytes from 192.168.1.1: icmp_seq=43 ttl=64 time=0.932 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=64 time=1.04 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=64 time=3.41 ms
64 bytes from 192.168.1.1: icmp_seq=46 ttl=64 time=2.54 ms
64 bytes from 192.168.1.1: icmp_seq=47 ttl=64 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=48 ttl=64 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=49 ttl=64 time=3.39 ms
64 bytes from 192.168.1.1: icmp_seq=50 ttl=64 time=2.79 ms
64 bytes from 192.168.1.1: icmp_seq=51 ttl=64 time=54.2 ms
64 bytes from 192.168.1.1: icmp_seq=52 ttl=64 time=2.27 ms
64 bytes from 192.168.1.1: icmp_seq=53 ttl=64 time=2.30 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=64 time=2.40 ms
64 bytes from 192.168.1.1: icmp_seq=55 ttl=64 time=2.43 ms
64 bytes from 192.168.1.1: icmp_seq=56 ttl=64 time=2.40 ms
64 bytes from 192.168.1.1: icmp_seq=57 ttl=64 time=2.33 ms
64 bytes from 192.168.1.1: icmp_seq=58 ttl=64 time=1.32 ms
64 bytes from 192.168.1.1: icmp_seq=59 ttl=64 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=60 ttl=64 time=2.44 ms
64 bytes from 192.168.1.1: icmp_seq=61 ttl=64 time=3.30 ms
64 bytes from 192.168.1.1: icmp_seq=62 ttl=64 time=2.70 ms
64 bytes from 192.168.1.1: icmp_seq=63 ttl=64 time=1.62 ms
64 bytes from 192.168.1.1: icmp_seq=64 ttl=64 time=2.62 ms
64 bytes from 192.168.1.1: icmp_seq=65 ttl=64 time=3.56 ms
64 bytes from 192.168.1.1: icmp_seq=66 ttl=64 time=2.33 ms
64 bytes from 192.168.1.1: icmp_seq=67 ttl=64 time=1.80 ms
64 bytes from 192.168.1.1: icmp_seq=68 ttl=64 time=2.41 ms
64 bytes from 192.168.1.1: icmp_seq=69 ttl=64 time=2.27 ms
64 bytes from 192.168.1.1: icmp_seq=70 ttl=64 time=2.63 ms
64 bytes from 192.168.1.1: icmp_seq=71 ttl=64 time=3.28 ms
64 bytes from 192.168.1.1: icmp_seq=72 ttl=64 time=3.75 ms
64 bytes from 192.168.1.1: icmp_seq=73 ttl=64 time=6.41 ms
64 bytes from 192.168.1.1: icmp_seq=74 ttl=64 time=2.29 ms
64 bytes from 192.168.1.1: icmp_seq=75 ttl=64 time=2.60 ms
64 bytes from 192.168.1.1: icmp_seq=76 ttl=64 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=77 ttl=64 time=2.49 ms
64 bytes from 192.168.1.1: icmp_seq=78 ttl=64 time=2.27 ms
64 bytes from 192.168.1.1: icmp_seq=79 ttl=64 time=2.54 ms
64 bytes from 192.168.1.1: icmp_seq=80 ttl=64 time=3.45 ms
64 bytes from 192.168.1.1: icmp_seq=81 ttl=64 time=2.56 ms
64 bytes from 192.168.1.1: icmp_seq=82 ttl=64 time=3.10 ms
64 bytes from 192.168.1.1: icmp_seq=83 ttl=64 time=2.34 ms
64 bytes from 192.168.1.1: icmp_seq=84 ttl=64 time=2.48 ms
64 bytes from 192.168.1.1: icmp_seq=85 ttl=64 time=3.29 ms
64 bytes from 192.168.1.1: icmp_seq=86 ttl=64 time=1.14 ms
64 bytes from 192.168.1.1: icmp_seq=87 ttl=64 time=2.50 ms

```

---

### Post by skatinjj on 2010-08-29
> **thomasdsc said:**
> Hello all. 
I installed the Broadcom driver on my dell, it worked nice, it could detect my wireless network and it showed it was connected to my wireless network.
But as soon as I browse, I cannot load any pages. I searched on the forums and got many different complicated solutions. However, they dont seem to be applicable for me cause I am not using wireless connection through a wireless router.
My configuration is:
Modem--> Router (not wireless) --> Aztech Wireless N Adapter (its compatible with g and other signals too). 
And the 192.168.1.1 doesn't work on my ubuntu.
I uses the TL-R402M router by the way.
Any help for me to get back on internet is appreciated.

Could you post the contents of this file:

/etc/network/interfaces

And also open a terminal and post the output of this:

```
ifconfig -s
```

---

### Post by thomasdsc on 2010-08-29
This is the ifconfig -s :
   [FONT=&quot]me@me-laptop:~$ ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
eth1       1500 0         4      0      0 0            32      6      0      0 BMRU
lo        16436 0         4      0      0 0             4      0      0      0 LRU
[/FONT]
  This is my interfaces file:
   [FONT=&quot]auto lo
iface lo inet loopback
[/FONT]

---

### Post by skatinjj on 2010-08-29
> **thomasdsc said:**
> This is the ifconfig -s :
   [FONT=&quot]me@me-laptop:~$ ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
eth1       1500 0         4      0      0 0            32      6      0      0 BMRU
lo        16436 0         4      0      0 0             4      0      0      0 LRU
[/FONT]
  This is my interfaces file:
   [FONT=&quot]auto lo
iface lo inet loopback
[/FONT]

Your interfaces file is interesting as it does not list eth0 or eth1 as listed by the ifconfig -s cmd.

For a single ethernet connection it should look like:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Then again I do not use network manager but i would make a backup copy and try what i posted.

---

### Post by spillage2 on 2010-08-29
you have the same interfaces file as me so dont think that is you problem. have you pinged [www.google.com?](www.google.com?)

---

### Post by cariboo on 2010-08-29
Could you post the output of:

```
cat /etc/resolv.conf
```

note the spelling.

---

### Post by thomasdsc on 2010-08-29
I got 
* Generated by Network Manager
domain domain
search domain
nameserver 218.102.60.110
nameserver 218.102.32.208
I pinged external sites, and I got unknown host.

---

### Post by thomasdsc on 2010-08-30
This is getting really weird.
I left my computer idle, when I came back, I was able to use internet for some reason. Then when I restarted, I couldnt get back on any more!
Therefore I did the ifconfig thing and see if you can come up with something:(this is when I get the internet for some reason)
   [FONT=&quot]eth0      Link encap:Ethernet  HWaddr 00:24:e8:ad:dd:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:76:5f:55  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:56ff:fe76:5f55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:592538 errors:0 dropped:0 overruns:0 frame:596361
          TX packets:455036 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:868807275 (868.8 MB)  TX bytes:38809548 (38.8 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


 [/FONT]

---

### Post by migs73 on 2010-08-30
> **thomasdsc said:**
> 
My configuration is:
Modem--> Router (not wireless) --> Aztech Wireless N Adapter (its compatible with g and other signals too). 


If your router is not wireless, how are you connecting to it using a USB wireless adapter?:confused:

Is it possible you connected to the internet using an available unsecured Wifi network in the area?

---

### Post by thomasdsc on 2010-08-30
I didnt use any usb adapters. 
The wireless N should be extender, not adapter, my bad.
It creates a wireless network in addition to the router's wired network system.

---

### Post by migs73 on 2010-08-30
Does your wireless extender have its own DHCP?

I recently set one up in Client mode (the other way round to your application) and had major problems. Changing the Access point (extender) to have a dynamic IP from my routers DHCP, meant I could not connect through it. A google search stated I should have the AP's LAN on a different subnet from the WAN, but his was impossible on the AP I had, as it assigned its LAN side DHCP using addresses from it own IP subnet, meaning I had two DHCP servers assigning the same numbers on the same network. Anyway, to cut a very long story short, I gave up on DHCP and made both the AP and the device on the LAN (A Sony TV by the way) have static IP's. This then worked fine.

In other words, does your router or the extender do the DHCP? If it is both there could be IP clashes.

---

### Post by thomasdsc on 2010-08-30
> **migs73 said:**
> Does your wireless extender have its own DHCP?

I recently set one up in Client mode (the other way round to your application) and had major problems. Changing the Access point (extender) to have a dynamic IP from my routers DHCP, meant I could not connect through it. A google search stated I should have the AP's LAN on a different subnet from the WAN, but his was impossible on the AP I had, as it assigned its LAN side DHCP using addresses from it own IP subnet, meaning I had two DHCP servers assigning the same numbers on the same network. Anyway, to cut a very long story short, I gave up on DHCP and made both the AP and the device on the LAN (A Sony TV by the way) have static IP's. This then worked fine.

In other words, does your router or the extender do the DHCP? If it is both there could be IP clashes.

Other computers in my house can connect to that Extender wirelessly, other than the linux.
But if static ip is a fix, how do I configure it when I cannot check my ip? Nevertheless, I have another computer that is connected to the extender in windows and is capable of reaching 192.168.1.1 . 
I already read the guides as of how to edit the /etc/networking/conf thing, but I dont know what to put in!
As there another user friendly way?

---

### Post by migs73 on 2010-08-31
Whatever system sets the IP addresses (the DHCP server) will have settings in it for the range of addresses it can allocate. Log in to it and set this to 192.168.1.0 to 192.168.1.100 (if it currently starts t 1.1 or higher just leave it at that) that gives you about 100 addreses to allocate dynamically. 
Now on your laptop, Right click on the network icon on the top panel and select edit connections (NB make sure the connection is disabled first before editing this or it won't do it). Select the one for your wireless, click on the IPv4 tab, from the drop dowmn menu that says Automatic DHCP change it to manual.
on the table underneath, click add, and then put in an IP address above 100 say 101, so 192.168.1.101, the subnet mask you can get from the the DHCP server but is probably 255.255.255.0. Next is the gateway, now I am not so sure about this as every value I put in was replaced by 0.0.0.0 so give it a go with that. Now apply it and re-eneable your wireless. Give a minute or so to get itself sorted out. Now at the very least I would expect you to now be able to connect to the WAN/LAN. If you have problem connecting to the internet, try editing the connection settings again, but putting in the DNS addresses (should be able to get them from your router/modem/extender).
If your still having problems , I am afraid I'm out of suggestions, that is what worked for me. Good Luck.




EDIT; Just out of interest did you try connecting to your router with a cable to see if it works that way?

---

