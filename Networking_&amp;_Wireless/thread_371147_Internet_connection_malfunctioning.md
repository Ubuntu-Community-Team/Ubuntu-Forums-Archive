---
title: "Internet connection malfunctioning"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by sandldan on 2007-02-26
I installed Ubuntu 6.10 on my computer 2 days ago, everything went smoothly but today when i started up my computer i was unable to connect to the internet in every way. Checked my networking settings and such but found nothing faulty, i have both windows and linux installed on different partitions on the computer.
When i tried to logg into windows xp the internet worked just fine, checked this again after 10 hours but the problem still remains, got 2 computers in the house connected to a switch and then to a DSL router.
Im still pretty new with linux and ubuntu, hoping you can help me find the problem

Update: Now a friend whom i just gave Ubuntu to just got the same error, the internet connection says it's just idle and unable to connect anywhere.

---

### Post by essexman on 2007-02-26
I would love to help but I have the same problem on 6.06-1 - no connection.  I am currently connected vai the Live CD - as recommended by the talktalk helpline.

This is very embarrassing as my Internet problems are always down to talktalk - but this time it is my Dapper installation.

Something must have broken - probably on the weekend upgrade - but I can't figure out what; everything was working fine last night and know settings have changed as far as I can see.

---

### Post by Rui Pais on 2007-02-26
In order to somebody could help you, you need to post the output of:
```
ifconfig
```
```
cat /etc/network/interfaces
```
and ```
cat /etc/resolv.conf
```

---

### Post by sandldan on 2007-02-26
Ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:50:8D:45:A5:BC  
          inet addr:85.157.26.228  Bcast:85.157.31.255  Mask:255.255.224.0
          inet6 addr: fe80::250:8dff:fe45:a5bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709 (709.0 b)  TX bytes:2615 (2.5 KiB)
          Interrupt:185 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

cat /etc/network/interfaces :
> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0


cat /etc/resolv.conf :
> nameserver 62.148.192.130
nameserver 62.148.192.154

---

### Post by Rui Pais on 2007-02-26
hi,
my bedtime (badly need to sleep a little...) 

My suggestion would be starting by avoid ipv6 from loading. Thats a general source of problems.
Do:
```
sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
```
reboot and check if you can surf web or do sudo apt-get update on a terminal.

---

### Post by sandldan on 2007-02-27
[QUOTE=sudo echo "blacklist ipv6" >> /etc/modprobe.d/blacklist[/CODE][/QUOTE]

Hiya, were unable to enter the whole string of the line at the same time got permission denied, but wrote "sudo echo "blacklist ipv6" which worked. Rebooted but still the same error.

Tried to do a 
sudo apt-get update
But was just connecting for a while until it failed.

---

### Post by Rui Pais on 2007-02-27
sorry without complete command that don't do nothing...

Do instead:
```
gksudo gedit /etc/modprobe.d/blacklist
```
and at the end of line add:
> blacklist ipv6
(without any "")

and then reboot.

---

### Post by sandldan on 2007-02-27
Wrote 
> gksudo /etc/modprobe.d/blacklist
in terminal just asked for my password without anything happening. Rebooted and wrote it like this
> gksudo /etc/modprobe.d/blacklist blacklist ipv6
Rebooted but still the same problem, might have misinterpreted your instructions please excuse my current newbiness with this :-?

---

### Post by Rui Pais on 2007-02-27
> **sandldan said:**
> Wrote 

in terminal just asked for my password without anything happening. Rebooted and wrote it like this

Rebooted but still the same problem, might have misinterpreted your instructions please excuse my current newbiness with this :-?

sorry sandldan, my mistake.
I was in  a rush this morning and only now i have a moment of calm to read this. I forget to type a part of the command (the text editor). 

do:
```
gksudo gedit /etc/modprobe.d/blacklist
```
(replace gedit with kedit if you are a kubuntu user)
and that will open a text editor on the admin mode.

And the line at the bottom:
> blacklist ipv6
and reboot.

No need for apologies for your newbiness. Welcome to linux if this is your first steps on it. 
My opinion is that we are all always newbies :)

I'm the one who must ask for excuses for my previous rush and incomplete command.

---

### Post by sandldan on 2007-02-27
When i booted up again the only difference was that the firefox 404 site could not be found came instantly, and the sudo apt-get update also failed instantly

---

### Post by Rui Pais on 2007-02-27
can you post what it's the output of ifconfig now?

Do you know what it's de the ip of your router? Should be the one you use to access the router configuration (something like  192.168.1.1 or 10.0.0.2)?

---

### Post by sandldan on 2007-02-27
Rebooted and was going to do what you said, everything's working fine now all of a sudden :o

the ifconfig now, if interested :p
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:45:A5:BC  
          inet addr:85.157.26.228  Bcast:85.157.31.255  Mask:255.255.224.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:846979 (827.1 KiB)  TX bytes:204494 (199.7 KiB)
          Interrupt:185 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)
