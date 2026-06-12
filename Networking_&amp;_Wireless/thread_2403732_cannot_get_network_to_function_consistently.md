---
title: "cannot get network to function consistently"
date: 2018-10-15
forum: Networking &amp; Wireless
---

### Post by jgw on 2018-10-15
I continue to have problems with my connection.   Right now settings and the icon top bar dropdowns tell me I am connected.  I am not (cannot ping yahoo.com, etc).  When its trying to connect settings will sometimes tell me that "status unknown (missing)".  Sometimes I am connected and it just stops, even though it thinks its connected.  To fix that I turn off the network and then turn it back on and, at least 70% of the time it won't connect.  This is driving me nuts.  I just did a complete re-install and that didn't help a bit.

I am going to put 2 files on pastbin.  The first will be called netstuff.  This is a copy of the results of some commands.  Each one will tell the viewer if I am really connected or told I am connected whilst not being able to ping anything, etc.  That file will be called "netstuff".  I will also post a copy of my netstat file.  

I don't know what else to do.  Oh, It doesn't matter if I am using a wired or a wi-fi connection.  The results are all the same, ie. network simply stops working whilst setting and icon dropdowns say I am, just stops working and says so, etc.  This is true whether I have the vpn up or not.  None of this makes any sense to me.

I have two network icons, one for the network and one for the vpn.  The vpn icon remains solid, the network icon goes from solid to greyed out w/question mark, sometimes and other times greyed out with something on the lower right network block (there is one block connected to 2 others).  I have also tried to test my netspeed with netspeed-cli as well as others on the net and they all failed to get the job done.  

I had to turn off my wired connection and turn on my wi-fi connection to get this onto pastbin, I tried, several times, with both the wired and the wi-fi connection to upload my syslog and failed.  Its 2mb long and it just craps out. so, I can only off the one below.

[https://pastebin.com/H08w0wcv](https://pastebin.com/H08w0wcv)


Thank you.................

---

### Post by TheFu on 2018-10-15
Troubleshooting networking comes down to a few simple things.

1) use only one type of connection at a time.  Use wired ethernet OR wifi.  Don't enable both at the same time.

2) don't use any VPN. PERIOD.

3) with 1 active connection, try to ping the IP of your local router.  Does that work or not?  If it does, continue on, the driver and network device on the computer are fine.

4) with 1 active connection, try to ping a well-known IP on the internet.  8.8.8.8 is an example. If this works, continue on. The internet is fine too.  You've just eliminated all IP issues on your LAN or on the internet.

5) with 1 active connection, try to ping a well-known server on the internet using a name.  google.com is an example. If this works, you are done.  The problem was temporary and is fixed now.  If google.com doesn't work, try a different server, like yahoo.com or microsoft.com.  If you can't ping any of them, but the 8.8.8.8 ping worked, you have a DNS issue.  Tell people here about it and get help.

Until all these things are sorted, don't enable, touch, try, install any VPN.  VPNs don't work until all the things above work perfectly.

netstat isn't actually helpful at this point. It is just cruft until someone specifically requests it.

In short, do these things **in order**. If 1 files, don't bother with 2 and 3.  If 2 fails, don't bother with 3.
```
ping {router IP}    # <--- you must know your LAN router IP.
ping 8.8.8.8
ping google.com
route -n
more /etc/resolv.conf

```

If any of those fail, tell someone which command failed and whether you are using static IPs or DHCP setups.

Please.  Oh, and use code tags for all output, so it lines up and it readable.  Too hard to read otherwise.

---

### Post by jgw on 2018-10-16
I gave up on my wired connection.  Its just not right.  I moved on to wi-fi which seems to be running fine.  The wired connection kept turning itself off.  Showing me that it was up when it was not (unable to ping yahoo..com, etc.)   It got very strange.  I will make a run at it later..

---

### Post by jgw on 2018-10-17
My wired was based on d-link power connectors.  I had two sets.  I have had an av500 for some time and it worked but not too fast.  I then updated to a dhp-701av starter kit.  This connection was actually worse than the av500.  I actually drilled a hole in a wall to move the router connection in the hope of a better connection but that too didn't help and it just kept on not connecting.  Its after that that I tried the wi fi and it too wasn't great but better than the power connectors.  My problem with that is that all I had was a bunch of old wi-fi adaptors.  I think that is my current problem with wi-fi in that I do have a consistent connection but it remains close to half of what it should be.  I have ordered an extender and a better wi-fi adaptor and should strenghen the wi-fi to a point where I would have a really good, faster connection.

With the wi-fi I have tried the connection with, and without, the vpn.  That made absolutely no difference in the speed or the connection (PIA VPN).  I know there may be cheaper and better  VPN's but I have been with them for some time and its always worked.  They have actually, now, built a software package for ubuntu 18.04 that makes it all very easy to install too.  I also have usenetserver vpn which I use on some other machines which also works well, with little degredation to speed and connection.  

Anyway, thanks again for the response.  I think I will eventually be dandy if I put the right wi-fi hardware in place although I am really tempted to run a wire from the router to the other computer but I am simply too damned lazy to do it <sigh>

---

