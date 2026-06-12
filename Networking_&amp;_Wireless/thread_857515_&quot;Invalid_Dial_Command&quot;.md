---
title: "&quot;Invalid Dial Command&quot;"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by Drakelet on 2008-07-12
You may have seen from my countless other threads, I'm having problems getting Hardy online with a dial up connection.

For the background, here's some:
[http://ubuntuforums.org/showthread.php?t=787062&page=2](http://ubuntuforums.org/showthread.php?t=787062&page=2)

I have a BT Enabler serial hardware modem, connected via USB to serial cable.
I know the modem works with Ubuntu because a person in the above thread has it working.

I've tried pppd, wvdial and GnomePPP, and none work.

For wvdial/GnomePPP, I get the following problem:
[img]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/FFSserialbtenabler.gif[/img]
"Invalid Dial Command".

I did sudo wvdialconf, and wvdial.conf was automatically set up for the modem.  GnomePPP also detects the modem, so that's definitely not the problem.
I changed the phone, username and password to the correct ones, and I got the above problem.  I've tried editing wvdial.conf lots, changing the Dial Command (ATM#L#DT, ATDT, ATI# and lots more, where # is a number 1-9).  No luck.  Added Stupid Mode and various other things I found, changed Baud, and more.  Still nothing.
The Inits work though.

I tried "echo ATDT0001112222 > /dev/ttyUSB0", and nothing happens.  Heard something should happen if it works... or something.

Currently I'm thinking either it's a hardware problem or something wrong with my connection number.

Any thoughts?  ALL help is welcome and wanted!!  I've been trying to get this working for months now.

---

### Post by Drakelet on 2008-07-13
Done some Googling, can't find anything (much).

I'm relying on you people!

---

### Post by kri_vijay on 2008-11-21
I had the same problem. I enable HSDPA on my pda phone (I used KaiserTweak to enable it in the phone registry)

---

### Post by pabouk on 2009-02-19
In the Connection Log the modem replies with "ERROR" to the dial command. It means that the dial command contains some parts which are not recognized by the modem. I encountered the same problem and currently I am investigating where is the dial command defined.

**EDIT:**
I have found the solution. It is really a problem of gnome-ppp which does not allow you to configure the dial command. The solution is to switch the modem type to ISDN and to add DT in front of the phone number. See [http://ubuntuforums.org/showthread.php?t=318328](http://ubuntuforums.org/showthread.php?t=318328)

---

