---
title: "Internet problems with Firefox."
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by yimingwuzere on 2007-01-06
I'm using an Aztech DSL600E adsl modem connected to the net with a connection made via pppoeconf.

The problem is this: After a certain period connected to the net, surfing pages on Firefox leads to "Server not found" and pages could not open. This problem seems to lie mostly with Firefox, I tested with Azureus and could still torrent, most of the time I could still message using aMSN, and I can still ping people via IP. Pinging say, google.com though would lead to an "Unknown host" problem. I cannot figure out a solution to this unless using "poff" and "pon" the conection again.

Any ideas how I can solve this?

---

### Post by Joeb on 2007-01-06
Since you can ping ip addresses, but can't access names, it sounds like dns is a problem.  DNS is what converts ip names to ip addresses.  Have you checked with your ISP to make sure they aren't having DNS problems?

---

### Post by yimingwuzere on 2007-01-06
Yes they don't have any. I tested on my xp computer and it doesn't have any issue with the Internet, apart from the slower speeds due to TW earthquake.

---

### Post by Tanchelm on 2007-01-06
have you investigated IPV6 as a possibility?

---

### Post by yimingwuzere on 2007-01-07
$ test -f /proc/net/if_inet6 && echo "ready"
ready

Seems that IPV6 is available and ready, is there anything else to check on IPV6?

---

### Post by Joeb on 2007-01-07
It sure sounds like you are losing your DNS server.  One thing to try to resolve the problem, would be to go into the networking applet under System==>Administration and hard code the DNS server.  You may have to contact your ISP to get it, though.  EDIT:  Or before contacting them, try entering the ip address of your modem as the address on the DNS tab.

---

### Post by handy on 2007-01-08
Try [_**this How-To**_]("http://ubuntuforums.org/showthread.php?t=282034"), the DNS part could solve your problem...

---

### Post by yimingwuzere on 2007-01-08
Joeb:

Okay, I keyed in the DNS servers in and saved the network configuration. But even after clicking 'Apply' after a half-hour or so I get the 'Server not found' error again and have to re-launch Networking again. Any idea how to make this permanent until I close my connection?

---

### Post by handy on 2007-01-09
> **yimingwuzere said:**
> Joeb:

Okay, I keyed in the DNS servers in and saved the network configuration. But even after clicking 'Apply' after a half-hour or so I get the 'Server not found' error again and have to re-launch Networking again. Any idea how to make this permanent until I close my connection?

Did you modify your router with the new DNS server addresses too?

---

### Post by yimingwuzere on 2007-01-09
Using an ADSL modem, I don't plan to try using it as a router.

---

### Post by handy on 2007-01-09
> **yimingwuzere said:**
> Using an ADSL modem, I don't plan to try using it as a router.

Your ADSL modem is a router too...

Look at the [_**OpenDNS how-to**_]("http://www.opendns.com/start/") get an understanding of this?

---

### Post by yimingwuzere on 2007-01-11
I can't configure it as a router despite using links from my manufacturer's page and portforward.com. Any alternatives should I not find a solution to setting it as a router?

---

### Post by maranellored on 2007-01-11
this thread  sure did help me

I use Xubuntu edgy

THANKS !!!!

---

### Post by maranellored on 2007-01-13
well i realised something.

the first two times, i restarted the comp, the open-dns addresses worked normally.
but the next time, after a bad shutdown, the dns addresses reverted back to normal and now i have to configure the stuff everytime i start the pc.

Please help me

---

### Post by handy on 2007-01-14
You have to reconfigure even after you have done the  prepend DNS routine as mentioned in the [How-To]("http://ubuntuforums.org/showthread.php?t=282034")?

---

### Post by maranellored on 2007-01-15
yes, i did exactly as was mentioned in the guide.

i removed the # and changed the line to **prepend domain-name-servers 208.67.222.222, 208.67.220.220; ** in the **/etc/dhcp3/dhclient.conf** file

i even changed the DNS addresses in my router.
i use a Huawei SmartAX841.

---

### Post by yimingwuzere on 2007-01-15
My modem's for some reason always unsuccessfully makes connections to the ISP while configured as a router... wierd. It didn't happen when I borrowed a friend's identical router as it worked normally.

I guess I got to save a location in my Networking tool with the DNS addresses keyed in? Or is there another solution without router configuration?

---

### Post by handy on 2007-01-15
My limited understanding says that the only reason these problems exist is because the  router's  are built really cheaply.

So, as far as consistancy is concerned? ...

Forget about it!

---

### Post by handy on 2007-01-15
That's not a total cop out, it's just a; *well thankfuly other people know stuff too* thing...

What are forums for?

---

