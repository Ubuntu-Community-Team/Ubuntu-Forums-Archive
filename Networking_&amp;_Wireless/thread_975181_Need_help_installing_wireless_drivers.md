---
title: "Need help installing wireless drivers"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by Jameshardy88 on 2008-11-08
Hi i have recently installed Ubuntu 8.04 hardy heron using Wubi (i know already out of date). I do not appear to have my driver software for either my wireless or graphics cards, firstly is tis normal? Secondly die to this whilst on ubuntu i do not have access to the internet, which appears to be integral to installing new software, including new driver software. My question is this as i still have access to the internet using other computers is it possible to download driver software (i think i need it to be a .deb file, is this correct?) and then manually transfer it over to my computer with ubuntu and install it? if this is the case how exactly do i achieve that?

Thanks for your help, James

---

### Post by crashingthrueden on 2008-11-08
what brand and model is your laptop and do you know who the manufacture is for your devices?


i am also fairly new to the linux platform, but i have been able to tackle some similar problems.  you CAN def. transfer the files via disk or flash drive.  you said that you couldnt get online...have you tried just jacking into your ethernet port, or do you not have internet access in your location.   if that is the case you will be best off getting to an internet connection with the notebook in question.   with the notebook booted and on the desktop, run [system - administration - synaptic package manager]  click search at the top and type in the manufacture name of your wifi card.  read the description of the installs verify its for estricted drivers and preferably select one with the ubuntu symbol....(i dont know why but it made a difference for me)

install and restart and you should atleast have your drivers installed.....using the hardware may be a different story

do the same for the video card




let me know if this was any help

---

### Post by Jameshardy88 on 2008-11-08
> **crashingthrueden said:**
> what brand and model is your laptop and do you know who the manufacture is for your devices?


i am also fairly new to the linux platform, but i have been able to tackle some similar problems.  you CAN def. transfer the files via disk or flash drive.  you said that you couldnt get online...have you tried just jacking into your ethernet port, or do you not have internet access in your location.   if that is the case you will be best off getting to an internet connection with the notebook in question.   with the notebook booted and on the desktop, run [system - administration - synaptic package manager]  click search at the top and type in the manufacture name of your wifi card.  read the description of the installs verify its for estricted drivers and preferably select one with the ubuntu symbol....(i dont know why but it made a difference for me)

install and restart and you should atleast have your drivers installed.....using the hardware may be a different story

do the same for the video card




let me know if this was any help


Yes thanks, i will be trying that first thing monday all being well.

I have a Hp Pavillion dv6000 i think, it has a BCM 4312 netwrok card and some version of Nvidia graphics, not tried to decifer which yet. Just regarding installing the driver software once i have found the relevent deb file do i literally just double click on it or do i need to open it in a different way or open it through a program?

---

### Post by Jameshardy88 on 2008-11-08
any additional info is welcome

---

### Post by Jameshardy88 on 2008-11-09
any more help would be appreciated

---

### Post by Foxbat250 on 2008-11-09
hello
I bought a new HP laptop and I installed ubuntu 8.10
but I am facing a problem with the atheros AR928X wireless driver.
I couldn't find the way to install and to use wlan 
does anybody find a solution for installing a driver 

Thanks in advance

---

### Post by buccaneere on 2008-11-09
Yes, you can download driver modules to CD, and transfer them to another machine, I've done it (but do not remember proper file formatting)

