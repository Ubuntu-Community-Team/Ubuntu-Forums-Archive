---
title: "NOOB with not so NOOB WIFI going idle problem - howto set NIC to Full Duplex"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by jal301 on 2009-07-10
I have been searching for an answer for my wireless connection going idle for 15+ seconds, then coming back, going idle, coming back, etc., etc. etc.

Problem is, I *believe* at times that I've found an answer, but I don't always know enough to navigate through Ubuntu to execute the solution so I remain stuck and am looking for somebody who will be willing to walk me though steps when I need.

Ok, problem is that I have both a D-Link Router (DIR-615 wireless N router) and Wireless card (DWA-542 N adapter) on my desktop computer.  As stated before, my wifi connection goes idle while a wired connection keeps with no problems.

I spoke with D-Link technical support and ultimately they told me that I need to go Full Duplex versus Half Duplex.  So, I ran sudo mii-tool -wlan0 from the terminal window which produced the following:

```
mii-tool: invalid option -- 'a'
mii-tool: invalid option -- 'n'
mii-tool: invalid option -- '0'
usage: mii-tool [-VvRrwl] [-A media,... | -F media] [interface ...]
       -V, --version               display version information
       -v, --verbose               more verbose output
       -R, --reset                 reset MII to poweron state
       -r, --restart               restart autonegotiation
       -w, --watch                 monitor for link status changes
       -l, --log                   with -w, write events to syslog
       -A, --advertise=media,...   advertise only specified media
       -F, --force=media           force specified media technology
media: 1000baseTx-HD, 1000baseTx-FD,
       100baseT4, 100baseTx-FD, 100baseTx-HD,
       10baseT-FD, 10baseT-HD,
       (to advertise both HD and FD) 1000baseTx, 100baseTx, 10baseT

```

So it appears as though this tool is not available or not accessing my setting correctly.  Is there somewhere else further I can take this tool to help me get to the solution?  Or, maybe you could just help me set my adapter to Full Duplex?  How is this done?

Then, I found that another user suggested setting the MTU value to the same as the router (from the default 1500).  When I contacted D-Link tech support, they suggested changing it within the router to 1472.  But when I run the code ifconfig wlan0 mtu 1472 I receive the following:

```
SIOCSIFMTU: Operation not permitted
```
per:
[http://ubuntuforums.org/showthread.php?t=1193107](http://ubuntuforums.org/showthread.php?t=1193107)

Next, I found the following page with what I believe may be a solution, however I am not able to follow what the users are saying in order to even get a start towards a solution.  If you are able to walk me through, please let me know.  Thank you
Josh

[http://ubuntuforums.org/showthread.php?t=578744](http://ubuntuforums.org/showthread.php?t=578744)

---

### Post by LewRockwell on 2009-07-10
I had some problems with wireless on a netbook and after I experimented with some of the advanced settings on both the router and netbook(including rebooting both) I eventually got it working but couldn't point to exactly which procedure ultimately achieved success.

---

### Post by superprash2003 on 2009-07-10
you mean your connection drops out at times?

---

### Post by jal301 on 2009-07-10
No, my connection actually does not drop.  The connection will maintain itself during the whole time, but all transfers will stop.  If I bring up System -> Administration -> Network Tools I can view the connection which shows it as being connected, but the State on the Devices tab will go from Active to Idle, then back to Active again.  D-Link tech support stated that they believe that I must change some settings for my adapter from Half Duplex to Full Duplex, but they were not able to help me since they didn't have Linux knowledge, and I'm not certain how to do it, either.

> **superprash2003 said:**
> you mean your connection drops out at times?

---

### Post by LewRockwell on 2009-07-10
I think it is dropping out and that it only appears to continue to be connected due to the time-frames involved in the problem and the refresh rate of various devices/software

We know your router is functioning properly via wired connections so we'll only be looking at the wireless side of the router interface set-up/administration areas

You'll need to go through these screens one by one and familiarize yourself with each of the settings, what the default is(or should be), and what each of the different selections does differently

Same goes for your wireless card in your computer

If you have a good memory you can probably get by without taking notes, otherwise they are a simple solution to the alternative frustration of "going back there to check it out once again...and then...just one more time"(old-timer's syndrome is hell I tell ya)

If I had the same equipment then I'd try to be of more assistance

At least you should know that...like Red Green and all Possum Lodge Members...we're pullin' for ya!

[http://www.imdb.com/title/tt0101177/quotes](http://www.imdb.com/title/tt0101177/quotes)

.

---

### Post by The Cog on 2009-07-10
I can't help you with the actual wlan problem, but I can see the problems with the commands you posted:
[B]
sudo mii-tool -wlan0[/B] is wrong. The interface name shouldn't have a - sign at the front. The program is trying to interpret wlan0 as a series of option switching characters.

**ifconfig wlan0 mtu 1472** needs the word sudo in front. It is an operation only allowed by root.

---

