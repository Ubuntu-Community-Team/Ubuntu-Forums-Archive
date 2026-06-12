---
title: "can ping, can't surf"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by mjs_sporko on 2006-11-30
Hi,

I can ping my router but I can't open any web pages. Any ideas?

If I `ftp google.com` (strange I know), it can't connect but does return a valid IP address for google.

Some solutions to similar problems I've found don't work.
Solutions were to:
  - Black list IPv6.
  - Manually enter DNS into router.
  - Add "nameserver 192.168.1.1" to /etc/resolv.conf
  - Restarting after changing something.

Thanks for any help. :)

Cheers,
Martin.

---

### Post by apjone on 2006-11-30
I made my desktop static and inputted my own DNS Servers into resolv.conf. try adding the dns's listed on the router config to your resolv.conf:

nameserver xxx.xxx.xxx.xxx
nameserver yyy.yyy.yyy.yyy

then restart your networking

---

### Post by mjs_sporko on 2006-11-30
Thanks for the reply.

I've tried this, and thats how its setup at the moment.
Static IP with my ISPs DNS servers in /etc/reslov.conf.

Any more thoughts?
Thanks again.

---

### Post by apjone on 2006-11-30
does your web browser give you an error or just wont load a web page?

---

### Post by mjs_sporko on 2006-11-30
Firefox returns this...

> Server not found

Firefox can't find the server at [www.google.com](www.google.com).

    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

* This was generate in Windows, but its exactly what I get under Linux.

---

### Post by apjone on 2006-11-30
does IE work under windows?

---

### Post by mjs_sporko on 2006-11-30
Yeah sorry, everything works under Windows.
I just used that to get the error message the Linux+Firefox gives.

Sorry for the confusion.

---

### Post by apjone on 2006-11-30
can you list your /etc/resolv.conf and /etc/network/interfaces for me to look at please.

---

### Post by mjs_sporko on 2006-11-30
`cat /etc/resolv.conf`
```
nameserver 192.168.1.254
nameserver 198.142.0.51
nameserver 192.168.1.1
```

`cat /etc/network/interfaces`
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid GIGABYTE


iface rausb0 inet static
address 198.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254
wireless-essid GIGABYTE

auto rausb0
```

Does it have something to do with having both wlan0 and rausb0?
The default drivers use 'wlan0', but I need to unload these and load other ones when I start up, these new ones use 'rausb0'.

Thanks.

---

### Post by apjone on 2006-11-30
whats the IP of your router?

the gateway should be the same IP as your router

---

### Post by mjs_sporko on 2006-11-30
192.168.1.254

---

### Post by apjone on 2006-11-30
does your wired ethernet work under linux. this is a strange one

---

### Post by mjs_sporko on 2006-11-30
No way to test sorry. Our modem is in the other end of the house, being used by people. Can't move my computer there or it here.

However, at college I had the wired connection working, that was under Kubuntu 6.06, when I moved back i switched to Ubuntu 6.10, never tested 6.06 sorry.

Would the fact that I have wlan0 statements in /etc/network/interfaces affect things since I unload the module that (I think) uses it?

---

### Post by apjone on 2006-11-30
not sure, i havent really done wireless, Could be that the wireless-essid is incorrect.

---

### Post by mjs_sporko on 2006-11-30
I used the same one from Windows, I don't think wireless is the issue because I was able to get the IP address of google. Meaning that packets were sent and received outside of my house.

Is there any other info I could give you that might help?

---

### Post by apjone on 2006-11-30
which device is the phone line connected into?

---

### Post by mjs_sporko on 2006-11-30
I'm not sure how ADSL, Routers, etc. work so this might not be the answer your looking for. (Plus I didn't set any of it up)

The phone line is connected to the (ADSL) modem, which is connected to the router. This is connected by wire to 2 computers and wirelessly to 2 others.

---

### Post by apjone on 2006-11-30
set the gateway as the (ADSL) modem and restart the networking

---

### Post by mjs_sporko on 2006-11-30
How do I determine its address, sorry?

---

### Post by apjone on 2006-11-30
tracepath google.com

it will be the last 192.x.x.x address in the list

---

### Post by mjs_sporko on 2006-11-30
`tracepath google.com` 
```
1: send failed
 Resume: pmtu 65535
