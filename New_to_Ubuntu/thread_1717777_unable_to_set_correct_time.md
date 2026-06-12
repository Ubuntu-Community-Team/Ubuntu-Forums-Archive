---
title: "unable to set correct time"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by geppetto1 on 2011-03-30
I'm running Ubuntu 10.04 in Virtualbox on XP.  Locale is Eastern time / NY / America...   

I noticed the clock was off by an hour - we recently switched to daylight savings time.  Not sure if it happened then, but it was after the switch that I noticed.   XP shows 11:44 am, Ubuntu shows 12:44 pm.  Attempts to correct the clock on Ubuntu have been unsuccessful.  I have tried to change the time through:
 - the clock on the Gnome Panel, 
 - System / Administration / Time and Date, 
 - the command line (date mmddhhmmyyyy, ntpdate servers_near_me), 

/etc/default/rcS UTC=yes, UTC=no, ntp enabled, ntp disabled.  I also went through the command line process of setting the correct time zone (just to be sure).  All are unsuccessful.  Shortly after I change the time, it reverts to current time plus one hour.  

I would think that if I disabled ntp, set the gnome time and date applet to manual, su'd to root, and executed 'date mmddhhmmyyyy' or 'ntpdate server' that I would be able to change the time and have it stay changed.    

Is there a piece of software that is protecting me from myself?

Thanks!

---

### Post by VernonA on 2011-03-30
The time is coming from a real-time clock (RTC) chip on your motherboard. In order to change it you need to talk to the BIOS, and so that needs to be done from the host O/S (ie Windows). The virtual machine which is running Linux provides a virtual BIOS to Ubuntu - you may well be able to change the virtual RTC but eventually it will re-synch with the real RTC and your change will be lost.
Why don't you use Windows to set the clock correctly?

---

### Post by lhb1142 on 2011-03-30
> **geppetto1 said:**
> I'm running Ubuntu 10.04 in Virtualbox on XP.  Locale is Eastern time / NY / America...   

I noticed the clock was off by an hour - we recently switched to daylight savings time.  Not sure if it happened then, but it was after the switch that I noticed.   XP shows 11:44 am, Ubuntu shows 12:44 pm.  Attempts to correct the clock on Ubuntu have been unsuccessful.  I have tried to change the time through:
 - the clock on the Gnome Panel, 
 - System / Administration / Time and Date, 
 - the command line (date mmddhhmmyyyy, ntpdate servers_near_me), 

/etc/default/rcS UTC=yes, UTC=no, ntp enabled, ntp disabled.  I also went through the command line process of setting the correct time zone (just to be sure).  All are unsuccessful.  Shortly after I change the time, it reverts to current time plus one hour.  

I would think that if I disabled ntp, set the gnome time and date applet to manual, su'd to root, and executed 'date mmddhhmmyyyy' or 'ntpdate server' that I would be able to change the time and have it stay changed.    

Is there a piece of software that is protecting me from myself?

Thanks!

I believe that having ntp disabled is what is causing your problem. I recommend that you go back into < System / Administration / Time and Date >, click to make changes (you will need to enter your password), enable "Keep synchronized with Internet servers," (I believe that it is at this point you will be required to enable NTP), and then choose your servers (I have checked all of the US-located time servers).

I hope I am correct in my suggestions; I haven't actually done this for some months now. My computer's time is always correct almost to the second (verified by looking at a radio-controlled ("atomic") clock) and the daylight-savings time change was effected properly.

I hope the above is of some help to you.

Lawrence

---

### Post by VernonA on 2011-03-30
You don't mention whether or not you have ticked the "Hardware clock in UTC time" box on the Motherboard tab of the System Settings dialog shown when you click the Settings section for your guest O/S in the VirtualBox Manager. This affects how the BIOS emulation layer handles reporting of the real RTC to the guest.

---

### Post by geppetto1 on 2011-03-30
Thank you for your replies.

@VernonA - I was not clear in my orig.post - The time settings in windows and bios are both correct.  The time in the Ubuntu VM is incorrect - one hour fast. 

@ Lawrence - ntp had no effect.  I configured the software to utilize ntp automatically and the time appeared to be unchanged.  I then disabled ntp - set it to manual.  I then su'd to root and executed the commands from the command line.  I would like to get this VBOX running on ntp but I need to get the time / clock function working correctly first.

More info that may help, or not...

Here is a trace of one of the attempts last night:

```
root@adminuser-desktop:/home/adminuser# ntptrace louie.udel.edu
louie.udel.edu: stratum 2, offset -0.001558, synch distance 0.022327
rackety.udel.edu: stratum 1, offset 0.000003, synch distance 0.000000, refid 'PPS'

root@adminuser-desktop:/home/adminuser# date
Wed Mar 30 12:19:42 EDT 2011

root@adminuser-desktop:/home/adminuser# ntpdate louie.udel.edu
30 Mar 11:20:04 ntpdate[4062]: step time server 128.4.40.12 offset -3597.792939 sec

root@adminuser-desktop:/home/adminuser# date
Wed Mar 30 11:20:12 EDT 2011

root@adminuser-desktop:/home/adminuser# date
Wed Mar 30 12:20:23 EDT 2011

root@adminuser-desktop:/home/adminuser# ps -ef |grep ntp
root      4250  2269  0 12:25 pts/0    00:00:00 grep ntp
```I added the spaces between the commands to improve the readability.  A few seconds after I set the clock from louie.udel.edu, I checked the time and it was correct.  A few seconds later I checked again and it was an hour fast.  I then checked to make sure ntp was not running.  It was not.  Not that it matters, louie.udel.edu is in the same timezone as me.  

There are other virtual machines on this Virtualbox and their time is correct.  VirtualBox's virtual bios appears to be reading the RTC correctly.  I have Ubuntu 10.10 VBox running on another XP system and it's time is also correct - although I haven't tried setting the time.

I should be able to go into manual mode and set the time.  Something is changing it shortly after I set it.  

Thanks.

---

### Post by VernonA on 2011-03-30
I too have 10.04 and 10.10 on VBox 4.0.4 but the difference is that for me both are working correctly;-)

1) If the error is only occurring on one guest then I think you are right to say that the Windows time is probably set correctly. If you only had one guest, I would be looking hard at Windows since it doesn't handle time well at all (to be fair it does what people expect, but what people expect is wrong since they assume the BIOS clock should be set to local time when it shouldn't). Assuming that your BIOS reads local time uncorrected for Daylight Savings, and you have the DST box ticked in Windows, then the virtual Bios in VBox should be able to "adjust" the time it sends to Linux to convert it to UTC based on your locale. Ubuntu then uses the time zone and date you have set to convert that back to local time.
2) This process is automatic and in general works well so I wonder where the error is creeping in. Note though that you cannot set the time in the guest for the reasons I have already mentioned, so doing things like attaching to an NTP server are not going to help. I'm sure you have a flag unset/set somewhere that is causing an extra hour to be added in cos something thinks a DST correction needs to be applied to a time that is already corrected. We just have to find it and toggle it!

3) As a sanity test, could you lie and set your location to the next timezone along (try both directions)? The clock should adjust forward and back one hour each way. If it doesn't, it would suggest you do have a daemon running that really is over-riding the displayed time for some reason. If the time does adjust correctly, then its back to hunting for the flag!

4) Also make sure you are up-to-date on all the software, in case its a known bug somewhere that has already been fixed.

---

