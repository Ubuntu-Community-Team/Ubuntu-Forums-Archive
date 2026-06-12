---
title: "Integrated eth adapter not working on Feisty"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by zorranco on 2007-05-31
Hello community.

I've read the forums deeply finding no answer for this issue.

I've installed Feisty after a format on a box that, when using Edgy, had no problems with the net.
Now with 7.04 I have a very very strange problem:

I configure the net as in XP (in XP works like a charm, so we can discard hardware problems)

Surprisingly, the leds from the ethernet adapter doesn't appear lighted, neither link or transfer, although I can make pings to public IPs (to the DNS of my ISP, for example).

When I try Firefox, I can't surf the web (it stucks on "Looking for..."), but downloads from synaptic are available.

The motherboard is an Asus commando. The ethernet adapters are Marvell Yukon.

Any suggestions would be apreciated.

---

### Post by spd106 on 2007-05-31
Can you use a live cd to test the network card? It might be a kernel problem as you said it worked fine on Edgy. It would also be useful if you could provide more specific information about the network card. 

The output of the following commands would be useful.
```
lspci
``````

sudo lshw -class network
```

---

### Post by stoian on 2007-05-31
i think you have a hardware issue, my ubuntu installations (dapper thru feisty) worked fine with the builtin ethernet adapter.

if you're talking about wireless - then you're not alone :(

[http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem](http://digg.com/linux_unix/Ubuntu_devs_for_God_s_sake_please_fix_the_wireless_problem)
[http://ubuntuforums.org/showthread.php?t=459665](http://ubuntuforums.org/showthread.php?t=459665)

---

### Post by psychoelf on 2007-06-02
My ethernet has been acting flaky too since downloading the latest updates for Feisty.  My connection is going out randomly.  Please note that this is a hardwire connection, NOT wireless.  It works fine in XP and worked fine last night before the updates.   I am running an IBM T30 laptop.  I do have an Aironet miniPCI wireless card installed, but haven't had the chance to see if thats still working right since the update.

Update:  kernel 2.6.20-16 seems to be the issue, I think.  When I select 2.6.20-12 it works fine.  Bummer.

Update 2: kernel 2.6.20-12 is doing the same thing, just didn't notice as fast.

I know its not my internal ethernet port as it still works fine under XP.

HELP!

---