```

I can still ping the router and `ftp google.com` gets me google's IP but a `tracepath` on that gave the above message.

---

### Post by stream303 on 2006-12-01
> **mjs_sporko said:**
> `cat /etc/resolv.conf`
```
nameserver 192.168.1.254
nameserver 198.142.0.51
nameserver 192.168.1.1
```


Oops.  The first two nameservers should be the primary and backup dns server addresses of your *isp,* not these private .254 and .51 addresses.  If your windows box doesn't show what the isp dns servers are, you might want to call them or search your providers help pages.

The last one is most likely that of your router's internal dns server.  Ok as long as you leave it as the last one.

Here's a quickie howto that goes into it in a little more detail - don't worry, you're almost there.

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

### Post by mjs_sporko on 2006-12-01
Thanks for the reply.

It must be getting close. Firefox now takes a long time to respond with that same message and `ping google.com` shows after a long delay "ping: unknown host google.com"

I got the DNS servers from an unoffical page (couldn't find any offical details), is there a way to verify their correctness?

Thanks for any help. :)

---

### Post by mjs_sporko on 2006-12-01
I don't think that HowTo is relavent because I am using a static IP. Is that right?

---

### Post by mjs_sporko on 2006-12-01
It must be almost there, right?

If I `ping google.com` I get a delay before saying "ping: unknown host google.com", a similar delay occurs in Firefox when trying to access a site. 
If I `ping my_isps_dns_servers` I instantly get "connect: Network is unreachable", does this help with the diagnosis/solution?

I have verified that the DNS server addresses are correct.

Thanks again for any help.

---

### Post by trubblemaker on 2006-12-01
can you install anything with apt-get?  or do "sudo apt-get update"?   does it fail of succeed?

or try

```
wget www.google.com
```

do they fail?

---

### Post by dbott67 on 2006-12-01
> **mjs_sporko said:**
> If I `ping my_isps_dns_servers` I instantly get "connect: Network is unreachable", does this help with the diagnosis/solution?

Please post the output of
```
route -n
```
and
```
ifconfig -a
```

-Dave

---

### Post by mjs_sporko on 2006-12-02
`route -n`
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0
```

`ifconfig -a`
```
eth0      Link encap:Ethernet  HWaddr 00:0C:76:40:D2:47  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5316 (5.1 KiB)  TX bytes:5316 (5.1 KiB)

rausb0    Link encap:Ethernet  HWaddr 00:08:A1:A0:C7:60  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fea0:c760/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2750 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:192389 (187.8 KiB)  TX bytes:12794 (12.4 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

`sudo apt-get update`
```
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Err http://security.ubuntu.com edgy-security Release.gpg                       
  Temporary failure resolving 'security.ubuntu.com'
Err http://au.archive.ubuntu.com edgy Release.gpg                            
  Temporary failure resolving 'au.archive.ubuntu.com'
Err http://security.ubuntu.com edgy-security/main Translation-en_US          
  Temporary failure resolving 'security.ubuntu.com'
Err http://au.archive.ubuntu.com edgy/main Translation-en_US                 
  Temporary failure resolving 'au.archive.ubuntu.com'
Err http://au.archive.ubuntu.com edgy/restricted Translation-en_US           
  Temporary failure resolving 'au.archive.ubuntu.com'
Err http://security.ubuntu.com edgy-security/restricted Translation-en_US    
  Temporary failure resolving 'security.ubuntu.com'
Err http://au.archive.ubuntu.com edgy-updates Release.gpg
  Temporary failure resolving 'au.archive.ubuntu.com'
Err http://au.archive.ubuntu.com edgy-updates/main Translation-en_US
  Temporary failure resolving 'au.archive.ubuntu.com'
Err http://au.archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2  Temporary failure resolving 'au.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

`wget www.google.com`
```
wget www.google.com
--17:24:45--  http://www.google.com/
           => `index.html'
Resolving www.google.com... failed: Temporary failure in name resolution.
```

---

### Post by dbott67 on 2006-12-02
According to your routing table, your computer only knows how to send packets to the 192.168.1.xxx network.  You're missing the default route off of your network.

You're routing table should look like this:
```
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0
[COLOR="Red"]0.0.0.0         192.168.1.254     0.0.0.0         UG    0      0        0 rausb0[/COLOR]

```

**_2 things to try:_**

**1. Disable & re-enable your ethernet adapter:**
```
sudo ifdown rausb0
```
```
sudo ifup rausb0
```


Then, print out the routing table again (route -n) and check to see if it looks like my example.  Try pinging google.com and an external IP address.

If it doesn't work, try method #2.

**2. Add the route manually:**
```
sudo route add -net default gw 192.168.1.254 dev rausb0
``` 
where 192.168.1.254 is the IP address of your router.

-Dave

---

### Post by dbott67 on 2006-12-02
I also noticed that you're using static IP addresses.

A couple of things to verify:

1. Be sure of the internal IP address of your router (you posted that it was 192.168.1.254).  Try logging into it using Firefox.  This is very important as it's the required IP address that I had you enter above:
```
sudo route add -net default gw 192.168.1.254 dev rausb0
```

2. Once you're sure what it is, edit you /etc/resolv.conf file to look like the following:
```
gksudo gedit /etc/resolv.conf
```
```
nameserver 192.168.1.254
# nameserver 198.142.0.51
# nameserver 192.168.1.1
```

The # just 'comments out' the line and the computer ignores them.  I'm assuming that you put 198.142.0.51 in there for your ISP.  The 192.168.1.1 entry that you added would be used if your router's IP was 192.168.1.1 (which is a very common IP for D-Link routers).

-Dave

---

### Post by mjs_sporko on 2006-12-02
Thanks so much apjone, stream303, trubblemaker and dbott67. It all seems to be working well! :D

The google logo has never looked so lovely. ;)

---

### Post by dbott67 on 2006-12-02
That's great! Can you post what fixed the trouble, as it may help serve others that find this thread?

Also, maybe you can post your current settings for the following:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
cat /etc/resolv.conf
```
```
route -n
```

Thanks,
Dave

---

