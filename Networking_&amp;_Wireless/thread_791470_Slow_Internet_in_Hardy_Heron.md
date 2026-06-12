---
title: "Slow Internet in Hardy Heron"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by leillo1975 on 2008-05-12
Hello

I have the following problem with my connection:

When I go to any web in firefox, the connection freeze about 4-5 seconds and then It works normally. I try too with Ephipany and the problem is the same. This situation is not only in Firefox, becouse, If I open a terminal and type the following command ```
ping www.google.com
```, it freeze 4-5 seconds too, and then it shows the result normally. 

This problem isn't in my network, because I have another Computer connected with Gutsy Gibbon, and firefox and "ping" works correctly, without delays.



Note: Sorry, my English is bad, I'm from Spain

---

### Post by superprash2003 on 2008-05-12
i think you should give opendns servers a try .here's how you change your dns servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by leillo1975 on 2008-05-12
I try it, but the problem persists....

Remember, I have another computer with Gutsy in the same network and It works well.

---

### Post by Joe of loath on 2008-05-12
is it with wireless? if so, what's the output for iwconfig?

---

### Post by cubeist on 2008-05-12
Try turning off ipv6.

[http://ubuntuforums.org/showthread.php?p=1210481](http://ubuntuforums.org/showthread.php?p=1210481)

---

### Post by leillo1975 on 2008-05-13
Mi network is wired, and I turn off IPv6 to optimice Ubuntu, but I have the same problem

---

### Post by leillo1975 on 2008-05-14
I reinstall Ubuntu and the problem don't repeat.

---

### Post by gganitis on 2008-05-20
I have the same problem. By the same router, the laptop (wireless) downloads on 106 kb/sec and the desktop (wired) on just 5,6 kb/sec!!! On Hardy Heron both pc's.

Please help!!!

---

### Post by awahid2020 on 2008-06-23
> **superprash2003 said:**
> i think you should give opendns servers a try .here's how you change your dns servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)



thanks man
this thing helped me a lot
it was unable to upload at 2 kpbs only before doing that,
but after that its perfect, and browsing speed has increased amazingly.

---

### Post by linuxismywife on 2008-06-24
I also encountered the problem

but when i try this:

```
iwconfig wlan0 rate 54M
```

It worked :)

---

### Post by Arcadian on 2008-07-01
> **linuxismywife said:**
> I also encountered the problem

but when i try this:

```
iwconfig wlan0 rate 54M
```

It worked :)

Thank you SO SO MUCH! :popcorn:

The fix you mentioned above instantly solved my issue, well, once I renewed my wireless connection in Network Manager. It's also reporting my signal strength correctly now too!

My "iwconfig wlan0" output prior
```
wlan0     IEEE 802.11g  ESSID:"Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:24:D5:40   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=68/100  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And after...
```
wlan0     IEEE 802.11g  ESSID:"Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:E3:24:D5:40   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=86/100  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

The symptoms I've had previously have been Network Manager reporting a 1Mb/s connections speed & poor signal strength, even though my wireless router was shifted right next to my wireless card (RT2500). I've been blaming my broadband connection for dire youtube performance all this time! It really was running that slow. I should have guessed it was something like this when the normal NIC connection on my hardy laptop got a normal speed!

Now it's properly reporting 54Mb/s & an appropriate strength. I'm getting the appropriate 200KB/s downloads for my 2Mb/s connection, so am happy again!

I'm going to link this post into a few other threads, as it sounds like others are having the same issue. Really strange, I never had this in gutsy... I wonder why this gets set wrong & never corrects itself?

Thanks again. Rock on! :guitar:

---

### Post by Arcadian on 2008-07-01
Okay folks, looks like I might have spoken a little too soon :( - It doesn't stick after a reboot. I'm going to see if I can find a way to hardwire this, so it runs on every boot (don't see why you should have too).

BTW, I found another post mentioning disabling the Multicast DNS discovery services (avahi-daemon) but this didn't help it seems.... still 1Mb/s after boot on 1st connect...

Cheers!

---

### Post by Arcadian on 2008-07-02
Okay, found how to solve it at startup here [http://ubuntuforums.org/showpost.php?p=5196903&postcount=16]("http://ubuntuforums.org/showpost.php?p=5196903&postcount=16")

Running "sudo gksudo gedit /etc/network/interfaces" it now looks like this...

```
auto lo
iface lo inet loopback

pre-up iwconfig wlan0 rate 54M
```

So, when I now startup & login for the first time, I get 54MB/s on my wireless every time & am happy again! :)

P.s. Disabling IPV6 properly [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") didn't make much difference here at all, and I've turned the avahi-daemon processes back on too.

---

### Post by thrashfan on 2008-07-03
> **linuxismywife said:**
> I also encountered the problem

but when i try this:

```
iwconfig wlan0 rate 54M
```

It worked :)

Whenever I try that my entire connection screws up. It won't even connect to google. I'm also pretty new to ubuntu and linux altogether but I just can't stand how slow my internet has been when I used to get a download rate of 450 kb/s on windows and here I get 30.

---

### Post by ipsi on 2008-08-03
Many thanks from a fellow New Zealander for posting that :D. I'm not sure if I'll get that much better international speeds, but maybe I won't feel like my 10MB connection is being wasted quite so much now!

---

### Post by oliver85007 on 2010-04-24
I had the same problem try this:

[https://help.ubuntu.com/community/Firefox](https://help.ubuntu.com/community/Firefox)

**Custom Configuration**

 There are a number of basic adjustments you can make that have been reported to improve Firefox's performance. 
Open a new tab in Firefox and enter in the address: 
about:configNo http, or anything, just 'about:config'. Then search for each of the following, by typing them in the Filter box, and make the suggested changes: 

[LIST]
[*]**network.dns.disable****IPv6** - Double-click on this to set it to **true** 
[*]**network.http.max-connections** - set to **96** 
[*]**network.http.pipelining** - set to **true** 
[*]**network.http.pipelining.maxrequests** - set to **8**  
[*]**network.http.proxy.pipelining** - set to **true**
[/LIST]

---

