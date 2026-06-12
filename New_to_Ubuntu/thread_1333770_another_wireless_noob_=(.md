---
title: "another wireless noob =("
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Un_loco on 2009-11-21
Ok i tried an install of KK on an alternate drive.  Since Grub wont work with fakeraid, I am about to start the process of putting windows7 on one 500g drive and ubuntu on another.  I ALWAYS try out every new edition of ubuntu, just to see if me and ubuntu are ready to click. Of course I just want an answer to my main issue, but i'm going to WTF 9.10 for not supporting Linksys wireless out of the box but supporting it on an apt-get. I dont expect everything to be supported for a CD (not DVD) install, but come on.... what DO they support for wireless when i see this wireless ready claim.  but i apologize for that rant, i really wanna work it.

anyway.. my desktop is N wireless (maybe my problem) my router is G wireless.  both linksys.  waiting for the router to crap before i upgrade, as my desktop wireless card did.
how can I jerry rig the wireless to work in order to get the proper driver the easy way.  I am not good enough to compile anything, i'm not smart enough for that.  I'm a windows idiot, and i am ready to get changed over but i'm scared of every time i try this, i end up in a routine of copy and paste terminal commands.
its either that or move the desktop to a spot where i can wire the computer for a short update, if you will

(edit... waiting to find out the answer to switch windows to non-raid.. I'm gunna do it anyway, cuz I just learded fakeraid just eats up CPU time for games, so it ruined my whole reason of doing it lol ... correct me if i'm wrong)

---

### Post by oldsoundguy on 2009-11-21
At the top of your page is a bar.  That is called the panel.  on the right side near the date/time will be some funny little lines.  Mouse over for verification that it is your wireless connection.  OPEN IT.  Select your network (there may be many if you live in an apartment complex.) Enter your password (if you put one in in the first place) Wait a few seconds while it does some spinning.  You will get a pop up that you are connected to your network.  Launch you browser of choice. (that is all I had to do on two 9.10 installs and a Mint Gloria install.)

Now this is provided that your wireless connection device (be it plug in card or on board) is recognized by the software.  If it is NOT, replace it with something on the compatibility list.

But MOST devices are recognized by 9.10.  (some Broadcom chips are not, as Broadcom changes it's architecture in laptops as often as I change my shorts.

The NEW wireless connectivity issue is with G3/G4 or Wireless Broadband.  MOST Wi-Fi or home net stuff has been solved.

---

### Post by Un_loco on 2009-11-21
i guess mine is one of the few pci boards that are not. i went to the wireless part on the panel.  nothing found.  went to the network setting and entered in my specific wireless info and of course even tho i knew tht wouldnt work, nothing was found.

what is the command for figureing out the broadcom chip i have? lol

---

### Post by oldsoundguy on 2009-11-21
in terminal: 

lshw

It will list ALL of the hardware the OS sees.

---

