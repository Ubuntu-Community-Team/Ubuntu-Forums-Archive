---
title: "e1000 driver Networking Serious issues!!"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by guru369 on 2007-03-19
Hi,

I know the title seem big and "shouty" but theres a reason for it.

I am running feisty dawn on a dual boot laptop with windows XP.

My setup consist of the following:
1. The laptop Fast Ethernet card is connected to a Cisco ADSL router 837.
2. BW tests are being tested on [http://speedtest.shimi.net](http://speedtest.shimi.net)

Results:
1. Windows XP: 3Mbps.
2. Ubuntu  Feisty: 500Kbps.

Facts:
No FW enabled on neither.
The issue seems OS related. (Happens on Ubuntu Not on XP)

I would like to add that I previously had Gentoo on this Laptop and it had the same problem as Ubuntu.

I think it relates to the Interface driver but I am not sure and I don't know where to begin to check.

Test was conducted several times.

Dekel

Laptop T60 Lenovo.

---

### Post by Mr. C. on 2007-03-19
Try: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

MrC

---

### Post by guru369 on 2007-03-19
Thanks,

I followed the guide and IPv6 is disabled.

```

dekela@dekela-laptop:~$ ip a | grep inet6 
dekela@dekela-laptop:~$

```

Rebooted but the problem persists.

I must say that with Gentoo I was using a manual compiled kernel without IPv6.

Any other ideas?

---

### Post by Mr. C. on 2007-03-19
The e1000 driver has changed considerably.  Your version is probably 7.0.33.  The latest kernel, 2.6.20 contains 7.3.15-k2.  Unfortunately, change comments have been eliminated from the driver itself, so I can't quickly see what was changed.

If you can update kernels to 2.6.20, you're likely to have better luck.

MrC

---

### Post by guru369 on 2007-03-19
I think its the latest:
```

dekela@dekela-laptop:~$ uname -a
Linux dekela-laptop 2.6.20-12-generic #2 SMP Sun Mar 18 03:07:14 UTC 2007 i686 GNU/Linux
dekela@dekela-laptop:~$ 

```

---

### Post by guru369 on 2007-03-19
One important note I found.
I am having the same issue using the wireless as well..

```

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

I think this is using ipw3945 so this leads me to believe its not e1000 issue.

Something is wrong with the networking stack maybe?

Dekel

---

### Post by Mr. C. on 2007-03-19
Ok, now you've confused me.  You said you were wired, now you are saying wireless.

You're going to have to narrow this down a bit.

Are you sure this isn't a problem with your router (ie. power cycle it).

If you think this is a generic kernel issue, you'll have to test that theory by using different kernels.

How is performance in the stock kernel ? 

MrC

---

### Post by guru369 on 2007-03-19
Why are you confused?

There are 2 topologies:

PC --> Wireless Router --> ADSL Router --> WAN.

And

PC --> ADSL Router --> WAN.

In both topologies the issue is the same:
Ubuntu: 500Kbps XP:3Mbps.

I am using Ubuntu Feisty Dawn with all the latest updates. It is the default kernel selected by the installation and then updated by the update manager. I didnt compiled any kernel.

I pointed out the wireless to eiliminate the e1000 driver assumption.

p.s.:
I have power cycle the router and the wireless router a couple of times. Although I dont think thats the reason. Again: Ubuntu Slow XP Fast.

Dekel

---

### Post by Mr. C. on 2007-03-19
I understand you have two cards.  The confusion was jumping from one NIC to another, while your "big and 'shouty'" subject made clear that the e1000 driver had serious issues.  So you threw me an unexpected curve.

I'm hard pressed to believe the kernel has such a substantial networking performance problem, or others would see it as well.

I'm not sure what else to tell you.  Try narrowing it a bit more.

MrC

---

### Post by guru369 on 2007-03-19
Sorry man.
I thought it was oviouse I had 2 card as its a T60 Laptop..

My Bad.. ;-)

I hope to find a solution..
My next step is to you my other machine. (The desktop) which runs Gentoo but is connected to a different ADSL router. (I have 2 connections)

I will hook it up to the "problematic connection" and see how it goes...

I think this will definitely tell me if theres something wrong with My Laptop HW and Linux or something else..

Thanks!
Dekel

---

### Post by guru369 on 2007-03-19
Ok.. I got some results:

I moved my Wireless router to my other ADSL connection:
Laptop --> Wifi -->Wireless Router --> ADSL Modem.

BW  Test: 2Mbps (Which is expected on this connection)

So to summarize:
The happy result is that the kernel driver seem to be ok. But for some strange reason is having issues with my Cisco 876 ADSL router....

Dont know why.. I am lost here...

Can it be that the provider is BW shaping me based on OS type???
Reminder: It dosent happen with XP....

Dekel

---

### Post by guru369 on 2007-03-19
More testing:

Ubuntu Laptop:
```

dekela@dekela-laptop:~$ ifconfig eth0 | grep errors
          RX packets:20994 errors:352 dropped:7874 overruns:0 frame:0
          TX packets:19796 errors:0 dropped:0 overruns:0 carrier:0

```
Gentoo Desktop:
```

monster dekela # ifconfig eth0 | grep errors
          RX packets:3335672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2757774 errors:0 dropped:0 overruns:0 carrier:0

```

Interesting...

I have packet drops on the wireless interface...
The only difference is that the desktop is using wired and the laptop wireless..

Is that common to have drops and errors on wireless cards?

Dekel

---

### Post by Mr. C. on 2007-03-20
Receive (Rx) errors are not uncommon when there is a lot of noise at the frequencies that your wireless card is currently using.  The packets get retransmitted, but you'll see an accumulation of errors, and a loss of performance.

Use one of the wireless sniffer tools to see what channels near you are in use to find the best channel for your NIC.  Only a few channels (1, 6, and 11 in the US) do not overlap, so are the best choice if they are free.

MrC

---

### Post by chili555 on 2007-03-20
May I draw your attention to: [http://www.thinkwiki.org/wiki/Ethernet_Controllers#Intel_Gigabit_.2810.2F100.2F1000.29](http://www.thinkwiki.org/wiki/Ethernet_Controllers#Intel_Gigabit_.2810.2F100.2F1000.29)

Especially, this: > There is a known issue with the e1000, t60/t60p and the 2.6.17 kernel. It is unconfirmed if this issue effects other configurations.

This is sobering to me, because my shiny new T60 is on the way.

---

### Post by Mr. C. on 2007-03-20
Don't sweat it Chili.  You should be able to work around the issue.  Good link.

This isn't the first chip to hammer a system with interrupts.  I've seen and reported the same thing with some 3Ware RAID controllers several years back.

Many users are surprised to find their system's load increase and performance *decrease* with gigabit Ethernet, failing to account for the leap in interrupts/second and retransmits required due to saturating a smaller pipe on the other end.

MrC

---

### Post by guru369 on 2007-03-21
Guys, Thank you for the information. Its very helpfull.

However I am still puzzled.
During my tests I also connected my Laptop or another ADSL connection I have. (Reminder I have a Cisco 837 ADSL router and a ECI B-FOCUS ADSL Router )

Using my ECI connection which is 2.5Mbps I have no problems and the BW is great.

This is only a problem when I am working with the Cisco Router.

The problem happens if I work with Wireless or Wired.
But the main issue here is the Cisco Router.

Thanks,
Dekel

---

### Post by Mr. C. on 2007-03-21
Good to hear that you have this issolated.

It is time to start looking at help on the Cisco site.

MrC

---

### Post by russell.h on 2007-03-22
Could someone take a look at the following thread:
[http://www.ubuntuforums.org/showthread.php?t=388812&highlight=e1000+driver](http://www.ubuntuforums.org/showthread.php?t=388812&highlight=e1000+driver)

Was the e1000 driver built into the kernel as early as Dapper? Would this guy be better off just installing a newer kernel and/or Edgy or Feisty?

Thanks,

Russell

---

### Post by mkz on 2008-03-19
Well,

One year later ...

I'm having the same performance problems too with ThinkPad T61 and e1000 driver.

I've posted here :

[http://ubuntuforums.org/showthread.php?p=4532719#post4532719](http://ubuntuforums.org/showthread.php?p=4532719#post4532719)



Mkz.

---

