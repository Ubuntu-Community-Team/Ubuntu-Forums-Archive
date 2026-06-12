---
title: "How do I make a full crash report after a hardware restart?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-30
Hi

I am now getting frequent crashes on my 64bit system having managed to get it to the point of being stable with the help of the forum over a period of about a month.

The system just hangs. I can't do anything other than press the start button on my pc for a couple of seconds until it turns off, then turn on again.

The annoying bit is that the system appears oblivious to the crash and offers no means of reporting it. How can I capture what is happening at the time of the crash to report to the developers and hopefully achieve a fix?

---

### Post by Didius Falco on 2009-04-30
Look up above your post in the light green box. It has a link that explains how to do it.

Good luck getting your problem resolved...

---

### Post by bwallum on 2009-04-30
> **Didius Falco said:**
> Look up above your post in the light green box. It has a link that explains how to do it.

Good luck getting your problem resolved...

Thanks Didius, I have tried that route but it is not that helpful when the system crashes completely. I can report manually but to be effective I need to report the module that it occurred in. I was hoping that I could pick up a log file that named all running processes and ideally named the process that caused the crash. I tried the ddebs repository and got somewhere towards running a debug routine but became lost, hence my query.

If you know how to set up a process that monitors and reports continuously to a file, then I could find the file once the system was recovered and send it with the bug report. That is what I would like to do.

Thanks for your help
Bob

---

### Post by philinux on 2009-04-30
Did apport catch the crash. If so there will be a report in /var/crash.

Double clicking a report will fire up apport again.

For hard lock up try alt sysrq K. This will kill x and take you to the login window. Or if that fails alt sys rq REISUB.
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Better than the power button as this can cause more damage.

---

### Post by bwallum on 2009-04-30
> **philinux said:**
> Did apport catch the crash. If so there will be a report in /var/crash.
Unfortunately not. I have found something called .xsession-errors though, a text file in my /home/me directory. It has some stuff in but is difficult to work out.

> For hard lock up try alt sysrq K. This will kill x and take you to the login window. Or if that fails alt sys rq REISUB.
[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Better than the power button as this can cause more damage.
Excellent tip. I had the opportunity to try it out when my system hung trying to reply to you! It's the first time a hang has been useful!

The alt key does not work for me. The AltGr does however. I held down the AltGr key whilst pressing SysRq key and then k. Nothing happened. This worked though:-> Hold down AltGr then press the following keys: SysRq r e i s u bThe system rebooted nicely without having to press the power button. Thank you very much for that tip.

---

### Post by Didius Falco on 2009-04-30
If you go to **System/Administration/System Log** you will find a whole series of log files that should help track the cause of the lockup.

---

### Post by bwallum on 2009-05-01
> **Didius Falco said:**
> If you go to **System/Administration/System Log** you will find a whole series of log files that should help track the cause of the lockup.Another good tip, thanks Didius! I found lots of logs at System>Administration>Log File Viewer. All can be copied to plain text files.

I tried System>Preferences>Main Menu and under System Tools checked the Report a problem.. app. It appeared in my Applications>System Tools menu and started to run minimised when selected, but then just died before a gui was brought up.

There has to be an easier way for non techies to report crashes which are all too frequent and very frustrating.

---

