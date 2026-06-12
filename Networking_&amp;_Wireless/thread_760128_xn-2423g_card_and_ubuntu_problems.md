---
title: "xn-2423g card and ubuntu problems"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by mattgen88 on 2008-04-19
Hi guys,
First off, I'm fairly new to linux in general. I've been using red hat enterprise on my school's computers all semester and have been playing around with linux for the past year on and off.
After having very poor performance with XP on a fairly old laptop (compaq presario 700) I decided I'd go to linux for a performance boost. I use it for programming anyway and all the programs I use can be ran from there.
So, I decided to go with Ubuntu. I downloaded it on tuesday and installed it with some problems (took 3 tries, it kept locking up). But now its running fine.
However, being a laptop, using a cat 5 cable all the time is a little restrictive. So, I have 2 network adapters that I figured would be a solution to my problem. The first was a USB that I could never get to work on any computer really, it worked some times and not other times. I got that working with ndiswrapper however every time dhclient runs, it returns a hardware error. I'm guessing its defective, which is why I never really use it to begin with.
But I also have a PCMCIA card. Its an xn-2324g from xterasys. 
it can see the network, it can figure out the signal strength, however it just won't connect to the router.
I have tried with school routers and my home router to no avail.
I have configured it manually and through the network manager, still can't connect.
It seems that it is just not recieving the DHCP Offer, since it says No DHCPOFFERS received.
I've configured it through iwconfig and enabled it through ifconfig. then called dhclient to use wlan1. The activity light lights up, and my router activity light seems to also light up as if it was communicating with it, but it never actually connects.
the card if fairly old, about 5 years or so. I'd like to be able to use it if I can. If I can't use it, though, does anyone have  a cheap alternative that is known to work well without any hassle under ubuntu?

---

### Post by chili555 on 2008-04-19
Well, if you've gotten that far, you are 90% done! Why start over? Why go back to zero?

Most every wireless card will readily connect with:```
sudo iwlist wlan0 scan
```Learn the ESSID you want to connect to. Case sensitive, please, UniWifi is *not* the same as uniwifi.```
sudo iwconfig wlan0 essid uniwifi
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```Please substitute your wireless interface here if it is not wlan0. Skip the key part, of course, if there is no encryption. It will show up in the scan.

Let us know.

---

### Post by mattgen88 on 2008-04-20
I tried setting everything from the command line earlier.

```
mgeneral@matthew-laptop:~$ sudo iwlist wlan1 scan
[sudo] password for mgeneral:
wlan1     Scan completed :
          Cell 01 - Address: 00:E0:98:D8:A7:0B
                    ESSID:"GENERALNET"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level=28/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

mgeneral@matthew-laptop:~$ sudo iwconfig wlan0 essid GENERALNET
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
mgeneral@matthew-laptop:~$ sudo iwconfig wlan1 essid GENERALNET
mgeneral@matthew-laptop:~$ sudo iwconfig wlan1 key 536b6c3021685f7b3f4a7c4c3b
mgeneral@matthew-laptop:~$ sudo dhclient wlan1
There is already a pid file /var/run/dhclient.pid with pid 6517
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan1/00:e0:98:bf:92:3d
Sending on   LPF/wlan1/00:e0:98:bf:92:3d
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
that should show you whats going on.

---

### Post by chili555 on 2008-04-20
> sudo iwconfig wlan0 essid GENERALNETLet's try wlan1, please, since that seems to be your wireless interface.```
sudo iwconfig wlan1 essid GENERALNET
sudo iwconfig wlan1 key <encryption_key>
sudo dhclient wlan1
```Also, we must specify the encryption details:```
Encryption key:on
```Do you have the key?

---

### Post by mattgen88 on 2008-04-20
okay yes, the router has encryption, as I stated earlier.
Key = 536b6c3021685f7b3f4a7c4c3b
it is set to shared WEP encryption
essid = GENERALNET

---

### Post by chili555 on 2008-04-20
Let's try:```
sudo iwconfig wlan1 essid GENERALNET
sudo iwconfig wlan1 key 536b6c3021685f7b3f4a7c4c3b restricted
sudo dhclient wlan1
```Shared key in your router equals 'restricted' in iwconfig. Let me know how it goes.

---

### Post by mattgen88 on 2008-04-20
you sir, are brilliant. I hadn't realized that restricted had to be said directly after the key. I was under the impression I could just type sudo iwconfig wlan1 key <key> then type sudo iwconfig wlan1 key restricted

Thanks for the help! I am just hoping I'll be able to do the same thing at the routers at school. I think I'll be able to use the skills I have learned through the tutorials and information I've gotten since I started this weekend working on this and apply it to the school's network

I'll add to this thread if I have any further issues.

Once again, thank you very much!

---

### Post by chili555 on 2008-04-21
Glad it's working for you! Thank you very much for the kind comments.

If this is your real key, now that you have published it for the whole world to see, I recommend you change it immediately.

---

### Post by mattgen88 on 2008-04-21
yeah, I'm not too worried, there isn't anyone with wireless around my home. I'll be trying out WPA later this week anyways, since I hear there is a performance boost in network traffic compared to WEP encryption as well as a tighter security.

---

### Post by mattgen88 on 2008-04-21
I seem to be having the same problem all over again, but at school.

its an open access point, no encryption. essid UB_Wireless. the dhclient never recieves the DHCP call, even though its broadcasting the requests. 

iv'e tried this: (also tried with the ess id in quotes)
```

