---
title: "Broadcom Wireless on zv6000 w/8.04"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by jbaerbock on 2008-06-01
So I got this working fine in gutsy via a script I found online however this time I clicked the box in the restricted drivers and my card seems detected but when doing iwlist scanning in terminal nothing is listed (and I know there are at least some encrypted wireless points around here. Any ideas?

---

### Post by jbaerbock on 2008-06-01
And I am officialy a dingbat lol. I decided what the hey and re-checked the box in the restricted drivers. Well my problem before was that aparantly the wireless points were all down or something. Now I do see one though so I think it should be working now. What a wierd thing (used to be tons of encrypted ones around here a few months back)

---

### Post by genesiss on 2008-06-10
can you share the script???
I am about to try 8.04 on my zv6000
thanks

:guitar:

---

### Post by Ayuthia on 2008-06-10
> **genesiss said:**
> can you share the script???
I am about to try 8.04 on my zv6000
thanks

:guitar:
I am not for sure about the Gutsy script, but the restricted driver is now found at System->Administration->Hardware Drivers.  The Gusty scripts might not work either because NDISwrapper has changed a little bit because of the new kernel changes.  Here is a link that might work for you:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
It is a guide for NDISwrapper on Hardy.  It seems to work pretty well for most people.

---

### Post by jbaerbock on 2008-06-10
yeah no script just go to the restricted drivers thing and check the box by the wireless. And bingo it auto installs.

---

### Post by genesiss on 2008-06-10
ok thanks
will try it and report back !
:)

---

### Post by genesiss on 2008-06-10
just finished installing Ubuntu 8.04
I enabled the driver but I still cannot 
connect, what am I doing wrong??

---

### Post by genesiss on 2008-06-10
Hey good news for me!!!
just found out what I did wrong and fixed it
when installing the driver I forgot to fetch the
firmware... well then I did it, and now it is working
but here is question, when I tried to to connect using the 
network connect dialog ( the one on the side of the clock ) 
it  would not connect, I could only do it using the System -
Admin - network ( and doing it manually) how can I fix this??
also is there a way of detecting a wireless network connection?, 
as in when I go to to an Internet Cafe...
thanks

---

### Post by Ayuthia on 2008-06-11
> **genesiss said:**
> Hey good news for me!!!
just found out what I did wrong and fixed it
when installing the driver I forgot to fetch the
firmware... well then I did it, and now it is working
but here is question, when I tried to to connect using the 
network connect dialog ( the one on the side of the clock ) 
it  would not connect, I could only do it using the System -
Admin - network ( and doing it manually) how can I fix this??
also is there a way of detecting a wireless network connection?, 
as in when I go to to an Internet Cafe...
thanks
There seems to be problems with Network Manager sometimes.  You might try a different manager like Wicd ([http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)) or wifi-radar.

For scanning manually, you can use sudo iwlist scan.  The sudo seems to help it refresh the scan because it goes into admin mode.  Here is a like by kevdog that helps you figure out how to do things manually:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by genesiss on 2008-06-11
Thanks..
will report back as soon as I fix it
thanks again

---

