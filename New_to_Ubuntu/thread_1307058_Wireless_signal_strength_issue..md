---
title: "Wireless signal strength issue."
date: 2009-10-30
forum: New to Ubuntu
---

### Post by mattweed9 on 2009-10-30
I own a Gateway nv5214u notebook, and I have been using Ubuntu 9.4, which I installed using the Wubi installer, for about 3 weeks. I like the OS very much and thanks to all who help make it possible. I updated to Ubuntu 9.10 yesterday, which I liked even more. I noticed though, when I run Ubuntu my wireless signal is, nearly half if not more, weaker. I was really hoping it was because I wasn't running the full install so today I wiped my hard drive clean and installed 9.10 as the only OS. Unfortunately, my problem still remains. I understand that Ubuntu is not Windows, but this is the only problem holding me back from giving Windows the finger and learning to make the change and discover a new way to compute.

So, I looked and looked for about two weeks. Reading google search after search looking for a answer to this problem in my spare time. I can't seem to find or figure out how to get a better signal from my router. I am hoping it is possible

So here are some spec's.

OS - Ubuntu 9.10 64 bit full install

Processor - AMD Athlon™ 64 X2 QL-64 Dual-Core Processor (2.1GHz, 667MHz FSB, 1MB L2 Cache)

wireless - Atheros Wireless 802.11a/g/n

D-link wbr 2310 wireless router

Other then the Wireless issue, I am very please and amazed at how well Ubuntu installed and seems to work so well with my hardware with out any real effort or tweaking. I really hope it is just something I missed or overlooked and it can be resolved.

 Right now I get a signal strength of between 20%  and 60%. and it changes between those constantly. When I first run the computer and everything loads, I get a signal of 90% - 100%, but then it just loses it from there and remains weak.

Thanks for any help,
                       Matt Weed.

---

### Post by phillw on 2009-10-30
> **mattweed9 said:**
> I own a Gateway nv5214u notebook, and I have been using Ubuntu 9.4, which I installed using the Wubi installer, for about 3 weeks. I like the OS very much and thanks to all who help make it possible. I updated to Ubuntu 9.10 yesterday, which I liked even more. I noticed though, when I run Ubuntu my wireless signal is, nearly half if not more, weaker. I was really hoping it was because I wasn't running the full install so today I wiped my hard drive clean and installed 9.10 as the only OS. Unfortunately, my problem still remains. I understand that Ubuntu is not Windows, but this is the only problem holding me back from giving Windows the finger and learning to make the change and discover a new way to compute.

So, I looked and looked for about two weeks. Reading google search after search looking for a answer to this problem in my spare time. I can't seem to find or figure out how to get a better signal from my router. I am hoping it is possible

So here are some spec's.

OS - Ubuntu 9.10 64 bit full install

Processor - AMD Athlon™ 64 X2 QL-64 Dual-Core Processor (2.1GHz, 667MHz FSB, 1MB L2 Cache)

wireless - Atheros Wireless 802.11a/g/n

D-link wbr 2310 wireless router

Other then the Wireless issue, I am very please and amazed at how well Ubuntu installed and seems to work so well with my hardware with out any real effort or tweaking. I really hope it is just something I missed or overlooked and it can be resolved.

 Right now I get a signal strength of between 20%  and 60%. and it changes between those constantly. When I first run the computer and everything loads, I get a signal of 90% - 100%, but then it just loses it from there and remains weak.

Thanks for any help,
                       Matt Weed.


hi Matt,

Welcome to the forums,

Now, I guess I should say this really quietly ....

>>> come here .....
>>> whispers into ear ... Signal strength monitor in ubuntu doesn't really work.... The tech guys are more concentrated on getting all the different wireless systems to work, the little bar that goes up & down is not top a priority.

:D

I can sit next to a commercial wi-fi broadcast unit (as in on the same desk) and i only get 3 out of 5 bars ....   As long at it shows connected, you're okay 

Phill.

---

### Post by Jakey_TheSnake on 2009-10-30
Go to a speed test website and check what kind of download speeds you can pull with each, and use that to compare. 

Not to mention, even if the bar did work, it's not comparable as the windows bars would work on a completely different scale etc >_>

---

### Post by coolbrook on 2009-10-30
Have you experimented with the channels on your router?  I have 2-3 decent ones and test them from time to time through terminal.  What Ubuntu could use is an application with GUI similar to InSSIDer for Windows.

---

### Post by mattweed9 on 2009-10-30
[B]Cnet say's

1761.7 Kbps - You 

Is this poor? I am with comcast high speed. And I am suppost to have a upgraded version for faster speeds.

Also, thanks for the info. Wish I would of found that out a little sooner, but "does the signal meter even work?" was never one of my searches. 
[/B]

---

### Post by isee on 2009-10-30
phillw

Thanks very much!  I was too wondering why Ubuntu seems to have such a weak signal from my router which is about 10 feet away.

I'd like to take this opportunity to say that when I had XP on this laptop, for some reason the signal ( i know that is not the geek way to describe it) would be completely lost, and to get wireless access to my laptop I literally had to reboot my router.  I bought a cheap d-link, so considered it my fault for buying a crappy piece of hardware.

Ubuntu has not had that problem with my router at all.  Not once, since I've installed Ubuntu, have I had to reboot my router, wereas it was a daily task with XP.  I dunno why.   So that makes me understand it was a Microsoft fault.

Just my experience.
Cheers!

---

### Post by phillw on 2009-10-31
> **coolbrook said:**
> Have you experimented with the channels on your router?  I have 2-3 decent ones and test them from time to time through terminal.  What Ubuntu could use is an application with GUI similar to InSSIDer for Windows.


