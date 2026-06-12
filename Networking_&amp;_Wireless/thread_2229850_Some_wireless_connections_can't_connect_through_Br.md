---
title: "Some wireless connections can't connect through Browser"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by thora2 on 2014-06-15
I have 3 wireless connections where I am, and only one of them ever connected AND allowed me to browse in Firefox.  Today, that connection is not working, so now I want to connect on one of the other available wireless connections.

These 2 connections will connect and say they are connected, but will not actually browse the internet in a browser.

I have tried a number of things from other things on the forum here, but have not found anything that works.

I have deleted connections, let them reload.

Let me know what I need to provide to you so you can help me.  I am a novice but can follow instructions, and am fine using a terminal window if you tell me what I need to put in.

Thanks

---

### Post by thora2 on 2014-06-16
Can anyone help me please.  Thank you.

---

### Post by Bucky Ball on 2014-06-16
Welcome. Are you using static IP addresses set up in Network Manager?

When you say you have three wireless networks you can connect to, do you mean there are three available networks you can connect to or you have three wireless cards attached to the machine?

---

### Post by thora2 on 2014-06-16
There is a static IP here.  There are 3 networks that I can connect to, all on the same system into the building.  I do not have 3 network cards.  The owner of the building has installed 3 wireless modem/routers, so that guests can get wireless throughout the building.  I'm pretty sure that they all have the same IP.  I think I had connected to 2 different ones on the first couple days here, but I'm not certain.  But now only one of them works for internet browsing, and it's the one with the weakest, most flaky signal.  It would be good if I could use one of the others, as the signal is stronger.

I was using Network Manager, but installed WICD yesterday.  It appears to work fine.  It is no better or no worse for logging in.  I had changed hoping to resolve the problem.  It didn't make any difference.

---

### Post by Bucky Ball on 2014-06-16
As you are using a static IP, what DNS IP address are you using? If you have nothing set, obtain the DNS IPs of the ISP or try the IP of the router(s), seperated by commas and a space.

---

### Post by thora2 on 2014-06-18
Now none of the 3 available connections are allowing me to browse.  I am hardwired into one of the modems.

The people here don't have much info on the internet here, so they are little help.  So I cannot obtain some info.  It my computer can find it with the right command, then I can get it.

The recent IP that is showing when the 3 wireless connections connect are 192.168.0.119, but I can't browse with them.  I know that is different than it was a couple days ago.

I've tried other things I've seen on the internet, but still nothing is working to make them be able to browse.

I tried telling the WICD connection manager to use a variety of IP's that have showed up in the last few days, similar to the one I listed above, but I don't have some of the info it might need, such as Netmask and Gateway, but it did automatically fill those in with some numbers.  But I don't have an IP for a connection that actually connected.

Someone here has a different type of connection, and it is accepting the password provided, but gets stuck on "Obtaining an IP" and just won't grab one.

Let me know what else I can try, or how to obtain some info from my computer.[INDENT]Doing the following command I get:
     lspci -vvnn | grep 14e4
     03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
[/INDENT]
 
I am running Ubuntu 14.04.

The connection that was working, the people here physically changed the router, so I suspect that might be one of the reasons that quit working.

Thanks.

---

### Post by thora2 on 2014-06-19
Now one of the connections has decided to work again.  It appears to have the same IP as those times when it didn't work.

---

