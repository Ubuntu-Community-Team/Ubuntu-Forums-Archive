---
title: "Internet only works occassionally- HELP!"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by declaration on 2006-07-26
Hi,

I am having severe problems with a new Ubuntu installation which is causing me to switch back to Windows.

Basically, when I boot up, I can only access a very few websites. A ver few (google included). The vast majority will not work.

Then, this morning after the first boot of the day, it started working properly for the first time. Then later on stopped again.

It is not an IPV6 issue. The internet works on every other PC in the house (including an Ubuntu laptop).

This issue is making ubuntu unusable for me so if you can help I will thank you for ever!

---

### Post by zxee on 2006-07-26
I think that to get more help you could provide the specifics of how you connect and what applet(s) you use to connect with.e.g dial up, dsl, broadband...and what your hardware is and the version of ubuntu you have installed.

---

### Post by declaration on 2006-07-27
Hi,

I am using a new install of Dapper. 

The internet is cable broadband and is linked to my computer (and many others) via a Linksys router. 

I don't really know what else to say- I assume all my settings are correct because the internet works sometimes (ie-now). But rest assured it won't be this evening.

The guy in the following thread seems to have exactly the same issue but there isnt a resolution in that thread-

[http://ubuntuforums.org/showthread.php?t=203384]("http://ubuntuforums.org/showthread.php?t=203384")

Could this be a hardware issue? My ethernet board is mobo inbuilt but I am willing to go buy a PCI ethernet card if anyone thinks that might help.

---

### Post by mips on 2006-07-27
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

### Post by declaration on 2006-07-27
Hi MIPS. I'll try post that info later.

For now I have had a little progress.

Previously, the only times my network would work properly were in the morning after getting up. I thought why should that be the case? Then I remembered that before I go to bed each night I switch the power to my computer off at the switch. I just booted down, stitched at the switch and booted, and guess what? my internet works. For now its just a coincidence but I'll see what happens.

---

### Post by T700 on 2006-07-27
In situations like you describe, powering down and then powering back up the router is often helpful.  Clears the cobwebs out.  :-)

Paul

---

### Post by declaration on 2006-07-28
Right, It stopped working again so I powered down, turned off at the switch and rebooted and its works now. So I think I have found a solution.


@T700- yeah I know, but the weird thing is is that the router is not in this room so I am not actually restarting it at all.

One thought- I think this might usually happen when restarting after booting my windows partition. Could this be a cause?

---

