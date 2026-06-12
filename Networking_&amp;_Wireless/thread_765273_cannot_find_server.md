---
title: "cannot find server"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by Leigen_Zero on 2008-04-24
Hello there, I am having a wierd problem with my internet on ubuntu.

Basically i can connect to a network, but for some reason about 5-10 mins after connecting all I get out of firefox is 'cannot find server' and ktorrent also loses all its connections, but the internet is still connected (network manager does not disconnect from the internet)

also, is there any way to get ubuntu to search for all wireless networks in an area as soon as i log in,  I'm currently having to manually enter the ssid and wpa key each time.

thanks
Leigen_Zero

---

### Post by Swiftfeet8 on 2008-04-24
I take it you are connecting to a wireless network for your internet connection?  Try doing a ping to a website and see if you get a response.  Then try pinging an IP address outside of your network and see if you get a response.

As far as searching for wireless networks when you log on if you have your wireless adapter set to "roam" you should see all available wireless networks when you click on the network icon on your panel.  Then you can just choose the network you want to connect to, and it will prompt you if you need to provide a key.

Let me know if you need any more help.

---

### Post by prshah on 2008-04-24
> **Leigen_Zero said:**
> Hello there, I am having a wierd problem with my internet on ubuntu.

Basically i can connect to a network, but for some reason about 5-10 mins after connecting all I get out of firefox is 'cannot find server' and 

also, is there any way to get ubuntu to search for all wireless networks in an area as soon as i log in,  I'm currently having to manually enter the ssid and wpa key each time.



See my (solved) thread on [http://ubuntuforums.org/showthread.php?t=718709&highlight=firefox+lynx](http://ubuntuforums.org/showthread.php?t=718709&highlight=firefox+lynx) regarding intermittent browsing problems. Does it help?

you can add the iwconfig command with the relevant security and essid parameters to your /etc/rc.local file, so that it will be executed on startup automatically.

---

### Post by Leigen_Zero on 2008-04-24
It is not a problem with specific websites, when it happens all websites become unavailable, I am using a wireless connection, it cannot be the router as I have had the problem with two different routers and two different ISPs (both my home and university internet).  The network manager says the connection is fine, but any websites I try to visit give me an 'error loading page: cannot connect to server',

p.s. my network manager does not automatically detect them, when I turn on my laptop I have to manually type in the SSID in 'connect to another network' THEN it connects to that network and finds the others.

---

### Post by Leigen_Zero on 2008-04-28
ok the most recent time it happened (i.e. started saying 'cannot find server') i did a ping of yahoo:
```

george@george-laptop:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com

```

and iwconfig reports:
```

george@george-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"2 Alexander Terrace"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:65:76:06   
          Bit Rate=54 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Leigen_Zero on 2008-05-13
have been observing the issue for a couple of days and have found that it seems to occur when my wireless card searches for networks (it doesnt do so on startup automatically, but once I've used the 'connect to other network' option it will happily begin searching for networks) so I think what is happening is it is losing communication every time it searches for available networks.

---

