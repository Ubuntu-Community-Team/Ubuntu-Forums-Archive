---
title: "[SOLVED] Connection issues with Compaq Evo"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by UglyShirts on 2009-01-03
Once again into the breach, my friends.

Just bought a secondhand Compaq Evo (P4 2.0) from a resale computer shop to replace a dead Presario which developed a freezing issue inherent to the hardware.  Ran into problems almost immediately. It supposedly came with a Windoze XP install...bit it was broken.  No problem, I'll just whip out the Hardy install Live CD.  The CD-ROM drive makes a grinding noise, but won't open.  Grrr.  Replace the drive with a spare.  Drop in 8.04 live CD, it spins up, and then despite spinning, freezes up at the first install window, and won't progress.  So, I pull the old HD from the dead system (which already has Hardy on it, and is not the source of the freezing issue) and drop THAT in.  

Victory!  It boots up beautifully!  Pain!  It won't connect to the internet!

A little Googling reveals two things: 1) That this particular model of machine seems to have trouble connecting in Ubuntu, and 2) any solutions anyone has found are either not shown, or are WAY over my head.  

I'm using a router and modem which are both problem-free (as THIS communication is being sent via them) and the cable is fine, too.  It worked just peachy before the old system developed the freezing issue.  
Can someone help me turn the spinning globes / exclamation point in the network connection icon into sweet, sweet internet traffic?  

Thanks in advance.

---

### Post by UglyShirts on 2009-01-03
*bump*?

---

### Post by rfruth on 2009-01-03
I have a Evo (like yours?) and have Debian (Lenny) & Ubuntu (II) on it, no problems, got it off e-bay for $ 140.00 well over a year ago, the CD ROM drive is a little flaky but other than that the sucker won't quit (not that I want it to) !  ((wired ethernet, ADSL))

[http://picasaweb.google.com/rob.fruth/Evo#]("http://picasaweb.google.com/rob.fruth/Evo#")

---

### Post by melojo on 2009-01-03
open a terminal and post the output of

```

lspci
sudo lshw -C network
ifconfig

```

This will give us more info.

if you don't have any internet on the system but a double boot save to a .txt file to the windows partition then upload it.

---

### Post by UglyShirts on 2009-01-03
> **melojo said:**
> open a terminal and post the output of

```

lspci
sudo lshw -C network
ifconfig

```

This will give us more info.

if you don't have any internet on the system but a double boot save to a .txt file to the windows partition then upload it.

Got it, thanks.  Here's the entirety of the output info:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)

 *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VM (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth1
       version: 81
       serial: 00:08:02:c2:0c:28
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

eth1      Link encap:Ethernet  HWaddr 00:08:02:c2:0c:28  
          inet6 addr: fe80::208:2ff:fec2:c28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:231626 (226.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115200 (112.5 KB)  TX bytes:115200 (112.5 KB)



```

---

### Post by UglyShirts on 2009-01-03
Desperation *bump*

---

### Post by UglyShirts on 2009-01-03
Anybody home out there...?

---

### Post by UglyShirts on 2009-01-04
This is getting a little embarrassing.  

Someone has to know SOMETHING.  Please help!

---

### Post by UglyShirts on 2009-01-04
Seriously...Did I offend someone?  Do I SMELL bad?  What?!?

---

### Post by MenZa on 2009-01-04
Have you considered the option that noone who's had a chance to look knows anything about your problem?

Give your thread some time; someone is bound to look at it after a while.

Addressing your problem, though; I find it weird that an Intel ethernet controller doesn't just work. Are you fortunate enough to have a spare ethernet controller lying around?

After a bit of Googling, I noticed several people with wireless and sound issues, who happened to have the same ethernet controller in their machine, but they didn't report any problems.

---

### Post by UglyShirts on 2009-01-04
> **MenZa said:**
> Addressing your problem, though; I find it weird that an Intel ethernet controller doesn't just work. Are you fortunate enough to have a spare ethernet controller lying around?

*Facepalm*

Duh.  I cannibalized so many parts from the old system, I have no idea why I didn't think to yank the ethernet card, as well.  Of course, I did, and now it works perfectly.  Thanks a million for the suggestion.

Apologies for my impatience, I've just routinely been spoiled coming here for advice.  You're a very supportive community, and very fast with the answers.  

Thanks again.

---

### Post by sledge73 on 2009-01-04
did you go into the bios & set the hard drive to boot as ide interface?? I had the same problem & that solved it. let me know!

---

