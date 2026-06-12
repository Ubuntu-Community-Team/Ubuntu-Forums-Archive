---
title: "Connecting to cisco swtich using minicom"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by Mrwasab1 on 2008-08-27
Hi guys,
I am trying to connect to my Cisco Catalyst 2900XL switch via the console port. I have the an authentic console cable, which works as i have been configuring the switch on a windows box up until now.

I installed minicom and set it up as described [here](http://useopensource.blogspot.com/2007/01/using-cisco-console-in-linux.html) but no luck. Minicom starts up but it wont connect.
If i press CTRL A at the bottom it says i am online, but i dont see a login prompt or anything.

I installed Putty as well, and i get the same result, a blank screen. I wanted to make sure it wasnt the cable or the switch, so i plugged it into a windows machine running putty and it works perfectly.

Any ideas?

---

### Post by puppywhacker on 2008-08-27
When you connect the serial cable to an already running system the terminal output is not refreshed, so it is logical that you don't see anything when you connect it to a running system. Try restarting the router and it should show you the full boot sequence. or you could hit "enter" a few times to see if you get a response

A common problem is that the port settings are wrong. I thought /dev/ttyS0 is the COM1. I'm guessing the speed should be 115200 (9600 or 38400 are pretty common as well) with 8-N-1 ... You have to know the speed setting on the router or try all the possibilities

use "minicom -s" and select "serial port setup"

---

### Post by mips on 2008-08-27
Using the right tty device?

Double check your config just to be certain.

---

### Post by Mrwasab1 on 2008-08-27
The documentation i have read from Cisco and other sources says that the baud rate should be 9600 and be 8N1 and that my com 1 is /dev/ttyS0 so these settings are in minicom and also putty.
i have pressed enter to the point where ive damaged the key, ive connected it to COM 2 and changed the settings to /dev/ttyS1 still no luck, so im running out of ideas. I might try to reboot the switch with the console cable plugged in, but apart from that, i have no clue

---

### Post by ModelM on 2008-08-27
I'm not a Cisco guy but you might check what the device requires as a line terminator - cr, lf, or cr/lf - & make sure that's what's being sent. I just went through a similar situation here & that was the problem.

I also found that cutecom was much better suited to my needs, you might want to check that out, also.

---

### Post by bballa23523 on 2008-08-27
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by puppywhacker on 2008-08-28
maybe the speed settings have been changed from the default, or maybe console access has been disabled or one the pins is broken. those rs232 ports have always been a pain. :(

---

### Post by timcredible on 2008-08-28
you want 9600, 8N1 for all cisco console ports.  you want /dev/ttyS0 for your serial port on your pc (equivalent to COM1 in windows).  i use kermit, and here's what i put in when connecting to ciscos:

```
set line /dev/ttyS0
set carrier-watch off
connect
```
the 9600, 8N1 is default in kermit.  the package in the repos is ckermit.

---

### Post by sles on 2008-09-03
We have the same problem on several computers since upgrade to 8.04 from 7.10 and 6.06- it is impossible to connect to any cisco hardware over /devv/ttyS0 using minicom or something else.
If we start minicom before powering on cisco switch- we see it's boot messages, but then our input doesn't reach switch.
Looks like ubuntu kernel bug.
I created bug report, but it is ignored.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246844](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246844)

---

### Post by shazbut on 2008-09-03
Have you tried gtkterm, it's fairly basic but works for me?  It's listed as "serial port terminal" under add/remove.  It's working for me using /dev/ttyS01, 9600, no parity, 8bits, 1 stop, no flow control.

---

### Post by sles on 2008-09-03
> **shazbut said:**
> Have you tried gtkterm

yes, the same problem.

---

### Post by Mrwasab1 on 2008-09-04
> **timcredible said:**
> you want 9600, 8N1 for all cisco console ports.  you want /dev/ttyS0 for your serial port on your pc (equivalent to COM1 in windows).  i use kermit, and here's what i put in when connecting to ciscos:

```
set line /dev/ttyS0
set carrier-watch off
connect
```
the 9600, 8N1 is default in kermit.  the package in the repos is ckermit.

tried this, didnt work, i just get a blinking cursor and no connection to the switch. 

As i said the switch and cables work fine as my windows box can access it with no problems.

Might try the new kernel for 8.10 as suggested in the bug report, but would appreciate it if someone else that posted in the bug report could give their findings, as i cant afford for this server to be experimental at this stage.

---

### Post by sles on 2008-11-01
Just upgraded my box to 8.10- absolutely the same problem.
I connected zyxel modem to com port and I see that it's data lamp blinks when I type something in minicom or gtkterm, or it blinks more on command with response, but I get nothing from modem!
This is, I'm shure, kernel bug, and it exists since 8.04.
I can't understand why there is no fix for it...

---

### Post by octobuntu on 2010-11-20
Hello all, I had a similar problem. To resolve, I just had to make sure that the settings were right for Cisco:

sudo minicom -b 9600 -D /dev/ttyS0


That was for me using a rollover cable to connect to the switch. Cisco likes the settings of: 9600 baud 8N1. Minicom tried to default to modem /dev/tty8 or something. also you can find your available console devices with the command

dmesg |grep tty

---

### Post by PeteLong on 2011-02-18
Hi All, Just did this it may be of help to anyone following up :D

[Ubuntu - Managing Cisco Devices via Serial / Rollover Cable]("http://www.petenetlive.com/KB/Article/0000400.htm")


Pete
[PeteNetLive]("http://www.petenetlive.com")

---

### Post by tdrusk on 2011-04-14
> **PeteLong said:**
> Hi All, Just did this it may be of help to anyone following up :D

[Ubuntu - Managing Cisco Devices via Serial / Rollover Cable]("http://www.petenetlive.com/KB/Article/0000400.htm")


Pete
[PeteNetLive]("http://www.petenetlive.com")
Awesome! I can vouch that this works for me under Debian Squeeze. :)

---