sudo iwconfig wlan1 essid UB_Wireless
sudo iwconfig wlan1 enc off
sudo dhclient wlan1

```

the dhclient offer requests just die, as if they're not getting replied to.
also, ubuntu's network manager crashes and I lose the ability to use any of the commands to control my wireless adapter whenever I try and connect through it. :-\

---

### Post by chili555 on 2008-04-21
Just to humor an old Linux-ian, please try:```
sudo ifdown wlan1 
sudo iwconfig wlan1 essid UB_Wireless
sudo iwconfig wlan1 **key** off
sudo ifup wlan1
```

---

### Post by mattgen88 on 2008-04-21
nope, no join, the request times out. :-/

---

### Post by mattgen88 on 2008-04-21
Seems that my campus is having issues with linux 2.6 kernel and connecting to ResNet but I don't think ResNet is included in the open access wireless around campus. But anyways, Still having issues, with open access. I'm about to test my router in open mode to see if I can connect to it in open mode.

---

### Post by mattgen88 on 2008-04-22
same problem with setting my router to open here, I can't get a reply from the router after a dhcp is not receiving an offer :-/

---

### Post by chili555 on 2008-04-22
May I please see the result of:```
cat /etc/network/interfaces
```Thanks.

---

### Post by mattgen88 on 2008-04-22
```

mgeneral@matthew-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback






iface wlan1 inet dhcp
wireless-essid UB_Wireless

auto wlan1

```

---

### Post by chili555 on 2008-04-22
Well, this only looks perfect! Let's try two things and take the first one that works:```
sudo iwconfig wlan1 **"**UB_Wireless**"**
```I am wondering about the underscore. In Googling, I came across one of my own posts on the subject! Also, you can disable ESSID checking with:```
sudo iwconfig wlan1 essid any
```Follow with:```
sudo dhclient wlan1
---OR---
sudo ifup wlan1
```Whichever connects!

---

### Post by mattgen88 on 2008-04-23
Problem seems to persist, I am still unable to connect :-s

---

### Post by mattgen88 on 2008-04-23
just a note, I have also tried sudo iwconfig wlan1 enc open key open to try an resolve this with no avail

currently it is saying "access point not-associated" could this be causing a problem?

---

### Post by mattgen88 on 2008-04-25
upgraded to hardy, still having issues. Network manager still crashes and disappears anytime I try to connect to a network with it.

---

### Post by mattgen88 on 2008-04-25
I tried connecting from a live session and it immediately froze and crashed the session. So, no fix there. Upgraded to Hardy and I still have issues, I haven't gotten to try it out on an open system yet though. I'll try at school tomorrow, but I'm almost confident that it won't connect.

---

