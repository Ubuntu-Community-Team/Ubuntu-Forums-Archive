---
title: "isn't detecting modem"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by Bob00037 on 2010-04-08
hi, i haven't any idea of what to do with any code.

my situation, i had winxp and could connect on dialup using 3 pieces of info:
username
pass
#

thats pretty much all i know off hand.

now.. when i go to kppp, it doesn't even detect my modem. what can i do? what do i need to know?

---

### Post by -humanaut- on 2010-04-09
First off what is the make and model of your modem? You're going to have to download the drivers to a usb key or something i'll look them up right now but I believe its wvdial

ok, just looked it up it is WVDial it will auto-detect your modem for you should be alot easier then kppp.

---

### Post by Bob00037 on 2010-04-09
well... i used kppp and i specified Dev2 as the COM location of the modem. now it just says it is Busy... and nothing happens. 




:(

---

### Post by Bob00037 on 2010-04-11
well, i looked up Wvdial and it looks like it is what i need, can someone point me in the right direction, 'cause i don't know what i'm supposed to do with it, but Kubuntu says it cannot find WVDIAL command... so now i am lost even moreso.

---

### Post by codemaniac on 2010-04-11
i always have had problems setting up modems in kde..knetwork managet suxxxxxxx..
use wvdial or better use nm-applet of gnome utilis...

---

### Post by Bob00037 on 2010-04-11
oh, alright. How do i get these utilities without internet on Kubuntu? i'm using XP to browse right now. and once i have them, how do i use them?

---

### Post by Nesaskewatch on 2010-04-11
I may be off base here, but I had a *lot* of fun getting dialup to work on ubuntu 9.04!  9.10 does _**not**_ have dialup support.  I'm not sure if Kubuntu is the same...  I used Gnomeppp however with great success.  9.04 only though.

Good luck!

---

### Post by lkraemer on 2010-04-12
We need the following questions answered:

1.  What Version Kubuntu?
2.  Win-modem or External Serial Hardware modem?
3.  USB Flash Drive Available?

Try:
[http://keryxproject.org/download/](http://keryxproject.org/download/)

for downloading with XP, and then copy the files to Kubuntu.

Then try:
[http://ubuntuforums.org/showthread.php?t=1425279&highlight=Dependencies](http://ubuntuforums.org/showthread.php?t=1425279&highlight=Dependencies)
Posting #4

It works with 8.04.xx and 9.10 for sure.  Same method should work for
any version.  You just need the dependencies, and wvdial.

If it is a Win-Modem then you are going to need the help of the folks
at [www.linmodems.org](www.linmodems.org).  Marvin and those folks know what they
are doing when it comes to a Win-Modem.  But I wouldn't go that route.
You need to go to the [http://www.linmodems.org/](http://www.linmodems.org/) site, then download
the ScanModem.tool and execute that script to get the information
on the modem. Then subscribe to the Linmodems discussion list.
Then send Marvin an email (in plain text....ONLY) to the discussion
list. He will analyze your results and get back to you on what to
do to get the correct drivers to get the Modem working.

You can also search the archives posted there for your Modem and read
those messages about how others have tried to get theirs working.
Use EDIT then FIND for your modem and search each month for responses
to keep from pouring over each months' ton of postings.

And your Dialup service needs to be one that Linux works with.  I use
Copper.net, but others also work.  Search the forum for Linux Dialup ISP's.

Shouldn't take more than ~30 minutes, unless you try the win-Modem,
and then you are looking at days.....

Another ref:
[http://ubuntuforums.org/showthread.php?t=1332211&highlight=Dependencies](http://ubuntuforums.org/showthread.php?t=1332211&highlight=Dependencies)
Posting #2.

lk

---

