---
title: "Wireless VERY slow"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by qalimas on 2007-01-06
I just installed Kubuntu Edgy on my girlfriend's desktop, and she uses wireless.  She connects with a Belkin USB adapter, which after compiling ndiswrapper 1.3.3, works.  At my house, on my desktop, it hit wireless fine, no issues.  I come to hers, install Kubuntu, setup wireless, and it's SLOW.  I know it's not the wireless here, because I'm on with my laptop right now, with no issues.

When I try to go to a web page in either Konqueror or Firefox, it takes forever to load a page, but once it starts, it loads it almost instantly.  When I did an apt-get for Firefox, for about a minute it didn't do anything, then when it started speeds got to 200kbps.

Why is it doing this?  She won't keep Kubuntu if her internet is this slow =/

Note, I can connect her AIM in Kopete and send her an IM and she gets it instantly, and I get hers instantly.

What's the deal???

Help is MUCH appreciated! =(


Edit----------------
PS: knetworkmanager and wlassistant both do not connect to networks.

I have to run sudo iwconfig wlan0 essid "building b" then "sudo dhclient wlan0" to connect.  maybe this has something to do with it? (On my desktop, her adapter worked fine with both programs, but then again, it worked flawlessly, much like it isn't on her desktop...)

---

### Post by jpkotta on 2007-01-06
Sounds like resolver issues.  Compare /etc/resolv.conf on both machines.  

Another possibility is ipv6 vs. ipv4.  
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by qalimas on 2007-01-06
resolv.conf looked fine when I checked it, the only difference I noticed is at my home, the IP was 192.168.0.x -- over here their system is 192.168.1.x -- I don't see how that could effect it, but I don't see anything else as to why it would do this.

Unfourtunately, my laptop's wireless doesn't work properly in Linux, so I'm on Windows and have no resolv.conf to compare it to over here =/

I disabled IP6 as you suggested, no changes in the system.

Maybe I mention, ping works as it should... getting 58 m/s hits instantly on a Google ping, the same as my laptop is getting and the internet on it right now is very responsive...

---

### Post by qalimas on 2007-01-06
While my laptop works fine on the "building b" access point, I don't know what I did but knetworkmanager works for some reason nwo, her desktop still won't work properly on "building b", but works perfectly fine on "wishireapta", just a little lower strength, but it's still pretty fast, MUCH faster than "building b" was, so I suppose that'll do =)

---

### Post by RideYourBike on 2007-01-07
Qalimas,

Are you using WEP?  I have a very similar issue which I haven't solved yet.  For me, I get the same performance you describe when using a WEP enabled connection in ubuntu (Dapper).

---

### Post by rbhigday on 2007-01-07
I agree with Qalimas, if you have any encryption like wep, wpa, or others try removing it and see if your speed improves.

---

### Post by qalimas on 2007-01-07
No WEP, completely encryption free network (it's in an apartment complex, they give free wireless to their residents).

---

### Post by Rob_H on 2007-01-07
If there are a lot of wireless access points in the area, try switching yours to a unique channel. That can make a big difference. As for why it only affects her laptop, it could be that her network adapter is more susceptible to channel interference, and might not be an Ubuntu problem at all. You can get a list of local access points and their channels by running:
```
iwlist scan
```

Don't rely on KNetworkManager to tell you because it combines multiple access points with the same SSID into one entry.

---

### Post by RideYourBike on 2007-01-08
As I mentioned above, I had a similar issue and found the cause

After capturing some packets, I discovered the router was dropping AAAA (IPv6) DNS requests.

I documented my solution here:
[http://www.rideyourbike.org/rants/2007/01/slow-wireless-connection-ipv6-not.html](http://www.rideyourbike.org/rants/2007/01/slow-wireless-connection-ipv6-not.html)

Hope this helps.

---

