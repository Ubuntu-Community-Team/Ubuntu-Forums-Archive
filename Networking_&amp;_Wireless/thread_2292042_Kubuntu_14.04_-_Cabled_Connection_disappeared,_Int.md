---
title: "Kubuntu 14.04 - Cabled Connection disappeared, Intermittent WIFI"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by zeropositivo on 2015-08-24
Running Kubuntu 14.04, 64bit, Kernel version 3.13.0-62 (just updated to see if the issue could fix itself), dual booth with Win 8.1

Today after a normal boot coming back from work, I reconnected my laptop to my desk, I noticed my laptop was having a mighty hard time connecting to my wired connection. It would just sit there connecting for a good 20-30 seconds, then spout out 2 notifications, one about the connection being deactivated, the other about "IP configuration being unavaliable". The process would repeat over and over and over again, with the notification tray geting more and more spammed with those two messages over time (and, of course, no connection)

So I hooked it up to my wifi, to begin searching for possible solutions

Someone mentioned wicd network manager being superior to the bundled one. I tried that one too, but the result was exactly the same, so I scrapped it and went back to the default one.

While poking around, I renamed the wired connection from "connection 1" to "home" (might as well, since I never bothered to do it before)... and the connection disappeared. I've tried checking the cable and resetting the wired router, but it simply doesn't see anything attached to the cable port anymore

In addition, I've now noticed that every 5-10 minutes, the WiFi connection will disconnect for a few seconds, and reconnect back after similarly short time

Here's attached the wireless info script:

[http://pastebin.com/Yjkt0HiB](http://pastebin.com/Yjkt0HiB)

I'm still relatively new to linux, so please be gentle with me if I've screwed something up. 

Thanks!

---

### Post by SeijiSensei on 2015-08-24
By default, the machine should be getting its configuration information via the DHCP service that usually runs on your router.

Don't try to connect both the wired and wifi to the same router simultaneously; that can lead to problems.  Choose one or the other.

Do you know that network range that the router is supporting, something like 192.168.1.something perhaps?  If so, you can try setting up the Ethernet connection manually.  If that works, then we can figure out where to go from there.  

Suppose the network uses 192.168.1  as the prefix.  Try this in a Terminal:
```

sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ip route add default via 192.168.1.1

```
Now try to ping your router with "ping 192.168.1.1".  Does that work?  Can you now connect to the Internet?

If your router uses a different network address, replace "192.168.1" with whatever it is using.  Some routers use 192.168.0 for instance.  If you can connect with wifi, run the command "ifconfig" by itself to see what address is assigned to the wifi adapter, usually called "wlan0".  That will tell you the correct prefix to use.

---

### Post by zeropositivo on 2015-08-25
Hello, and thanks

Running ifconfig returns 192.168.1.134 for eth0 and 192.168.1.135 for wlan0

I've also tried running those commands you suggested, but I don't see any result (accepts the commands, returns nothing except for the usual sudo password request)


I'm doing all of this with the wifi connection disabled, only renabling it to post in here

Also, I noticed today that my cabled connection still works on the Win partition, so I now know it's not a faulty cable


P.S. Almost forgot to run the ping. Results are:

192.168.1.1 returns not reachable
192.168.1.2 returns a good ping
192.168.1.134 returns not reachable
192.168.1.135 returns a good ping

---

