---
title: "Slow internet ubuntu 7.04"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by Humle on 2007-04-23
After installing ubuntu 7.04, had my internet been wherry slow, max download speed 20 kb/s.
When i trying to boot op in XP and download, are my download speed 200-500 kb/s.

Anny one there knows whats wrong..?

---

### Post by Kobalt on 2007-04-23
How do you connect to the internet : wifi, modem, router, etc. ?
How did you set up your connection in Ubuntu : automatically, did you install drivers, etc. ?

---

### Post by Humle on 2007-04-23
How do you connect to the internet : wifi, modem, router, etc. ?
I connect to the internet with a router/lan

How did you set up your connection in Ubuntu : automatically, did you install drivers, etc. ?
Automatically.

---

### Post by Kobalt on 2007-04-23
Can you please post the output of ```
ifconfig
``` and a ping to google for instance ```
ping -c 4 google.com
```

---

### Post by Humle on 2007-04-23
**ifconfig:**
eth2      Link encap:Ethernet  HWaddr 1A:73:11:02:BF:FB  
          inet addr:192.168.1.57  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1873:11ff:fe02:bffb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:96755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94181 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:124847900 (119.0 MiB)  TX bytes:8027175 (7.6 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2916 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153346 (149.7 KiB)  TX bytes:153346 (149.7 KiB)

**Ping google.com:**
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=239 time=147 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=239 time=150 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=239 time=151 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=4 ttl=239 time=150 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 147.335/150.119/151.921/1.740 ms

---

### Post by maxol on 2007-04-23
I have the same problem after doing a clean install of Feisty. I'm connected to the my router wirelessly using Rutilt (Wicd also works but Network Manager doesn't). It's annoying as I've got round the Network Manager problems to have very slow download speeds; also file downloads often fail before they complete.

My laptop running edgy connected to the same router has no problems.

Any ideas?

> ping -c 4 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=243 time=126 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=243 time=123 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=243 time=116 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3000ms
rtt min/avg/max/mdev = 116.065/121.911/126.233/4.298 ms

> ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:901 (901.0 b)  TX bytes:901 (901.0 b)

ra0       Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe90:dc44/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:53148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143936 errors:14120 dropped:14120 overruns:0 carrier:0
          collisions:13162 txqueuelen:1000 
          RX bytes:62126138 (59.2 MiB)  TX bytes:10943024 (10.4 MiB)
          Interrupt:10 Base address:0xc000 

---

### Post by maxol on 2007-04-24
bump

---

### Post by scubastevegk on 2007-04-24
It appears that you're having the same problem I am with your ping results.  No packets are lost, and the reply times are normal...but they take an incredibly long time to register and display.  The total response time on your 4 packets to Google is under 1 sec, but your total ping time shows as 3 seconds.

Furthermore, these same types of ping results happen to me with computers on my own LAN.  I do not see any slowdown in web browsing or LAN resource access - it just seems like ping results are delayed for some reason.  Anybody have any ideas?

---

### Post by StarQuake on 2007-04-25
I'm having the exact same problem, don't know where to start though.

It looks like ping takes too long to resolve a certain hostname. Though 'host' does it very fast. Also if i do a 'ping -c5' it's fast.

---

### Post by Tbay on 2007-04-25
if your running kernel 2.6.20-15 try booting 2.6.17.11 or 2.6.17.10. i had the same problem and this helps me

---

### Post by maxol on 2007-04-25
Where would I find those kernels, I don't see them in Synaptic?

---

### Post by Humle on 2007-04-25
I installed  firestarter, and now my internet works.. :D

---

### Post by Jarn on 2007-04-25
I have noticed this same sort of thing. And I know it's not just my connection. After I installed Feisty, anything I downloaded would get between 5 and 15 kb/s and we have a cable modem. I know it's not just my connection or the server the file was hosted on because I had my brother try to download it from his Windows installation and he got 70 kb/s. I'd run those commands and try changing my kernel, but i'm not at my Linux box atm.

---

### Post by scubastevegk on 2007-04-25
For whatever reason today, my pings are displaying in a normal amount of time.  I've changed nothing network related on my system, so unfortunately I've got no solution to offer :confused:

---

### Post by onlybui on 2007-04-25
Im connected via Wifi using a Laptop and my internet connection is super slow and I just updated to 7.04 does anyone know how to fix this... seems to be ok if I connect directly...

---

