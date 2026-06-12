---
title: "Belkin wireless card"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by PAPA L on 2009-06-08
Hi all, ):P
 
Hope I've posted the following question in the right area
 
Being a complete beginner with Linux, I'm not entirely sure how to get Ubuntu to recognise my Belkin wireless card. It's a F5D7001uk card.
 
I've installed ndiswrapper as per various guides I read on these forums and got it recognising the windows driver but am unable to get any further than this.
 
iwconfig shows the card at wlan0. output shown below :

[INDENT]wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry min limit:7 RTS thr:off Fragment thr=2352 B 
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
[/INDENT]Any suggestions would be very much appreciated.
 
Cheers.

---

### Post by PAPA L on 2009-06-09
OK sorry about the above output, I obviously wasn't taking forum code and smilies into account.
 
Anyway I think I should also have posted the lspci output. Here it is :
 
[INDENT]> 00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
 
[/INDENT]If there's any other info you need let me know,
 
Cheers.

---

### Post by Toshubu on 2009-06-09
Hi Papa,
I have 8.04, but I assume 8.10 works the same. See this link: 
[URL="http://ubuntuforums.org/showthread.php?t=197102"]http://ubuntuforums.org/showthread.php?t=197102
[/URL]. Mine is a bcm4318 also and it worked like a charm. Should at least get you started.

---

### Post by PAPA L on 2009-06-09
Thanks very much Toshubu, that looks very useful.
 
I'll give it a go and we shall see how I get on.
 
PAPA

---

### Post by PAPA L on 2009-06-09
OK, this didn't work.
 
But..... I have played around with various settings so much that I think it might be best if I did a fresh install and while I'm doing that downgrade to 8.04 ( I just noticed that it has LTS ) and then try that suggestion again.
 
Still, despite the teething troubles (most of which, I suspect, are down to me being a complete novice) I'm really loving the feeling of using an OS that isn't Windows.
 
Thanks.

---

### Post by Toshubu on 2009-06-09
Did not work?..Was the "Broadcom B43 driver" even in the (proprietary) Hardware Drivers list?...Or, is there no function like that in 8.10?..I'd like to help if I can...

---

### Post by anewguy on 2009-06-09
There are many posts here for the BCM 43xx, so if you do a forum search you should be able to find the instructions.  Just remember that if you use ndiswrapper for this series you will need to blacklist several things now:

b43
ssb

I think there is another one yet, but off hand I don't recall the name.  Without doing the step of blacklisting the built-ins, you can load your driver with ndiswrapper but it probably won't work because of conflicts.

If you need any help, please post back.

Dave :)

---

### Post by Toshubu on 2009-06-09
> **PAPA L said:**
> OK sorry about the above output, I obviously wasn't taking forum code and smilies into account.
 
Anyway I think I should also have posted the lspci output. Here it is :00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
 
[INDENT]
 
[/INDENT]If there's any other info you need let me know,
 
Cheers.
Hi again Papa,
Not sure about the F5D7001uk card that you have (as stated in post #1); but since it has the bcm4318 chipset, I'm suggesting that you don't have to go the ndiswrapper route. At least, I didn't have to. What I don't know is if ubuntu 8.10 works the same as 8.04. If it does, all it took me was a few keystrokes to make it work. One of the reasons I stuck with 8.04 is that it is indeed a LTS version, as you have observed. I just wanted to know where the proceedure failed on you; in case that might make me reluctant to link to it, in the future.

---

### Post by PAPA L on 2009-06-09
Hi Toshubu.
 
For some reason, there was nothing in the hardware drivers list at all.
 
Hope that helps.
 
Anewguy,
 
Blacklisting those items removed the device from wlan0 altogether. As Toshubu has said, that suggests that I didnt need to use ndiswrapper as those would appear to be the drivers I actually need. But still nothing in the hardware drivers list.
 
Thanks for taking the time to offer your suggestions both of you.

---

### Post by ptn107 on 2009-06-09
I have the same network adapter built into my Compaq v2000z laptop.  Enabling the proprietary drivers in System -> Administration -> Hardware Drivers allows the hardware to function properly.

---

### Post by Toshubu on 2009-06-09
I must confess Papa...I can't remember if I had to download anything to make that proprietary driver available. Surely somebody can help us with this.

---

### Post by anewguy on 2009-06-09
BTW - if you go with the restricted drivers, remember to reverse a couple of things:

remove the items added to blacklist

via ndiswrapper, remove any drivers you had installed

remove ndiswrapper from modules file

Easy to forget one of those, try a new driver and think hummmmm, this isn't working either!

I haven't ever used the restricted driver - it was always just my personal preference to ndiswrapper (old habits are hard to kill :) ), so I'll leave it to others with that experience to help you.

Best of luck!
Dave :)

---

