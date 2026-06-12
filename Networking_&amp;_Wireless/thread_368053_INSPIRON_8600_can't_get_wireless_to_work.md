---
title: "INSPIRON 8600 can't get wireless to work"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by adonikam on 2007-02-22
Hey.... I'm new to this. I've spent a while now searching posts, I can't seem to get my wireless to work. Any help would be appreciated. I'm here at work (my laptop wont get wireless) so soon would be good. Would be willing to call a phone number to for help. Thanks!
Chris

1)The first problem is i don't know which driver is in this beast. I know it's internal and it's b/g. Looking at the info on the dell website PRO/wireless seems most familiar
2) the second problem is i'm not sure what the ssid is here at work. So, it doesn't seem to let me enable the card in settings. when i do put something in, it doesn't look like i can search for other networks
heres some iwconfig output: 

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
4) for lspci command i get this for my wireless:
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

Let me know what other info you need....

---

### Post by tgalati4 on 2007-02-22
Welcome to the community.

You must be the only one with a Dell 8600 that doesn't have wireless working.

Go to Applications-->add-->WiFi radar

You need a wired connection of course to download anything.

Bring up the radar and wait a few minutes.  The Access Point should show up (assuming it is broadcasting).  If it is on silent mode then you will have to bug the Windows-centric IT staff.  When they find out you are trying to log onto their secured windows network, you will promptly loose your job.  That's life.  

If you see the Access Point, double click and log in with the access key, typically 10 digits.  If your network uses WPA security, search the forums, there may be some problems or additional procedures to get it to work.

Your card is detected.  It's a matter of logging in.

The alternative method:

sudo iwconfig eth1 essid  "This is my cheesy network"

Good luck.

Share with us the steps that you tried and how the IT staff reacted.
You might as well post a resume as well.

---

### Post by adonikam on 2007-02-22
Thanks...
When i bring up wifi radar, nothing happens. same with wireless assistant (they find no routers) this didn't work at home either with my dlink dime-a-dozen router.
i think there's something deeper happening
i ran this command, don't know if this provides any info
cs@cs-laptop:~$ sudo iwlist scanning
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning : No such device

Also, when i go to system->administration->networking it says it's not configured, and i when i go in, in order for it to stay checked for enabled, i need to enter in an ssid. what if i dont know the ssid???

---

### Post by tgalati4 on 2007-02-22
What version of ubuntu are your running?  It could be that a driver got loaded but it's buggy or there is a better driver out there.  We need the exact chipset that you are using.  Is it built-in?  Is it a plug-in pcmcia card?  Is it Intel Centrino?

Does the wireless work under windows?  What does device manager call it?  Can you see your Access Point under windows?

I apologize for my troll-like comments.  Sometimes we trolls get bored sitting under the bridge and get excited when a wanderer comes along.

Roll your sleeves up.  You have some work to do:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

---

### Post by adonikam on 2007-02-23
PLEASE, Troll away! i just want to get this to work....
I'm running Ubuntu 6.10.
I was wondering how to find the chipset, i suppose that's my first problem. It is built in (not a pcmcia) It is pentium M inspiron 8600. Here's a print out of drivers options for networking from the dell support site for my service tag #

 Broadcom 440x 10/100 Integrated Controller 
 Dell _Wireless (Except US,Japan) WLAN Card 
 Dell _Wireless (Japan) WLAN Card 
 Dell _Wireless (US) WLAN Card 
 Dell TrueMobile 1300 MPCI Card 
 Dell TrueMobile 1300 PCMCIA 
 Dell TrueMobile 1400 WLAN 
 Dell TrueMobile 300 Bluetooth Internal card 
 Dell Wireless 1350 WLAN MiniPCI Card 
 Dell Wireless 1350 WLAN PC Card 
 Dell Wireless 1370 WLAN MiniPCI Card 
 Dell Wireless 1450 WLAN miniPCI Card 
 Dell Wireless 1470 Dual-Band WLAN miniPCI Card 
 Intel (R) PRO/Wireless Network Connection 
 Intel (R) Pro/Wireless 2100 LAN miniPCI Adapter 
** Intel (R) PRO/Wireless 2200BG Network Connection **
 Intel (R) PRO/Wireless 2915ABG Network Connection 
 
 The one in bold is the one that I think i have, since it is b and g capable. 

I don't have windows installed. almost wish i did at this point. 

I brought my own router into work. It's ssid is "default" and it has no WEP. i'm able to connect in with ethernet. I know the AP works. 

Meanwhile, I'll look at those thinks - thanks.
Keep in mind though, i don't know what i'm doing and i've already followed a lot of steps from these sites, i hope i don't further mess it up, as i don't know how to undo what i've done.
Thanks again,
Chris


> **tgalati4 said:**
> What version of ubuntu are your running?  It could be that a driver got loaded but it's buggy or there is a better driver out there.  We need the exact chipset that you are using.  Is it built-in?  Is it a plug-in pcmcia card?  Is it Intel Centrino?

Does the wireless work under windows?  What does device manager call it?  Can you see your Access Point under windows?

I apologize for my troll-like comments.  Sometimes we trolls get bored sitting under the bridge and get excited when a wanderer comes along.

Roll your sleeves up.  You have some work to do:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

---

### Post by adonikam on 2007-02-23
also, here's some spit out of sudo lspci -vvv
question: is this the actual chipset, or just the drivers that ubuntu has installed?

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at faff6000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME+

---

### Post by adonikam on 2007-02-23
wow it worked, i had to restart the computer after a couple of these steps and it worked. i seriously doubted this would work... anyway, maybe i'll post here a few of the things i learned once i get internet at home..
meanwhile this site dominates:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

thanks for your help.

---

### Post by tgalati4 on 2007-02-23
We ubuntu trolls were confident in your ability to find your way home.

Please share with others your experience.  It will make a good campfire story.

---

### Post by fogster74 on 2007-07-24
Hey,

Any chances of posting your experiences as you mentioned? Sure we'd be glad of the info!

I actually abandoned Ubuntu back in March when a hard-drive replacement led to a clean Windows install. Would really, really like to come back to the fold - but dreading trying to get my Dell TrueMobile 1400 (BCM 4309 chipset) card working. Tried 'n tried 'n tried 'n tried previously. Had it working once (in 6.06, I think), but never again, either under 6.10 or 7.04. 

I'm curious - can someone either explain to me, in plain English, the difference between the ndiswrapper and fwcutter methods, or else point me to a link that explains how each of these different approaches works?

I can see there's truckloads of info on this card on here and, in some ways, that's the problem - so much contradictory information and alternative methods. It's information overload! It would be so lovely if this was moderated in some way to draw all of these threads together for the relative) newbie. There's so much duplication that, these days, it's truly frightening. And it always chills me to see some poor newbie in a post ' please help me', 'please please help me', 'agh I'm back off to Windows'... :(

PS If anyone has got a truemobile 1400 working on a Dell 8600 or knows of a link that works for exactly this combination, I'd be exceptionally grateful :)

Have fun people - I hope to be 'back in the club' soon!!!!

Stevo

---

