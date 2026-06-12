---
title: "No network devices found"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by dtmnuclear on 2005-08-28
Hello all, 

Right off of the bat, I admit I am a newbie to Ubuntu, and well, Linux in general.  After recieving the cd (v. 5.04) I installed it on a Gateway m460 (new) laptop.  I noticed that when installation was complete, there was a red strike-through over the Network Connections icon.  Single left-clicking on it yielded an error prompting me to contact my network admin. about there being "No network devices found."  This floored me, seeing as how I knew there were devices to be found!

Following this, I went into the configurations menu (under network connections) and tried configuring and activating eth0 (my ethernet connection) and eth1 (my wirless connection).  This went off without a hitch, barring the fact that my internet still didn't work, and Ubuntu still did not recognize the devices.  

Figuring that I was a newbie and could use the seasoned advice of those (far) smarter than myself, I came to these forums in search of an answer to my quandry.  I foudn the command (and I don't recall it now) to list my cards, and in fact, the terminal listed that I indeed had:

Network Controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
Ethernet Controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)

In addition to this, when I boot/shutdown the computer, configuring/deconfiguring network interfaces always registers FAIL.

I know this is not a hardware problem to the extent that prior to switching from XP these items functioned properly.  After fouraging through these forums for 2 long nights, I decided to post my own thread (and here I am).

So if you have any suggestions, please please please help me!

I thank you for your time and consideration in this matter!!! ]

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=dtmnuclear]Hello all, 

Right off of the bat, I admit I am a newbie to Ubuntu, and well, Linux in general.  After recieving the cd (v. 5.04) I installed it on a Gateway m460 (new) laptop.  I noticed that when installation was complete, there was a red strike-through over the Network Connections icon.  Single left-clicking on it yielded an error prompting me to contact my network admin. about there being "No network devices found."  This floored me, seeing as how I knew there were devices to be found!

Following this, I went into the configurations menu (under network connections) and tried configuring and activating eth0 (my ethernet connection) and eth1 (my wirless connection).  This went off without a hitch, barring the fact that my internet still didn't work, and Ubuntu still did not recognize the devices.  

Figuring that I was a newbie and could use the seasoned advice of those (far) smarter than myself, I came to these forums in search of an answer to my quandry.  I foudn the command (and I don't recall it now) to list my cards, and in fact, the terminal listed that I indeed had:

Network Controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
Ethernet Controller: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet (rev 03)

In addition to this, when I boot/shutdown the computer, configuring/deconfiguring network interfaces always registers FAIL.

I know this is not a hardware problem to the extent that prior to switching from XP these items functioned properly.  After fouraging through these forums for 2 long nights, I decided to post my own thread (and here I am).

So if you have any suggestions, please please please help me!

I thank you for your time and consideration in this matter!!! ][/QUOTE]
In order to gather some diagnostics, I am going to ask you to open up the terminal program (Applications -> System Tools -> Terminal) and enter a few simple commands.

Aslo, it would be extremely helpful if you could describe the physical network connections for your computer.  Is it plugged into a router?  Direct connection to the Internet?  You mentioned you have two network interfaces-- what do they connect to (or transmit to in the case of the wireless one).

In the terminal, please type in the following commands:
```

$ ifconfig -a | tee interfaces.txt
$ route | routes.txt

```
The first command will produce information about each of your network interfaces.  You will see this info on the screen, and it will also be saved to the file "interfaces.txt"
The second command will display your system routing table and save it to the file "routes.txt".  The routing table tells your computer where it should send data on your network so it will ultimately arrive at its final destination.

Note that both commands use the pipe (|) symbol, which for US keyboards is typically a shifted backslash.

If you could post the output of those files here, it would help considerably.

---

