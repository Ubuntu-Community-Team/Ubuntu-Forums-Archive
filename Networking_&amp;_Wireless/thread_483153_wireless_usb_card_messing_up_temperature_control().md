---
title: "wireless usb card messing up temperature control(?)"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by gpap on 2007-06-24
Hi, I am running feisty on a compaq presario 2540EA laptop and since I 
started using a usb wireless card 3 days ago I have been having the 
following two problems which I assume are somehow related:

-my wireless usb card works fine up to some point(20mins-4hours) and 
then refuses to work further. The "network configure" gui is not 
responsive when the card stops working and "ndiswrapper -l" doesn't 
provide any output. There doesn't seem to be a secondary driver conflicting
with the windows xp one (when card works "ndiswrapper -l" outputs only the 
one driver that ndiswrapper is using)
The card is a Mentor WLG-USBII and I am using the latest windows xp 
drivers with ndiswrapper.

-more importantly, after I first used the card I started getting the
"critical temperature reached" message and forced switching off. I 
have reasons to believe that this is not due to the bug that many people
have reported and that the laptop is actually overheating. There's 
several bizarre things related to that. First of all the critical 
temperature is different every time (ranging from 43 to 70 ^oC). 
Second is the fact that the two out of the three fans refuse to work
before the critical temperature is reached. Sometimes the second fan 
starts spinning and yesterday the third did as well and I managed to
run gnome and it didn't overheat at all. The laptop stayed on for
4 hours and all was fine, apart from the wireless card failing me of 
course, until the point I switched off. Today it is the same (I am now 
writing on recovery mode). I tried the "acpi=off" but grub didn't load
as it didn't recognise the command. I read that this would surely 
have all the fans working at full speed. 

The laptop has a history of overheating and under windows it would 
frequently switch off but I've been using ubuntu since November 2007
and it only did it once (and that once it was wrapped in a duvet). In
recovery mode, bizarrely, the wireless card works fine (I am posting using 
a text-based browser).

Please, any ideas would be really appreciated. I don't know if the wireless 
card can be responsible for the overheating thing but they were diabolically
coincidental if it wasn't.
 
Thanks

[EDIT]----------------------3 days later, problem solved--------------------------------------

I managed to solve my problem. It *WAS* indeed due to ndiswrapper. What
I did was:
-follow [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=483548") holy man's instructions (it is claimed that the ndiswrapper one gets from the depositories has errors and I believe that for some reason).
The correct installation of ndiswrapper stopped the false overheating alarms and the switching offs.
-manually add the mac address of the usb card to the relevant place at "/etc/ndiswrapper/[driver name]/[usb id].F.conf
-reboot

I haven't had any overheating problems and my wireless card works fine. If I had to spend the rest of my life in recovery mode, I'd still prefer it to changing back to windows...

---

