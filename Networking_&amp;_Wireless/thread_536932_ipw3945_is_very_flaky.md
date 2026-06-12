---
title: "ipw3945 is very flaky"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by dumbmatter on 2007-08-28
I just got a new laptop (dell inspiron 1520) with an ipw3495 wireless card.  it is having a lot of trouble with my network.  most of the time it won't connect, but every now and again it does.  but it will then disconnect after a few minutes of working.

i have a linksys router and i turned off all of the security stuff, so i don't know what the problem is.  i have another laptop with an ipw2100 that can connect to the network fine (that is running fedora 7 though).

the weirdest thing is that one of my neighbors has an unprotected network, and i can connect to that one fine.  no problems whatsoever with that network.  it's just mine.  and we both have linksys routers.

any suggestions?

---

### Post by nosrednaekim on 2007-08-28
did you try moving closer to your router?

---

### Post by dumbmatter on 2007-08-28
yes i did.  the signal for my network is stronger than my neighbor's.  and, as i said, my old intel card connects to my network fine.

---

### Post by markonhismobile on 2007-08-30
I'm also having a similiar issue with my IPW3495 card, I can associate with the network and usually connect on start up but then after a few minutes (sometimes about 5 but earlier I was online for over an hour) I disconnect and the only way I've found so far is to restart!

I'm currently checking if there is anyway of getting wpa supplicant to use the ipw driver rather then the generic wext one. 

I can check my syslog after it happens and see the card disconnects then tries to re-associate but eventually times out!

---

### Post by Zorael on 2007-08-30
My issue is similar, though it only disconnects about once every two hours or so.

I found a workaround to get it running again without having to reboot, but if the computer is unattended I'm (it's) screwed.

[https://bugs.launchpad.net/ubuntu/+bug/134515](https://bugs.launchpad.net/ubuntu/+bug/134515)

---

### Post by dumbmatter on 2007-08-31
like Zorael, i have found that it connects much more reliably with a static IP address.  i'm going to try buying another router and hopefully that will fix the problem.  one of my roommates is having the same problem as me, but he uses vista.  so it's not just us linux guys with wireless problems.

---

### Post by Zorael on 2007-09-01
Best of luck to you, but mind - I've tried it with six different routers now (one old D-Link, three different Netgears of the same model, another Netgear model, and my neighbor's unprotected router of unknown make and model :-$).

I managed to obtain an USB wireless dongle (of Netgear make, can post model tomorrow if interest exists), but it (the model) is not supported at present. This gave me further incentive to try ndiswrapper, and while I managed to install it and get it to manage both the dongle and the 3945 chipset, I've obviously done something wrong as it soft locks the system if I connect it, disconnect it, or reload the ndiswrapper module (through modprobe). So the only way is to boot the machine up with it already plugged in.

At any rate, I'm growing more and more convinced that there's some hardware difference (recently introduced?) that makes it work flawlessly and out-of-the-box for some and just barely for the rest of us.

---

