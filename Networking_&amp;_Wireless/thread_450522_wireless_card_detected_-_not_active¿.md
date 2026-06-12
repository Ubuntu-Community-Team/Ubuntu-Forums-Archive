---
title: "wireless card detected - not active¿?"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Korrontean on 2007-05-21
Hi there,

I'm trying to setup Ubuntu 7.04 on my Acer Aspire 3500 laptop. It was working well in Ubuntu Dapper Drake.

I installed NDISwrapper and the appropiate Windows driver. The NDISwrapper accepted the correct .inf file, and therefore there is a "wireless connection" in System/Administration/Network (that was not there before).

However, when I open NDISwrapper, there is a  message on the left: "Hardware present: no".

If I type iwconfig, my wireless card doesn't appear (which should be listed as "ath0").

If I type lshw, the output corespondent for my wireless card is:

>  *-network:1
             description: Wireless interface
             product: AR5005G 802.11abg NIC
             vendor: Atheros Communications, Inc.
             physical id: b
             bus info: pci@00:0b.0
             logical name: wlan0
             version: 01
             serial: 00:0e:9b:cf:da:48
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=,01/10/2004,4.0.0.14001 latency=128 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
             resources: iomemory:e2010000-e201ffff irq:22

Any ideas? THANK YOU VERY MUCH :):):)

---

### Post by Kobalt on 2007-05-21
I think once you have activated your card with ndiswrapper you should go to System > Admin. > Restricted Drivers Manager and from there activate "Atheros Hardware Access Layer". 

PS: also make sure to have the linux-restricted-modules-generic package installed.

---

### Post by Korrontean on 2007-05-21
Thank you, Kobalt! (or should I say Tintin?)

Mmm... I've made a step forward. It was my mistake, as my previous version of Ubuntu listed my wireless card as "ath0" I was looking for desperately. It's now "wlan0". OK, my card is working now!!! :p:p:p

However, I have a new problem: even if now my system can now detect the connection, and I select all the right options, password, etc. (I'm quite sure they're right) in wlassistant, I have no way to get an IP address.

I'm afraid it could be a Linux problem, as I used to have same problem a few months ago with another wifi connection where everyone but my could connect.

Any ideas? THANKS ;)

---

### Post by Korrontean on 2007-05-21
Don't worry, problem solved: I had click on "shared key" when I should've done it on "open system". 

I thought "open system" was for networks without a password.

So.......................finally I got my Feisty Fawn running PERFECT now.

One day and a half (basically screen resolution and wireless connection) of frustration lead to the greatest joy.

=D>=D>=D>:guitar:=D>=D>=D>

I wish I could make a guide for future Aspire 3500 users. However, I never realize which of the actions I've taken has actually led me to the solution. This is kind of sad :(

---

### Post by Kobalt on 2007-05-21
Glad I could help you out ;)

---

