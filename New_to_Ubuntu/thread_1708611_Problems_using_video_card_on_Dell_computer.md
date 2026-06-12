---
title: "Problems using video card on Dell computer"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Kilron on 2011-03-16
Ok, so I recently acquired a used Dell from someone for free after my previous machine took a crap on me, and decided to do a proper dual boot of XP and Xubuntu 10.10.  The thing is, I was unable to install Xubuntu at all unless I went into the BIOS and set it to only load the onboard graphics.  Now it's installed and I'm finding my way around fairly well, but I'd like to use the video card, and I cannot figure out how to make Xubuntu not attempt to use the onboard graphics, as there is no option to disable them via BIOS (and I've looked around, it has the latest BIOS and there is apparantly no option on this model at all).  Any ideas?

The pc is a Dell Dimension 2350, and the card is an ATI Radeon 9200.

---

### Post by wep940 on 2011-03-16
I don't know about the 9200, but I used to have a 9250 Pro and it just used the default Radeon driver in Ubuntu, and compiz desktop effects, etc., worked fine with it.  I did notice that XUbuntu uses Xfce, so perhaps that has something to do with why the Radeon driver isn't working.
 
Look at the Xorg0 log file in /var/log and see what it says when you try to use the Radeon card.
 
Perhaps there is a Radeon driver in the repositories that you can add that would also solve it.

---

### Post by Kilron on 2011-03-16
The problem isn't the driver, it's that I can't disable the onboard graphics.  From what I've read, this particular Dell has problems with Linux in general unless you turn off the video card, as it tries to load both and causes errors.  However, I'm sure there is a way to disable something in Xubuntu so it only recognizes the video card, I just don't know what that way is.

---

### Post by wep940 on 2011-03-16
Sorry - I didn't get that from your first post - went back and looked and it's there, so again - sorry.

---

### Post by wep940 on 2011-03-18
I'm not sure how you are going to do this.  I did some searching on the net, and what I read indicates that BIOS lets you say primary video is PCI/AGP.  Some people also report that in Windows (I don't know if there is a way to do this in Linux) they go into device manager after adding the 2nd adapter and disable the onboard adapter via the device manager.

---

### Post by Kilron on 2011-03-18
Unfortunately, the BIOS on this particular model only allows for two options, onboard and auto.  If I set it to auto, I get a ton of messages pop up and then it either stops working or it keeps saying "killed" over and over again.  I tried to run my live CD and set the "nomodeset" or whatever it's called that pops up when you push F6, and that doesn't work either, it causes the same errors.

Apparantly, I'm not the first to have this problem with this Dell model, and so far, it doesn't look like anybody has solved it.  So I'm thinking I may just have to stick with onboard for xubuntu, and only use the card with XP.  It runs great as it is, I just wanted to get this card working on here for games, but everything I play doesn't need it anyway.

---

### Post by wep940 on 2011-03-19
check your BIOS version - the posts I read, and the information on the net I have found, indicate it must be at a minimu of A01.  Some people have had a newer version and had problems and tried going back to A01 but couldn't.

---

### Post by Kilron on 2011-03-19
The version I have is A02, the newest one, and it still only allows auto and onboard to be selected.

---

### Post by wep940 on 2011-03-19
I'll try to go back out on the net and track down some of the things I was reading and then post the links back here for you to check.  Since it's Saturday, it will probably be later tonight or Sunday before I post back.

---

### Post by wep940 on 2011-03-19
Went back and read a lot of the threads on the net again.  As it turns out, BIOS A01 lets you disable the onboard video, where A02 only has the options you specified.  There may be 2 options for you to try:
 
- Some PC's recognize that a different video card is plugged in and will "auto-switch" to the new board.  I'm sure you have, but I have to ask:  have you powered off, connected the monitor to the new video card, then powered on again?  Does the display show anything?
 
- Try a BIOS downgrade to A01.

---

### Post by Kilron on 2011-03-19
I have in fact tried plugging it into the card, and it does show things properly, it's just that it fires errors at me after I select Xubuntu in grub.

I may try a BIOS downgrade, but I'll wait until I get a chance to back everything up in case something goes wrong.  Right now, I have nothing to back things up onto for all the data I have between XP and Xubuntu.

---

### Post by wep940 on 2011-03-19
Hummmmm.....maybe Xubuntu needs a driver for it to work well with your card.  I had the AGP version of the 9250 Pro and it worked in regular Ubuntu with the included Radeon driver, *BUT* I don't know anything about Xubuntu so I don't know if the same type of driver is included or not.
 
I may be requesting something you've already done again, so forgive me if so, but have you tried the CTRL/ALT and F1 to see if you get a terminal window, and if that window at least looks ok?  That might help point to a driver problem.
 
I'm curious just because I don't know - I wonder if this will be one of those cases where you have to create a xorg.conf file and set up the adapter there and link it to a monitor, etc., so that xorg will default to it.  That's *IF* Xubuntu uses xorg - I know I've heard mention of something called Xfce or some such thing, and I think that was in regard to Xubuntu, so perhaps it doesn't use xorg.
 
I can try searching the net again and see if anything specific shows up for that PC, video card switching and Xubuntu.
 
I wish I could help you more but I'm no expert on any of this - just trying to help.

---

### Post by wep940 on 2011-03-19
I have no idea if this will help you or not, but I did find it in a thread about your problem expect with regular Ubuntu:
 
**[SIZE=2][COLOR=#3366cc]Guest[/COLOR][/SIZE]** 
[LIST]
[*]**Rank:** Guide
[*]**Rating:** 0%, 0 Votes
[/LIST][]("javascript:void(0);")

I have the exact same PC and problem with all versions of linux I have tried from Mepis, Ubuntu, etc.

Problem is the bios appears to be buggy. Linux boot will find the onboard video even if you have the bios set to use your MX4000 PCI card. Linux boot freezes with different error messages. 

Easy fix is to just use the onboard video. Of course if you wanted to do that you wouldn't have bought the card right?

What I have done is first I use the onboard video to install say Ubuntu Linux. You don't even have to remove the PCI video card.

Step by step:
1. set bios to use onboard video, and connect your monitor to the onboard video port.

2. in terminal: sudo gedit /etc/modprobe.d/blacklist  **EDIT FROM WEP940:  THE FILE NAME IS NOW BLACKLIST.CONF, SO USE "blacklist.conf" AS THE FILE TO EDIT**

add these lines to the end
blacklist agpgart
blacklist intel_agp
press control-X to save your changes
After you install you have to "blacklist" the onboard video. 

3. shut down linux. besure to power down the PC because its just easier to bet into bios from a hard boot. 

4. go to bios and set video to "auto" and save your change.

5. move your monitor cable to the MX4000 PCI video card

that should do it. any trouble just search ubuntu forums for blacklist agpgart or intel_agp

---

### Post by Kilron on 2011-03-20
It.  WORKED!  I'm posting from the machine as we speak.  Thanks so much!

---

### Post by wep940 on 2011-03-21
I'm glad it's working for you - and I'm thankful for whoever created that thread on the internet where I found this.  Like I said - I don't know anything about, so I'm glad someone else had made it work and that their solution worked for you!

---

