---
title: "Neither wireless nor ethernet will work..."
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by deranged_one_13 on 2005-07-03
This is a plea for help from a VERY desperate woman.  I am brand spanking new to Ubuntu.  To Linux actually.  I installed the Hoary Hedgehog release on my Toshiba laptop 5 days ago and have yet to figure out a way to get internet to work.  I have a SMC2632 wireless card.  I have the drivers for it but I don't know how to get them installed.  Apparently I'm supposed to "make clean" and "make install" but according to my linux fluent friend I don't have those installed.  So then I tried to connect the ethernet cord to the computer directly and that doesn't work either.   The system won't recognize the ethernet connection or something.  I hope some kind soul can help me, but please, make all instructions easy for me to understand.  Think "linux for dummies".  Thanks for any help.  If I can't get it to work, I'll just go back to Windows....easy-to-use windows, even if I do have to reformat every few months.

---

### Post by Seti on 2005-07-03
Having to go back to Windows because you couldn't get a wireless card that is known to be supported in linux would be sad indeed; most often someone trying linux when they're normally a Windows user shows signs that the person has grown dissatisfied with the windows way. So...
I'm pretty sure your wireless card is supported. Since this is the case, you should have been able to set it up during installation; normally the Ubuntu installer will detect the hardware and offer to configure it in the process. Many wireless cards have a little switch on the outside to turn on the wireless, did you make sure this was on?
Perhaps during install you skipped the step inadvertantly where you could have configured your internet connection? 
I'm assuming since you use wireless you're familiar with the ESSID name (wireless network name) for your wireless network (at home? at work?)
I would just try reinstalling it and take care to pay special attention during the network setup part of the install. Otherwise, probably other forum members here may have better suggestions. Point is, you should be able to get online quite easily.

---

### Post by deranged_one_13 on 2005-07-03
[QUOTE=Seti]Having to go back to Windows because you couldn't get a wireless card that is known to be supported in linux would be sad indeed; most often someone trying linux when they're normally a Windows user shows signs that the person has grown dissatisfied with the windows way. So...
I'm pretty sure your wireless card is supported. Since this is the case, you should have been able to set it up during installation; normally the Ubuntu installer will detect the hardware and offer to configure it in the process. Many wireless cards have a little switch on the outside to turn on the wireless, did you make sure this was on?
Perhaps during install you skipped the step inadvertantly where you could have configured your internet connection? 
I'm assuming since you use wireless you're familiar with the ESSID name (wireless network name) for your wireless network (at home? at work?)
I would just try reinstalling it and take care to pay special attention during the network setup part of the install. Otherwise, probably other forum members here may have better suggestions. Point is, you should be able to get online quite easily.[/QUOTE]

Hi there.

okay, I did eventually skip the step to configure it during setup because it kept giving me an error message saying that it wasn't able to detect the network or something.  My wireless card doesn't have a switch, so that wasn't the problem.  Wouldn't I need to install the driver for my wireless card?  Because I can't do that during setup... maybe it couldn't detect the wireless connection because the driver wasn't installed or something?


EDIT:  Okay, I'm reinstalling Ubuntu.  I disabled the WEP key on my router and now the autoconfiguration of the network worked.  Hopefully I can reactivate the WEP key when Ubuntu is reinstalled.  I'll let you know how it goes.

---

### Post by Seti on 2005-07-04
Glad to hear that worked for you. You can re-enable your wireless encryption and set your laptop up with the WEP key, after that you shouldn't have any further problems. If you do, don't hesitate to post back, or PM me if you have any questions.

---