Hey !!

That's a real good point .... look at what channels the neighbours are broadcasting on (the default ones), alter yours to, say #3 or #5 .... 

Crikey, An excellent point, thanks for reminding me :D

Phill.

---

### Post by mattweed9 on 2009-10-31
> **coolbrook said:**
> Have you experimented with the channels on your router?  I have 2-3 decent ones and test them from time to time through terminal.  What Ubuntu could use is an application with GUI similar to InSSIDer for Windows.


No I haven't, This is the first laptop I have ever owned, so I am new to all this wireless stuff. And what do you mean by the last sentence? What GUI APP?

---

### Post by phillw on 2009-10-31
> **mattweed9 said:**
> No I haven't, This is the first laptop I have ever owned, so I am new to all this wireless stuff. And what do you mean by the last sentence? What GUI APP?

GUI APP = Graphical User Interface  APPlication

(Tech way of saying a programme that uses a window, mouse, touchpad etc for displaying what it is doing & little areas to enter information in)

You will also read about "Command Line / Terminal Stuff" - That's when you have a 'blank screen' and type instructions into it.

You get the command line by clicking on the little black box with the  >_ in it. You may see it being used to instruct people to type something in that cannot be done with the 'pretty' windows;)

e.g.

```
uname -a
```

or, for when you're having a bad day ...

```
who am i
```

When you're done playing in the terminal 

```
exit
```

puts it away for you. - Follow my link on Info to get some stuff on the inner workings of linux.

Phill.

---

### Post by mattweed9 on 2009-10-31
I understand the terminal, I used MSdos back in the day. Not that they are alike exactly, but I am not new to manually entering command lines to get results.  As far as all the commands, I haven't learned them yet. And the GUI question was my bad, I should of known better.

The issue isn't just the "pretty" wireless signal display. Whether that thing works or not, my wireless connection is bouncing up and down. It will peak between 1.7mb and 2.5 mb  for around 20 seconds, then it drops quickly down to 0 kbs and then back up slowly to it's peak. I've tested it with a Torrent client and with direct downloads from multiple sites. Unless everything else is jacking up for the last three weeks, there seems to be a wireless issue. Whether or not it just me, I don't know, but judging by the amount of new topics I've seen posted with wireless issue's, I doubt it.

So back to my original question, is there anything I can do to fix this?

```
mobile@mobile-laptop:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Acer Incorporated [ALI] Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
mobile@mobile-laptop:~$ 

```

---

### Post by NJ0E on 2009-10-31
Mattweed...

Something else to understand.  You pay your IP for up-graded download speed.  Basically a bigger hose to you.  That only goes to the first device that you have -- your router.  From there it will only be as big as the SMALLEST hose you have -- right now your wireless is small.  This will be true no matter what size "hose" you have comming into your house.

I apologize for not having a fix on your router issue.  Can you use a Cat-IV cable?

---

### Post by h0rnman on 2009-11-01
Mattweed,
     Perhaps you could try changing the channel that your wireless is connecting on.  In the research that I have done on a similar issue (that I am still not sure is fixed), it appears that using channels 1,6, or 11 will yield the best results, especially in a crowded or noisy (from a RF perspective) area.  Ultimately, a combination of experimentation and theory states that channel 1 would be the most ideal, unless you have one or more other routers in range that use it...then go to either 11 (good) or 6 (better).  
Also, I have noticed that if you have a compatible router, installing 3rd part firmware (DD-WRT or the like) that allows you to boost your router's signal strength is also something that can go a good way towards getting a better signal.  Also remember that NJ0E's explanation is *technically* correct, but in this case, your router should be supporting more than 20kbps throughput, unless you have an ancient ISDN line or really bad DSL/Cable service.

---

### Post by mattweed9 on 2009-11-01
The router is a d-link wrb2310 it's not that old. When using Windows, the signal is normal. I know it's not my hardware or router. It is probably a settings issue or driver issue. Like I  have said, this is my first laptop running Ubuntu. I am not a expert on either. I have tried searching for help topics, but there is so many, it can tend to make your head spend. You could spend hours and hours reading through them, just to find out that it doesn't apply to your issue. Which I have done time and time again.

In another section of this forum, it seems this is just a issue with Ubuntu and laptops. Sometimes, people can figure out what it is they need to do and fix it, other times it seems you just have to deal with it until either you, or somebody else figures it out. I was hoping this was a well addressed issue, and that it would be something simple that I over looked, but as it seems, you just have to keep trying and tweaking things until it works just right for you and your pc.

---

### Post by h0rnman on 2009-11-03
In that case, can you copy/paste the results of:
```
sudo iwconfig wlan0
``` 
or whatever your wireless connection is named - you can use iwconfig with no arguments to find out.
There may be something in there that gives a clue towards what is happening.

---

### Post by tristan8276 on 2009-12-09
Hello, I've posted in another thread as well.  I live in a guest house and in WinXP I have one to two bars of signal strength, plus showing eight to ten other networks in my area with varying strength.  In Ubuntu 9.10, I get no signal at all.  
 
I'd like to preface this by saying that I did not choose Ubuntu looking 'pretty windows'.  I'm looking for functionality.  I've heard that 9.04 doesn't have this issue, or it's at least not as pronounced.  I also understand that the developers have other things on their mind of higher importance than helping those with wifi get connected.  Although, I'm not sure if that fact puts me more at ease or not.  
 
The interface works and shows up in iwconfig and ifconfig as up and running, so i know it's not a compatibility issue. 
 
All I'm asking for is at least a starting point so that I can try it and report back the results here.
 
Thanks in advance.

---

