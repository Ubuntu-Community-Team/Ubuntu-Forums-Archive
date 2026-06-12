---
title: "Continuous network activity"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Jacdeb6009 on 2009-11-05
Hi there,

A couple of days ago I noticed a very strange thing on my notebook computer.  The machine had just been booted and was sitting idle, but conky showed regular continuous network activity.  I then opened the System monitor and what was going on is shown in the attached file.

Some background.  The machine is a Dell Vostro 1400 and I was originally running Windows XP and Ubuntu 8.04 LTS as a dual boot.  A while ago (probably about 2 months) I trashed the XP installation and since then have run only Ubuntu.

I connect to the Internet at home via an ADSL line using a D-Link Airplus Extreme router (using either wireless or ethernet, dynamic IP allocation).  At work I connect to a LAN which gives me internet access as well as access to two printers in the office (both on IP ports).

The problem occurs in both situations.  I run Firestarter, but in its standard "as installed" configuration.  I have checked the machine's "visibility" using GRC's Shields Up website and in both scenarios (office and home) the machine, according to GRC, is totally invisible (this courtesy of the ISP, since the results are the same with or without Firestarter running).

I am mystified as to what this activity is, but it is also a concern as this is racking up lots of network traffic which costs me money (at least at home).  Considering that the machine is online more or less permanently, this gets to be quite substantial.

I really do not know where to start looking for the problem. Looking at the processes running under the system monitor does not reveal anything strange to me, but then I am no expert.

I would appreciate some ideas on what this could be and also some guidance in tracing the problem and correcting it.

Many thanks!

Jac

---

### Post by zaphod777 on 2009-11-05
That amount of network activity is negligible it is probably just talking to your router. 

Try keeping that window open for a day and see how much data it transmits.

1,024 kb = 1 MB
1,024 MB = 1 GB

if you are really worried you can install a packet sniffer to see what it is really doing.

I have never used one in Linux but a popular one is eathereal it looks like they have a linux client. 

there may be a native ubuntu one i'm not sure.

I am willing to bet it is just some arp broadcasts or checking a time server or some thing.

---

### Post by ukripper on 2009-11-05
you can look active/established connections using below command
```
sudo netstat -nat
```

---

### Post by 3rdalbum on 2009-11-05
I saw this problem happening on a friend's computer, back when Ubuntu 8.04 was the absolute newest distro around. The odd activity was absolutely untracable.

The machine also had trouble with a very slow wifi connection, using an Atheros chipset.

Eventually I upgraded her to Ubuntu 8.10 and this solved the wifi problem and stopped the unusual traffic. I believe the traffic was the wireless card talking to the router, having to be especially chatty in order to maintain a connection using the bad driver.

In short, try upgrading, or install a later wireless driver.

---

### Post by Jacdeb6009 on 2009-11-05
Thanks Zaphod 777 and ukripper,  I have turned off all the services that I can "see" (time sync, weather, etc.) but it's still there.  Every 20 seconds there's a "blip"  Odd.

3rdalbum,  this is a new problem.  I have had Hardy on this machine since about a week after it was released, but I have not seen this before.  It only showed up about a week or two ago.

Unfortunately 8.10 and 9.04 were not an option for me since in the latter the graphics were all screwed up (yes, "that" Intel problem) and in the former the sound was a nightmare (Skype is essential to what I do).

I will get around to installing 9.10 on a test basis, but this will take a while since the machine is used for work.  BTW, the problem appears irrespective of whether I am using ethernet or wireless and even with the wireless turned off and in a building where there are no wifi connections available... don't quite get it.  Will look at using a packet sniffer.

Thanks!!

---

### Post by ukripper on 2009-11-05
> **Jacdeb6009 said:**
> 

Unfortunately 8.10 and 9.04 were not an option for me since in the latter the graphics were all screwed up (yes, "that" Intel problem) and in the former the sound was a nightmare (Skype is essential to what I do).



i have Dell Vostro 1400 too and am running 9.04 without any problem, even using compiz on it. Can you describe what problem you are facing with intel card? i am using 9.04 since beta with no issues on vostro 1400 at all.

---

### Post by Jacdeb6009 on 2009-11-05
Hi there ukripper,

Regarding your question about the Intel graphics and 9.04, as follows.

After the initial install, I could not get Compiz to work.  Even the Gnome desktop with extra visual effects would not work.  After trawling various forums I eventually found a way to get Compiz to work.  For whatever reason it was slow and did not behave as well as it did with 8.04.  To add to the frustration it would crash quite frequently, leaving the desktop in a mess.

I was in Indonesia at the time at the end of a pretty slow and unreliable satellite based internet connection (don't ask).  The net result was that trying to get it all working to my satisfaction just became an immense frustration.

As I was running 9.04 on a separate partition and use 8.04 for work, I eventually just got too frustrated and gave up.  I am now back in Vietnam and will definitely be giving 9.10 a try in the next couple of weeks.

I also need to build myself a desktop machine so that I can play with the various distributions without affecting my work.  I run only 8.04 on the Vostro at the moment and it is my work machine so I cannot really afford any mishaps... :)

Thanks a lot for your interest and inputs!!

Best,

---

### Post by ukripper on 2009-11-06
On vostro 1400 I had to enable compiz forcefully in 7.10, 8.04, 8.10 and 9.04 using below command:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

The Intel Graphic Card (965GM chipset)is blacklisted by default for Compiz in all the releases which I have tried on vostro so far. The problem is related to Video Playback and Compiz Fusion on Intel. Therefore, developers blacklisted compiz to make playback work on this intel card. The above command will enable compiz for you in all releases for intel chipset. Hope it works for you too..

And for sound and Mic problems which were in all the releases I have tried. All you need to do is follow below:

**_Sound fix -_**
Add options snd-hda-intel model=dell-3stack to /etc/modprobe.d/alsa-base save and exit, reboot.

**_Internal MIC fix-_**
VOLUME CONTROL APPLET in PANEL

Double click the VOLUME CONTROL APPLET until the PREFERENCES window opened.

Then .. just click EDIT &#8211;> PREFERENCES and choose CAPTURE and DIGITAL and DIGITAL INPUT SOURCE.

After you did that steps above, NEW TAB should be appear, just click on it (it shows DIGITAL INPUT SOURCE) and change the value to DIGITAL MIC 

So far 9.04 is snappiest on my vostro even when compared to 9.10 which i am testing right now.. i am going to stick to 9.04 on vostro till 10.04

---

### Post by Soul-Sing on 2009-11-06
try: ```
sudo tcpdump -n -i eth0 > tcpdump.txt
gzip tcpdump.txt
```

And analyze the output. (with us?)

---