### Post by Jarn on 2007-04-25
Lucky you, I'm directly connected and it's as slow as molasses in a Canadian winter!

---

### Post by stu_edgar on 2007-04-25
I'm having same network problem. I thought it was nsswitch but apparently not.
Sorry newbie question - re:  best way to use another kernel - is this to load a new older kernel in synaptic?
will this sort out GRUB automatically?
Thanks

---

### Post by medad on 2007-04-25
HUMLI,

How did firestarter help you?  It sets up a firewall.  Could you please explain what you did and what  speed you are currently connecting at?

---

### Post by Sendervictorius on 2007-04-26
This happens to me too. downloads start ok but never complete. slow, but also a constant 800bps background receive without any internet activity.

Atheros AR5212 PCI card. DHCP & WEP.

see my post [http://ubuntuforums.org/showthread.php?t=423732](http://ubuntuforums.org/showthread.php?t=423732)

---

### Post by Humle on 2007-04-26
> **medad said:**
> 
How did firestarter help you?  It sets up a firewall.  Could you please explain what you did and what  speed you are currently connecting at?

Firestarter set up my firewall. After running firestarter my download speed came up over 800 kb/s. before installing firestarter was my download speed max 30 kb/s.

---

### Post by StarQuake on 2007-04-26
Installing the edgy kernels did not fix it for me. For the people that still want to try it, just add the edgy repositories to /etc/apt/sources.list and install using synaptic

---

### Post by Jarn on 2007-04-26
I think I found out what my problem is. I don't know of you guys have the same one I do, but for me it's KGET. I was using Flashgot to redirect downloads to kget. In kget, I get less than 1 kb/s. I decided to set flashgot to let me choose how to download it instead of automatically using flashgot. I downloaded a file once without it, noting my speed (800 kb/s) then once with it and noting my speed (500 b/s - yes, that is BYTES per second. Less than one kb/s). So I've solved my problem, although it makes me VERY unhappy.

---

### Post by olskar on 2007-04-26
I have same problem..Im thinking of going back to edgy..its not worth it

---

### Post by medad on 2007-04-26
> **Humle said:**
> Firestarter set up my firewall. After running firestarter my download speed came up over 800 kb/s. before installing firestarter was my download speed max 30 kb/s.

Thanks for responding.  My system works most of the time (I have a 54MPS USB), but I noticed that the stick gets very hot.  I tried firestarter, but didn't appear to help me any.

---

### Post by shabri on 2007-04-27
Same problem here - firestarter made no difference.  Downloading is like 10-15 times slower than under XP :(

---

### Post by Sendervictorius on 2007-04-27
See this thread for a possible solution to slow 7.04 wireless internet.

[http://ubuntuforums.org/showthread.php?t=423732](http://ubuntuforums.org/showthread.php?t=423732)

---

### Post by maxol on 2007-04-28
I tried your suggestion Sendervictorius but it didn't help, I think I'm going to have to go back to Edgy untill this gets fixed.:(

---

### Post by shabri on 2007-04-28
This is great!  I have a rock solid, virtually uncrashable linux system, flashy cube effects for swithcing between desktops, the best of open source software ... 

... and pre-broadband connection speeds ... :(

---

### Post by kleu on 2007-04-28
I am having the same issue here. Around 5KB download speed where it should be around 2MB for my cable connection with my wireless network card. However I did notice the upload speed does not has this slowness problem.  Try changing /etc/nsswitch.conf as suggested in another post doesn't help either. Sounds like something very specific with ubuntu 7.04 wireless networking???

---

### Post by stu_edgar on 2007-04-28
I've tried a few things, the best fix seems to be 
downgrade the avahi daemon to the feisty one 
(use package - force in Synaptic)
This helps though doesn't solve everything
Stu

---

### Post by shabri on 2007-05-01
bump

---

### Post by stu_edgar on 2007-05-01
Best solution for me (after trying _everything)_ is to replace network  manager with wifi radar
seems to help a lot

wifi radar is in synaptcs, and just stop NM loading in system preferences sessions startup

---

### Post by thedragon4453 on 2007-05-02
So, I installed firestarter as well, and that did improve speeds. especially torrent speeds. pre firestarter i would max out at 10kbps, now im around 40kbps (im also downloading openoffice on my vista laptop though.)

it doesnt make a lot of sense that a firewall should improve speeds, unless it is overriding default network settings for feisty. ive read that feisty comes pretty locked down by default. anyway, if someone that knows what they are talking has any input, id love it. i wouldnt mind not having to run firestarter.


thanks

---

### Post by shabri on 2007-05-02
> **stu_edgar said:**
>  replace network  manager with wifi radar


this helped me too - thanks stu

---

### Post by stu_edgar on 2007-05-06
My pleasure.  I wish they fixed this in Beta!

---

### Post by buntu82 on 2007-05-14
I have the same problem. I recently buy a PCMCIA card and i configured it on my Feisty, my wifi connection is up to 22 Mbit/s but real download is about 20 kb/s.

If I try to load previous kernel nothing changes.

What can i do?

This is my iwconfig
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"default"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: XXXXXXXXXXXX
          Bit Rate:22 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chowdah45416 on 2007-05-27
I've had this same problem with my wired connection.  I tried downgrading avahi-daemon, but it still doesn't seem to work.  I'm gonna be downgrading back to edgy, which I hope will work.  Hopefully this will get fixed soon.

---

### Post by buntu82 on 2007-05-28
> **buntu82 said:**
> I have the same problem. I recently buy a PCMCIA card and i configured it on my Feisty, my wifi connection is up to 22 Mbit/s but real download is about 20 kb/s.

If I try to load previous kernel nothing changes.

What can i do?

This is my iwconfig
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"default"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: XXXXXXXXXXXX
          Bit Rate:22 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
New kernel  2.6.20-16-generic **solved** my problem

---

### Post by buntu82 on 2007-05-29
I've got full wlan speed with my PCMCIA card.
I insert my PCMCIA into the slot **only after** linux has been started and desktop is loaded.

Try with this step e tell me if it works.

---

### Post by Error1312 on 2007-05-29
Using kernel version 2.6.20-15 instead of 2.6.20-16 makes my internet speed normal again.

---

### Post by lsutiger on 2007-06-01
Nothing suggested here fixed my problem. Tried it all.
The reason I went to fiesty is because a lot of ppl were having success with the ATI 1150 Express video, but I can not get the drivers to load for that either.

---

### Post by chowdah45416 on 2007-09-29
I downgraded to 2.6.17-10 and that solved my problem.  I have a Dell Latitude D610 and have repeated this problem in anyone else with this or the D620.  Does using the Edgy kernel fix this for anyone else?

---

### Post by Kardacian on 2007-09-29
I had the same problem and this fixed it for me. where ping running very slow and sessions were slow to start.  I searched around and found the following fixes.  Hope this works for you.

In etc/hosts change the line
  127.0.0.1 localhost 
to
  127.0.0.1 localhost inspiron

In /etc/nsswitch.conf change the line
   hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
   hosts: files dns


no reboot required and it fixed ping as soon as the file was saved

:popcorn:

---

### Post by Kardacian on 2007-09-29
BTW I am running 7.04

---

### Post by dark_harmonics on 2007-10-05
I have the opposite problem on many many computers. It seems that when i connect via wireless i get an excellent connection but when i used a wired connection my speeds crawl to a halt (and yes sometimes to a complete halt and timeout).

I am on a corporate network and i know my switch is good (i use it to config windows boxes all day). I have a mac book pro running Ubuntu that doesn't have the problem at all. I tried all the above fixes without success. 

The funny thing about this is that for the first 3 seconds of so, the connection works! I can get things installed though apt-get if i just keep restarting it every time it stops but this is really annoying!

Any help would be appreciated. I've searched high and low for an answer to this one :(

---

### Post by kwisatz on 2007-10-09
I have the same problem with my Ubuntu PC connected via ethernet with the office LAN. I thought that was a LAN firewall problem, my download speed is never more thant 30 kb/s. I changed /etc/nnswitch.conf and the situation is slighty better...

---

### Post by lsutiger on 2007-10-09
Well, I finally upgraded the kernel and now it is blazing...I forget which kernel number it is and I am away from that computer right now, but I think it was up to the 16.29.

---

### Post by dark_harmonics on 2007-10-16
> **lsutiger said:**
> Well, I finally upgraded the kernel and now it is blazing...I forget which kernel number it is and I am away from that computer right now, but I think it was up to the 16.29.

I tried it on a gusty beta machine with the same error :(. Maybe the kernel upgrade process did something to the networking components to fix the problem native in the ubuntu release :(. 

(notice all my sad faces :P)

---

