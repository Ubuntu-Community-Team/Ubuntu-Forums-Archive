---
title: "How can I disable IPv6 to speed up my Internet in UBUNTU 11.04?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by coneill659 on 2011-06-08
I am a complete newbie
How can I disable IPv6 to speed up my Internet?
I have been looking through different terminal codes to enter and haven't found any instructions that disable IPv6 among the instructions available though a google search.

---

### Post by hatalar205 on 2011-06-08
> **coneill659 said:**
> I am a complete newbie
How can I disable IPv6 to speed up my Internet?
I have been looking through different terminal codes to enter and haven't found any instructions that disable IPv6 among the instructions available though a google search.

Look here 
[http://ubuntuforums.org/showthread.php?t=87798&page=16](http://ubuntuforums.org/showthread.php?t=87798&page=16)

---

### Post by iansane on 2011-06-08
Not sure if setting the system to ignore ipv6 really turns it off or if that would in some way still be affecting network speed but you can set this in the network manager.

left click on the network indicator icon, choose "edit connections", then choose your connection under wired or wireless and go to the IPv6 tab. There is a drop down where you would choose the method of connection and one of the options is "ignore". At least that how it is in 11.04

Not sure about terminal other than looking at your /etc/network/interfaces file but mine doesn't reference the eth0 connection like it used to on older dist.'s It only says 
auto lo
iface lo inet loopback
??? used to specifically refer to the eth0 connection.


My mistake, I was thinking system wise. I did not know firefox was trying to use it anyway. Gonna go disable mine in firefox, swiftfox, and chrome if they are on and see if that helps my speed

---

### Post by lemming465 on 2011-06-08
> I am a complete newbie
Well, welcome to Ubuntu.  Are you new to computers, to Linux in general, or to the Ubuntu distribution in particular?

> How can I disable IPv6 to speed up my Internet?
"Internet" is a fuzzy concept; I'm going to assume you mean "I want the firefox web browser to connect faster to servers".   It's not necessarily the case that any slowness is due to the mere coexistence of IPv6 transport and IPv4 transport on the same network.  Problems with overloaded ISP DNS servers are more common, in fact.

Do you get a different result from ```

time dig ipv4.google.com A
time dig ipv6.google.com AAAA
```

If the real time (wall clock elapsed) time for either of those is over 0.3 seconds, maybe you should add a local DNS cache such as *dnsmasq*.


You don't mention if you are in multiboot situation or if there are other devices such as PC's running windows around; do all devices and/or operating systems see the same slowness, or is it the case that Ubuntu Linux is noticeably slower than say Microsoft Windows XP on the same hardware? If booting a different OS changes the speed, the odds of an IPv6 problem increase.

> I have been looking through different terminal codes to enter and haven't found any instructions that disable IPv6
The [Ubuntu wiki page for IPv6]("https://wiki.ubuntu.com/IPv6") links to a rather out of date [community help page]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") on the topic.

There are a variety of things you can do to discourage IPv6.  This week I like:

* specifically for Firefox, visit *about:config*, filter on something like "dns" or "v6", and change network.dns.disableIPv6 to "true" (right click and pick "toggle").

* for GUI joy, click on your network icon (ethernet double arrow or wifi fan) and pick "connection information".  If the active connections don't say IPv6 ... ignored" click again, pick "edit connections ...", select the ethernet ("auto eth0") or wifi (wlan0?) connection you are using, and push the "edit" button.  The rightmost tab will be IPv6, set the dropdown to "Ignore".

* for instant and permanent command line gratification, edit /etc/sysctl.conf,
append a line ```
net.ipv6.conf.all.disable_ipv6=1
``` and run *sysctl -p*.  E.g. open a terminal window and run (type + press enter)```

sudo nano /etc/sysctl.conf
sudo /sbin/sysctl -p
```

---

### Post by iansane on 2011-06-08
Wow that did make a difference on my website access speed. Maybe it works for you conniel659

You should def try that command for time dig posted by lemming465.

Mine shows almost triple the time for IPv6 over IPv4 even though it's only 102msec.

Still this did make a difference. Had to disable it in FF and then it got faster and so did Chrome(thinking chrome uses the FF engine on ubuntu?)Chrome doesn't have a about:config of it's own. Swiftfox already had IPv6 disabled in about:config (probably part of the tweaking that makes it swift :-))

---

### Post by lemming465 on 2011-06-08
The firefox config change affects whether or not firefox makes DNS queries for IPv6 AAAA records, or just for IPv4 A records.  The underlying OS and network situation might or might not have v6. enabled.

Chrome is based on webkit (think Apple Safari) with a google javascript implemention, plus maybe a built-in flash engine, and basically shares no code with Firefox at all.  Chrome now sports a 300 millisecond fallback where if it isn't getting quick joy on an IPv6 try, it will start a second IPv4 connection try in parallel, and then pull the web page using whichever finished connecting first.

DNS uses a lot of caching, so time differences have to interpreted cautiously, e.g. if a v4 A record is in-cache but a v6 AAAA record is not, someone has to go look it up.  If you are seeing big differences, try a few more variants like A and AAAA queries for ipv6.he.net (dual-stack; it has both), or [www.facebook.com](www.facebook.com) versus [www.v6.facebook.com](www.v6.facebook.com).

---