Couple of solutions here:
[http://ubuntuforums.org/showthread.php?t=491621](http://ubuntuforums.org/showthread.php?t=491621)

Your HP dv uses Broadcom proprietary driver, which will download as soon as you have access to update. It WILL also have to be optionally enabled.

Mine is HP dv 9xxx

---

### Post by crashingthrueden on 2008-11-09
> **Foxbat250 said:**
> hello
I bought a new HP laptop and I installed ubuntu 8.10
but I am facing a problem with the atheros AR928X wireless driver.
I couldn't find the way to install and to use wlan 
does anybody find a solution for installing a driver 

Thanks in advance
dont try to download all kinds of crazy stuff for your atheros wifi adapter it will only make things harder....i know that is what my acer uses.  simply go to synaptic package manager and search for atheros and several options to download will pop up.  somethin called madwific   (which was just released this yr i believe) was designed specifically for the atheros wireless adapters.  just select on of the options with the ubuntu symbol next to it and the description below should read something along the lines of "restricted drivers...blah blah" and kind of tell you that it is for atheros wireless cards (integrated or not).  just install and restart.  if it doesnt work try removing all the driver packs or fixes youve tried allready and dont let ubuntu download anything when it recognizes that your device isnt functioning properly....that only made things harder for me....

i hope this help and let me know if it does



{also if you just installed ubuntu and havent done much with it yet, its best to install updates and not go crazy with apps and extras until you get all your hardware running because some advanced programs and interfaces i have seen effect delicate settings that may need to be set prior to their install....just a little somethin extra)

---

### Post by crashingthrueden on 2008-11-09
> **Jameshardy88 said:**
> Yes thanks, i will be trying that first thing monday all being well.

I have a Hp Pavillion dv6000 i think, it has a BCM 4312 netwrok card and some version of Nvidia graphics, not tried to decifer which yet. Just regarding installing the driver software once i have found the relevent deb file do i literally just double click on it or do i need to open it in a different way or open it through a program?
to be honest with you it would be alot easier and safer if you didnt try to "grab and stick" the file manually.  ubuntu has some great tools for file installation and they are allready routed to the correct locations when installed.  and beware of the ndis wrapper all of you....it caused trouble for my wireless device and i hade to restore ubuntu to get my device to even be recognized.  all it does (in many cases, not all) is use windows drivers on linux, sounds unstable to me. thats the reason i got away from windows.  so just remeber to use synaptic package manager, search for broadcom and you should see several options, pick the one you think is best by reading the description available when you highlight the package simply download and install....when you restart you should have all the necessary drivers installed......and remeber that im not knocking the ndis wrapper, just saying that when you have problems it doesnt necessarily make it easier to get a "fix".   from what ive seen its a smoother process to just stay away....atleast in the beginning

hope this helps, and sry about the rambling about the wrapper. lol

---

### Post by Foxbat250 on 2008-11-09
Thanks for your reply 
I did what you asked me: I installed the package, but it doesn't work. I found a utility which is called windows driver installer (which was already installed) I removed this application also. 
For information: I already tried the windows driver and some drivers available in the website of Atheros!!! but at the end nothing
for your information I have HP laptop Pavilion dv5 and I think the the Wlan and the bluetooth are in the same chip!!!
Do you have other proposal ?

---

### Post by crashingthrueden on 2008-11-09
> **Foxbat250 said:**
> Thanks for your reply 
I did what you asked me: I installed the package, but it doesn't work. I found a utility which is called windows driver installer (which was already installed) I removed this application also. 
For information: I already tried the windows driver and some drivers available in the website of Atheros!!! but at the end nothing
for your information I have HP laptop Pavilion dv5 and I think the the Wlan and the bluetooth are in the same chip!!!
Do you have other proposal ? 

well i havent even played with ubuntu 8.10 but im pretty sure its nearly the same as 8.04 in respects to our wireless cards.....i had to restore my linux os in order to make sure i had a true clean start (im dual booted with xp pro sp2). i noticed that the packets that where pulled up for you werent the complete list and that makes me wonder if you are connected to the internet.......you must have a live Ethernet connection in order to find the correct packets.... here you will see that the drivers are good and generic....just remove everything and start over, it wont hurt.......only do this if when you go to [system - admin - hardware drivers]  and dont see that you have drivers installed enabled and in use......then just simply search for the driver you see here on my screen and viola......now getting the drivers installed in relatively simple, just not always easy i have found....the tricky part is getting it to recognize your wireless card to make internet connections after the drivers are installed.....get this done and let me know more

---

### Post by Foxbat250 on 2008-11-13
hi
could you take a look to this link 

[http://wireless.kernel.org/en/users/Drivers/ath9k](http://wireless.kernel.org/en/users/Drivers/ath9k)

---

