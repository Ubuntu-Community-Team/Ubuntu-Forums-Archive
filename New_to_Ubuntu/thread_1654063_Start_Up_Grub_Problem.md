---
title: "Start Up Grub Problem"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Webster12 on 2010-12-27
Hi,

So I was trying to open my laptop this morning and it took me a while to do so....but it did't look normal and it froze...so I restarted.

And it took forever...snd it is not loading.

I was led to...something that says.

GNUE GRUB VERSION 1.98+20100804-5UBUNTU3

*IN BOX*
UBUNTU, W/ LINUX 2.6.35-24-GENERIC
UBUNTU, W/ LINUX 2.6.35-24-GENERIC  (RECOVERY MODE)
UBUNTU, W/ LINUX 2.6.35-22-GENERIC
UBUNTU, W/ LINUX 2.6.35-22-GENERIC  (RECOVERY MODE)
mEMORY TEST (MEMTEST86+)
MEMORY TEST (MEMTEST86+, SERIAL CONSOLE 115200)

USE *UP* AND *DOWN* KEYS TO SELECT WHICH ENTRY IS HIGHLIGHTED.
PRESS ENTER TO BOOT THE SELECTED OS, 'E' TO EDIT THE COMMENDS BEFORE BOOTING OR 'C' FOR A COMMAND LINE.

I did some updates yesterday buy i've restarted it twice and all looked well...not sure why this is happening now.

Please help. thanks in advance.

---

### Post by drs305 on 2010-12-27
Does it boot if you select one of the options?

It could be that Grub2 is detecting a problem and doesn't proceed automatically to allow the user to select the option he/she wants. It accomplishes a 'recordfail' check and if it detects a problem it won't boot automatically.

If you post the contents of the RESULTS.txt from the boot info script we can see if there is a problem with the boot files:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by amjjawad on 2010-12-27
Oh, it's you again? :)
I'm sorry you have another problem in a very short time.

Please follow drs305's instructions and/or answer his questions :)

---

### Post by Webster12 on 2010-12-27
well i've tried the first 2. 

1st one says error because i do not have /sbin/init

second one says, 'no init found' try passing init= bootarg
(initramfs)

---

### Post by Webster12 on 2010-12-27
> **amjjawad said:**
> Oh, it's you again? :)
I'm sorry you have another problem in a very short time.

Please follow drs305's instructions and/or answer his questions :)


lots of bad luck for me these days... :(

---

### Post by wilee-nilee on 2010-12-27
> **Webster12 said:**
> lots of bad luck for me these days... :(

Post the bootscript as suggested.:)

---

### Post by drs305 on 2010-12-27
For a possible quick fix, try highlighting the first entry in the Grub2 menu, press "e", remove the "search" line completely and change the UUID in the linux line to "... root=/dev/sdXY" ... then CTRL-x and see if it boots.

Change XY to your Ubuntu partition (sda5, etc).

---

### Post by Webster12 on 2010-12-27
> **drs305 said:**
> 

If you post the contents of the RESULTS.txt from the boot info script we can see if there is a problem with the boot files:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

I am not sure how to accomplish this...it won't log me in.

---

### Post by amjjawad on 2010-12-27
> **Webster12 said:**
> lots of bad luck for me these days... :(

Nuh, it happens.
Just follow drs305's post as he asked you to post the result of the boot script :)
All the instructions you need are inside that [link]("http://bootinfoscript.sourceforge.net/").

---

### Post by Webster12 on 2010-12-27
it says

No init found. Try passing init...
busybox v1.15.3 .... built in shell (ash)

Am I suppose to just remove  UUID?

---

### Post by amjjawad on 2010-12-27
> **Webster12 said:**
> I am not sure how to accomplish this...it won't log me in.

[http://ubuntuforums.org/showpost.php?p=10284224&postcount=12](http://ubuntuforums.org/showpost.php?p=10284224&postcount=12)

There you go!

---

### Post by Webster12 on 2010-12-27
Thanks a lot,man...if this takes a while im going to have to put this aside...i hven;t slept in 2 days...

and if i ask my cousin for help....he's going to install w7(which may not be a bad idea)....and i am going to get a lot of lecture for installing ubuntu..linux...because he told me not to...

---

### Post by amjjawad on 2010-12-27
> **Webster12 said:**
> Thanks a lot,man...if this takes a while im going to have to put this aside...i hven;t slept in 2 days...

and if i ask my cousin for help....he's going to install w7(which may not be a bad idea)....and i am going to get a lot of lecture for installing ubuntu..linux...because he told me not to...

What are you waiting for? switch your machine off and go to sleep :)

Ubuntu will not fade away so take your time ;)

---

### Post by Webster12 on 2010-12-27
> **amjjawad said:**
> What are you waiting for? switch your machine off and go to sleep :)

Ubuntu will not fade away so take your time ;)

yea...i think i'm going to go to sleep...I was so close...but doesn't look like the TRY UBUNTU will work anytime soon...

I will give this a try tomorrow when I get home. Thanks much for your help....I cannot believe I understood what you are saying...

also for drs' help...thank you..will let you guys know what happens.

by the way, can I use the 8.10 live cd to get that...i think that one loads faster...or it really has to be 10.10?

---

### Post by amjjawad on 2010-12-27
> **Webster12 said:**
> yea...i think i'm going to go to sleep...I was so close...but doesn't look like the TRY UBUNTU will work anytime soon...

I will give this a try tomorrow when I get home. Thanks much for your help....I cannot believe I understood what you are saying...

also for drs' help...thank you..will let you guys know what happens.

by the way, can I use the 8.10 live cd to get that...i think that one loads faster...or it really has to be 10.10?

You're most welcome.

If your machine can boot from an USB, try to create a LiveUSB and it will be much faster.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Step#2

or use: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Now, go to sleep :)

---

### Post by drs305 on 2010-12-27
> **Webster12 said:**
> by the way, can I use the 8.10 live cd to get that...i think that one loads faster...or it really has to be 10.10?

If it's a Grub2 problem the 8.10 CD won't work as it used Grub legacy. You can run the boot info script and perform file operations but it won't allow you do do any automatic updates of the Grub2 files unless we get creative with the sources.list.

---