```

---

### Post by Rui Pais on 2007-02-27
> **sandldan said:**
> Rebooted and was going to do what you said, everything's working fine now all of a sudden :o

the ifconfig now, if interested :p

the > everything's working fine now it's more interesting :lol:

anyway your ifconfig says that you don't have now an ipv6 address so you managed to blacklist ipv6 succefully.

That's what must have done the trick (and your system uses less resources and don't waste time at boot up loading that module :))... 
the only concern now it's why it failed first time? 
Let's hope that it was something that won't happen again. 
If you find your self without connection again, post back here, and we see what can be done.

Have fun :)

---

### Post by sandldan on 2007-02-27
Let's hope it wont screw up again, but i'll know where to turn for help. Thanks for your time

---

### Post by Princey on 2007-02-27
I've got a similar problem. I decided to do a clean install after messing up my installation trying to get my HP Scanner working(that's another post). I have both wireless and wired and like other times asked it to configure the wireless connection when asked. Forgot I don't use WEP so it couldn't. When prompted, I told it I'll configure later and proceeded. On booting up, NO INTERNET.

I said, ok, that's fine. I'll just enable the ethernet (wired) card and I'll be on my way. How wrong was I. Even after enabling and configuring it to load at boot, I'm still without internet. I'm typing from another machine in the house that runs Windows. Weird thing it correctly registers an IP address from the router.

Here are the results of cat /etc/network/interfaces:

>  cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0


Ifconfig yields:
> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:08:55:01
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17566 (17.1 KiB)  TX bytes:342 (342.0 b)
          Interrupt:201 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2960 (2.8 KiB)  TX bytes:2960 (2.8 KiB)


I've disabled ipv6 as stated earlier but still can't get a connection. Is there anything I can do besides another re-install? I'm sure it's something I must be overlooking.

---

### Post by Rui Pais on 2007-02-27
whats your router ip? what's your /etc/resolv.conf? 
have you tried connect using a static ip?

---

### Post by Princey on 2007-02-27
My router IP is 192.168.0.1 and no, I haven't given that a shot as yet. Strange enough it's the Wireless Card that's not yet connected I use with a Static Ip address for vpn reasons.

---

### Post by Rui Pais on 2007-02-27
> **Princey said:**
> My router IP is 192.168.0.1 and no, I haven't given that a shot as yet. Strange enough it's the Wireless Card that's not yet connected I use with a Static Ip address for vpn reasons.

try then with a static IP and ensure that gateway is set for the router ip.

check if /etc/resolv.conf have the router it too. 

Maybe its confused with the dhcp...

---

### Post by Princey on 2007-02-27
> **Rui Pais said:**
> try then with a static IP and ensure that gateway is set for the router ip.

check if /etc/resolv.conf have the router it too. 

Maybe its confused with the dhcp...

Tried that, nothing. Result of ```
cat /etc/resolv.conf
``` yields nothing. Sends me back to the prompt.

---

### Post by Rui Pais on 2007-02-27
> **Princey said:**
> Tried that, nothing. Result of ```
cat /etc/resolv.conf
``` yields nothing. Sends me back to the prompt.

resolv.conf needs to have DNS servers ip.

You can either manually editing the file and add nameserver 192.168.0.1 
or using network-admin and go for DNS tab, and type just router IP.

If that fails too, try this IPs instead (fom openDNS):
nameserver 208.67.222.222
nameserver 208.67.220.220

htp

---

### Post by Princey on 2007-02-27
I'll try that in a minute but the network tab does have the router's IP each time I checked. Something else must be blocking it but I'll try that and report back.

---

### Post by Princey on 2007-02-27
Thanks a million. The manual editing of the file worked. I'm now posting from my Linux Machine.

---

### Post by Rui Pais on 2007-02-27
> **Princey said:**
> I'm not posting from my Linux Machine.

i bet you wanted to say I'm posting from my Linux machine and not the other way :lol:

glad i could help,
have fun :)

---

### Post by karachuonyo on 2007-02-27
I'm also having a problem connecting thru wireless in kubuntu. My wireless card i believe is installed and i can be able to scan available networks. However despite seeing my WEP and essid i still get not associated and cannot connect. The card works flawlessly in xp. I have a same manufacturer (safecom) pcmcia card and that works in kubuntu. I have searched the forums for a while and even blacklisted ipv6 but no wireless connection. Any ideas welcome.

---

### Post by Princey on 2007-02-27
> **karachuonyo said:**
> I'm also having a problem connecting thru wireless in kubuntu. My wireless card i believe is installed and i can be able to scan available networks. However despite seeing my WEP and essid i still get not associated and cannot connect. The card works flawlessly in xp. I have a same manufacturer (safecom) pcmcia card and that works in kubuntu. I have searched the forums for a while and even blacklisted ipv6 but no wireless connection. Any ideas welcome.

Have you tried using KnetworkManger or KWan to connect? Also, to get WEP you must have wpa_supplicant installed.

---

### Post by karachuonyo on 2007-02-27
Yeah, i have wpa_supplicant. I'm not sure about the KWAN but i've tried using the wireless assistant wireless LAN manager and filled in my WEP and the other details. I've tried to copy the same details from my kubuntu laptop except for the device IP even though i'm on automatic IP addresses.

---

### Post by Princey on 2007-02-27
> **karachuonyo said:**
> Yeah, i have wpa_supplicant. I'm not sure about the KWAN but i've tried using the wireless assistant wireless LAN manager and filled in my WEP and the other details. I've tried to copy the same details from my kubuntu laptop except for the device IP even though i'm on automatic IP addresses.

To be honest with you, the Wireless Lan Manager has always given me issues that's why I defaulted to KnetworkManager instead. Lately, I've grown to fancy kwan instead and it does an excellent job even if you're using a laptop and have to log in to various AP's.

---

### Post by Princey on 2007-02-27
> **Rui Pais said:**
> i bet you wanted to say I'm posting from my Linux machine and not the other way :lol:

glad i could help,
have fun :)

Thanks :popcorn: I made the correction. I meant now* not what I had previously.

---

