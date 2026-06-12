---
title: "Lots of error (?) messages during boot ... how do i see them?"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by anothernewuser on 2010-05-19
Well .. I'm struggling with a system that seems to be unstable anytime any sort of media is played and I've recently noticed a stream of what seems to be error messages that scream up the screen too fast to read just before the graphical interface pops up to let me log in.


Is there some way to access that information?  Is it automatically stored somewhere or ... can I pause the boot somehow ... or can I get the info to be dumped somehow?

Any advice is better than what I can do so far.

Thanks for any and all advice.


Oh geez ... forgot to say its 10.04 a recent upgrade from 8.04.

---

### Post by ubunterooster on 2010-05-19
Try going to the ".xsessionerrors" file that is hidden in your home folder?

---

### Post by drs305 on 2010-05-19
Newer versions of Ubuntu provide an easy way to access message logs via System, Administration, Log File Viewer. Logs such as dmesg, messages, etc are available for viewing. Since you are interested in what's happened before you log in the logs you are interested in are probably in the system log folders (/var/log), which is where these log files reside.

---

### Post by anothernewuser on 2010-05-19
Well thank you muchly for offering advice :)


okie dokie ... I managed to pull that file into open office and I see errors  - which dosen't comfort me - but they're not the error I can just glimpse flying by ... this seems to be mostly information about things I don't have installed I think ...


The error I want to read is some sort of warning about an I/O error that repeats itself and fills the screen literally just before the login screen pops up but it goes by toooooo fast for me too read...

Anywhere else you think I could look for that?


Alright checking logfiles now .. y'all are answering quick ;)

Dear god there's a lot of them

---

### Post by -humanaut- on 2010-05-19
You can try opening a terminal as soon as you log in and typing: dmesg

---

### Post by anothernewuser on 2010-05-19
Hmmmm ... pretty sure i found it ...


[   19.512539] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   19.512546] sr 3:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   19.512553] sr 3:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   19.512562] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   19.512577] end_request: I/O error, dev sr0, sector 0
[   19.512639] Buffer I/O error on device sr0, logical block 0
[   19.515192] type=1505 audit(1274314311.523:2):  operation="profile_load" pid=543 name="/sbin/dhclient3"
[   19.515935] type=1505 audit(1274314311.523:3):  operation="profile_load" pid=543 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.516358] type=1505 audit(1274314311.527:4):  operation="profile_load" pid=543 name="/usr/lib/connman/scripts/dhclient-script"
[   19.517065] sr 3:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   19.517072] sr 3:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   19.517078] sr 3:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[   19.517088] sr 3:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   19.517102] end_request: I/O error, dev sr0, sector 0
[   19.517164] Buffer I/O error on device sr0, logical block 0


and then it literally repeats some combination of those last 6 lines dozens and dozens of times ...  eventually dropping out the line about "Buffer I/O error" and changing the string of numbers (28 00 00 00 00 00 00 00 02 00) 3 lines up and varying the sector numbers ...

So thank y'all for helping me find it - the info I need does indeed appear to be located in the dmseg logfile.


The messages logfile has similar looking entries ... dozens and dozens of them possibly hundreds

Now ... the next step is ....

How can I find out what all this means if anything?

This message wasn't there after I upgraded but it is now every time I boot.

---

### Post by drs305 on 2010-05-19
This sounds like a CD or DVD  or drive issue. Do you have a disk inserted during boot? Have you switched cables on your devices lately? Are your drives all working correctly (or did they)?  I'll have to leave the specifics to others on this one.

---

### Post by anothernewuser on 2010-05-19
Siiiiiiiiiiiiiiigh ... drive issues ...


been wrestling with them nonstop for days  ([http://ubuntuforums.org/showthread.php?t=1484579](http://ubuntuforums.org/showthread.php?t=1484579))


oh well ... 

and ummm yes ... I had a CD in the drive when it booted.



Thanks for your help :)


Hmmm ... the question posed in the thread title was solved but the problem is just beginning ... i'll ponder if this is [Solved] for a few minutes.

---

