---
title: "Wireless card in laptop problems.. No ndiswrapper available"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by shad0wslay3r on 2007-01-10
So I bought a new laptop and the wireless card that i bought for it was working fine with windows pro.  Wiped the drive and put the newest ubuntu on it and the card didnt work.  Big deal just need to install driver.  Try to install driver isnt supported.  w/e look up the ndiswrapper, try to use it with my O/S but it isn't there.. its like it isnt installed.  I dont kno how else to get my card to work.. probably something noobish but i spent the last 2 hours going thru all the how to guides

---

### Post by shad0wslay3r on 2007-01-10
I was able to download the ndiswrapper onto my laptop, i extracted it but I am not very familiar with ubuntu's file set.  I just extracted it onto my desktop.. How do I go upon installing it

---

### Post by hscottyh on 2007-01-10
From terminal:
sudo apt-get install ndisgtk
sudo ndisgtk

That will bring up a gui that will be intuitive from there.

Good Luck!

---

### Post by shad0wslay3r on 2007-01-10
Hi
Thanks for the reply

After selecting the .inf it came up with this:

Fatal: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid Argument

---

### Post by hscottyh on 2007-01-10
Hmmm....

Sounds like you'll have to find another windows driver for your chipset. It took several downloads before I found one that worked on my friends laptop a few months ago.

If you post your hardware, I bet someone will point you to one that works.

Sorry I couldn't be of more help :(

---

### Post by shad0wslay3r on 2007-01-10
Not a problem

My laptop is a HP/Compac NC6000, pentium M processor 1.6ghz.

I don't know a whole lot more about it but I will try to find some more info

---

### Post by warkro on 2007-01-10
what's your wireless card

---

### Post by shad0wslay3r on 2007-01-11
It doesnt really have a name... I bought it off of ebay.  When i was getting its info from terminal it says its a linksys

---

### Post by hscottyh on 2007-01-11
A quick google brought me to this page:
[http://people.debian.org/~pxt/nc6000/](http://people.debian.org/~pxt/nc6000/)

which has a link to a windows driver that works:
[http://cdgenp01.csd.toshiba.com/content/support/downloads/atheros_wpa_driver.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/atheros_wpa_driver.exe)

It's an exe, so you'll need cabextract to uncompress and extract it to get to the .inf file.

Hope this helps.

Note: Read the first link, looks like you may not need ndiswrapper and the windows driver. However, I would probably try that first.

---

### Post by shad0wslay3r on 2007-01-11
thanks!

I will give that a try

---

### Post by shad0wslay3r on 2007-01-11
now to figure out cabextract >.>

---

### Post by hscottyh on 2007-01-11
Or try the 4th post on this thread:
[http://www.ubuntuforums.org/showthread.php?t=287799&highlight=Atheros+5211](http://www.ubuntuforums.org/showthread.php?t=287799&highlight=Atheros+5211)

---

### Post by shad0wslay3r on 2007-01-11
thing is i'm not sure what the command is to extract files.. is it something like 

cabextract /desktop/blahblahblah?

---

### Post by hscottyh on 2007-01-11
Yes, exactly.

You may have to install cabextract, however first.

sudo apt-get install cabextract

---

### Post by shad0wslay3r on 2007-01-11
Thanks for all your help so far, but I have yet again a nother noobish question.

when i go into terminal, and i want to use the cabextract on the .exe, what do i type for the command if i have the file on my desktop?

i tried

cabextract /desktop/file.exe but that wasn't right.  ill keep trying some more combos, or wait until someone could point me in the right direction

---

### Post by shad0wslay3r on 2007-01-11
Anyone have an idea on what I'm supposed to do to extract the file?

---

### Post by shad0wslay3r on 2007-01-11
I know this is a noobish question but I don't know how to use cab extract and can't find any place that explains how to use it..

---

### Post by hscottyh on 2007-01-12
Sorry, the exe I pointed you to is not extractable with cabextract... There are no cab files in it. Use unzip instead, I did it on that file and it worked.

You may have to install unzip.
sudo apt-get install unzip

then:
unzip /somewhere/filetounzip.exe

I apologize for not checking it out first before telling you to use cabextract.

---

### Post by shad0wslay3r on 2007-01-20
not a problem, just been using wired connection until now.

will try that out

---

### Post by shad0wslay3r on 2007-01-20
well i have all of the drivers installed but.. wireless card still isn't showing up :-/

---

### Post by tturrisi on 2007-01-20
HOLD ON!
You MUST identify the card and model number and chipset BEFORE installing drivers.  Just because the card is not immediately recognized doe not mean "use ndiswrapper".

Put the card in the slot.  Open a terminal and find out what the card is:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Once you know what the chipset is then the correct driver can be located and used.  Don't go about this in a backward manner.

---

### Post by hscottyh on 2007-01-20
Good point and great link. I hope by trying to help I didn't do more harm than good.

---