### Post by markonhismobile on 2007-09-01
I'm having some better luck with mine now, at the time I was having problems I was doing some quite large transfer's on my wired lan across the router (a few 100Gb's!) and the problem was also occurring in Vista (sorry!) where I would disconnect and was unable to re-connect which also lead me to look beyond the software/hardware on the laptop! Since I've finished with the transfer I've had no problems so far!

---

### Post by Zorael on 2007-09-01
Most excellent!

One last thing, though. Could you do an 'lshw -C network' and paste the output here? I'm curious as to what firmware version it reports.

---

### Post by markonhismobile on 2007-09-02
The output of lshw -C network for the wireless interface is as follows:

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:46:e9:84
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.110 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d8000000-d8000fff irq:16

Good luck!

---

### Post by blackmh on 2007-09-02
I have identical wireless card and no problems whatsoever using stock 'restricted' drivers

---

### Post by whistl on 2007-09-02
> **blackmh said:**
> I have identical wireless card and no problems whatsoever using stock 'restricted' drivers

Same here, no problems in Edgy after installing the restricted drivers from the repositories.  Installing Feisty on them loaded the drivers automatically.  This is on two different laptops, a Lenovo T60 and Acer Travelmate 8204.

---

### Post by Zorael on 2007-09-02
That's just it, I *had* no issues until I sent in the machine to be serviced, where they replaced the motherboard which includes the wireless chipset. It works fine in Windows, so the new hardware shouldn't be broken per se, but it *barely* works now in linux whereas it worked very out-of-the-box-esque earlier.

Thus, I suspect hardware and/or firmware differences.

---

### Post by dumbmatter on 2007-09-04
my new router came today and now everything works fine.  i'm still not sure what the problem was with the original router.

hopefully you guys will get your problems figured out soon.

---

### Post by hasinasi on 2007-09-10
I have the same issue here: WiFi is good for a few minutes, then gets slow and dies.

Just to throw in one more idea: In some other thread (sorry, can't find the details right now), I read that it helps to disable the wireless (killswitch) while booting. Then switch it on a few minutes after the system is up. I tried it and got good connection for a while, but still not reliable. Quite annoying. 

I am running Kubuntu 7.04 on a Dell Latitude D620 (using a 3945ABG WiFi card)
My notebook works at my office (unencrypted WiFi, unknown access point), but it has the problem at home (Netgear MR814v1 Router, 128-bit WEP). 
When I run the same laptop on WindowsXP SP2 at home, the wireless runs flawless. So it there must be a software solution. 

I also thought about getting a different router, but from some reports in this thread, it seems that this problem may exist for many routers. It could become quite expensive, though! Could everyone please post info about which routers work and which don't (Make, model, version, firmware, etc.)? This could save some bucks... 

Cheers, 
Hasi.

---

### Post by linux23dragon on 2007-09-10
> **hasinasi said:**
> I have the same issue here: WiFi is good for a few minutes, then gets slow and dies.

Just to throw in one more idea: In some other thread (sorry, can't find the details right now), I read that it helps to disable the wireless (killswitch) while booting. Then switch it on a few minutes after the system is up. I tried it and got good connection for a while, but still not reliable. Quite annoying. 

I am running Kubuntu 7.04 on a Dell Latitude D620 (using a 3945ABG WiFi card)
My notebook works at my office (unencrypted WiFi, unknown access point), but it has the problem at home (Netgear MR814v1 Router, 128-bit WEP). 
When I run the same laptop on WindowsXP SP2 at home, the wireless runs flawless. So it there must be a software solution. 

I also thought about getting a different router, but from some reports in this thread, it seems that this problem may exist for many routers. It could become quite expensive, though! Could everyone please post info about which routers work and which don't (Make, model, version, firmware, etc.)? This could save some bucks... 

Cheers, 
Hasi.

Hi

Please don't buy anything yet. It is a known kernel driver issue.
Have a look [here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg432615.html") for more information

---

### Post by hasinasi on 2007-09-21
Hi linux23dragon,
thanx very much for your advice. Anyway, I could not resist getting a NETGEAR WPN824, which was on sale at buy.com, recently (very good deal). 
I have to say I got lucky! The WiFi works flawless now. This kind of confirms my hypothesis that it was an interaction problem specific to my router/card combination. 
That said, however, I have to add that there was one modification: I had to run the old router (MR814v1) on WEP128, as it does not offer WPA. I am running the new router on WPA2. So there is also a chance that the problems were due to a problem related to WEP. I remember I read some thread suggesting such a problem. Unfortunately, I never tried my old router without WEP. :(
Anyway everything is fine now, even w/o kernel upgrade. 
Thanx a bunch. 
--hasi.

---

### Post by betchern0t on 2007-09-21
Hi,
     there are a heap of issues with the ipw3945 driver that some experience and some don't. As suggested I think there are a few different hw revisions clouding the issue. The other things I have been seeing in my research is a report that some routers work and some don't. Another variable is the protocol used 802.11b or 802.11g. There are reports that the issues go away on 802.11g. I don't know if this helps anyone.

I had a new HP nx7400 back in April. Installed Edgy using the 1.13 driver. It was doing all the  things described above. Used NDISWRAPPER. That got me a situation where it would load up, die after a few minutes. I did rmmod, modprobe and re-setup and it would work the rest of the session. Actually wrote a script to do that.

Reinstalled to feisty in the last week. Using the standard 1.20 driver with dropped packets, dying after a while etc. Compiled the latest 1.22 with the same results. So from my view, there were bugs on this behaviour reported upstream on the driver in April, and the driver still has the same behaviour five months later. I think Intel have lost interest in the driver in favour of the iwlwifi drivers since they had strong push back by the kernel team on the dicky daemon this driver requires. In the mean time a world of pain.

Cheers Paul

---

### Post by dschouten on 2007-09-25
Hey all, 

I've had very similar problems as people in this and other forums have, and I wasted the better part of my week trying to fix it. None of the software fixes seemed to work, including ndiswrapper, iwlwifi drivers, or the newest Gutsy kernel (2.6.22-12). So I reverted to my original configuration with the restricted IPW3945 driver. Then one day, my wireless just started working properly again. I have no idea why (and I am not going to argue with it), but the only things that have since changed are

[LIST=1]
[*]I set the wireless mode to G only on my Linksys router
[*]configured my CPU scaling to performance mode (using the cpufreq utility)
[/LIST]

I don't trust this newfound success because there is no logical reason for it. But if it continues to work for a couple of weeks, I might change my mind :)

Sept 25 @ 7PM PST: Now it seems like whenever the signal strength drops below around 65%, it stops working. Anything above 70% and it is very fast. Strange! I'll try a different router soon.

Cheers!

---

### Post by markonhismobile on 2007-09-26
I'm having better luck now, as the wireless only seems to drop off occasionally now it does seem better but I am having the same issue with Vista so I've been fiddling with router settings! Might try using the G-Mode only and see if this helps!

---

### Post by pompollii on 2007-10-13
I've also been tearing my hair out trying to get the 3945 to work correctly. I've tried both ipw and iwl drivers. Had some sporadic success with them. Sometimes they'll connect for no particular reason, but usually not. I also have a Netgear mr814v2 which has been upgraded to the mr814v3 firmware. I don't run WEP or any security because i can't even gt the basics to work. It is extremely frustrating because so many have reported success on this wireless device with little to no effort. If someone is interested in helping me troubleshoot, I can post ifconfig, iwconfig, and any other info that is needed.

---

