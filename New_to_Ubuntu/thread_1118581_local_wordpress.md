---
title: "local wordpress"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by halberdiyiv on 2009-04-07
I've been installing wordpress locally under lampp several times, all works fine but only last for one or two days. one/two days after lampp+wordpress installed, my computer act really bad (im using asus p5pe mainboard), it keeps shutting down by itself. moreover, unsafe shut-down keep happen even after i uninstall those softwares and I have to pay repair service for damage inflicted. Can anybody tell me what is wrong, and suggest how to deal with it?

note: i've been trying to keep my computer clean from lampp+wordpress for several days for electricity problem, and there is none. i've also been trying to keep my computer free from unknown application before and after installing lampp+wordpress, but shut down still happen.

---

### Post by Joeb454 on 2009-04-07
Does it still shutdown when you don't have wordpress installed? I can't see any reason wordpress or lamp would shutdown the PC

---

### Post by halberdiyiv on 2009-04-07
my computer stop shut down by itself about few startups after uninstalling lampp.
(uh, I use lampp, or better said, xampp for linux. not lamp stack provided in synaptic for convenient purpose)

---

### Post by Malalo on 2009-04-07
Could this be a memory issue ?
Have your computer boot with the CD (not on the hard drive) and try the memory test option. Let it run for (sadly) a few hours, just to be sure...

---

### Post by dacorr on 2009-04-07
look in /var/log/

system logs and service logs are held there they should give you an idea as to what caused the shutdown.

Dac

---

### Post by halberdiyiv on 2009-04-15
i evaluate system log from system > administration > system log
almost (or should i say always?) unsafe shutdown are preceded by cron. this is the message:
Apr 15 02:09:01 desk02 /USR/SBIN/CRON[6136]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

i also do memory test using ubuntu CD. the computer shutdown the same way when the test reaches random memory test (it's about 5 to 7 minutes after the memory test started).

i don't have any idea of what have been happening. any clues and problem solver? thanks!

---

### Post by nandemonai on 2009-04-15
> **halberdiyiv said:**
> i evaluate system log from system > administration > system log
almost (or should i say always?) unsafe shutdown are preceded by cron. this is the message:
Apr 15 02:09:01 desk02 /USR/SBIN/CRON[6136]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

i also do memory test using ubuntu CD. the computer shutdown the same way when the test reaches random memory test (it's about 5 to 7 minutes after the memory test started).

i don't have any idea of what have been happening. any clues and problem solver? thanks!

Hardware issue then without doubt.

It could be a temp issue. Check BIOS and monitor if your CPU is running at a high temperature.

If it's not that then it's likely something is dying.

Either your memory is on it's way out (likely), the power supply is on it's way out (likely) or worse your motherboard or CPU is on it's way out. The latter two being rarer. Especially CPU.

If you're comfortable opening up the computer, have a look at the motherboard and check to see if any capacitors have popped. They're usually the first thing to go on a motherboard.

Like so: [http://www.jebswebsite.com/misc_pics/ibm_mobo_capacitors.jpg](http://www.jebswebsite.com/misc_pics/ibm_mobo_capacitors.jpg)

---

### Post by halberdiyiv on 2009-04-15
I have replace my power supply two weeks ago, then it make the memory being the main issue. thank you very much. i will immediately fix the problem.

---

