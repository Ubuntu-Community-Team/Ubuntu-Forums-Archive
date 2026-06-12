---
title: "New to Ubuntu..."
date: 2011-06-06
forum: New to Ubuntu
---

### Post by mrawson on 2011-06-06
Hello everyone :D

(very) new user here, burned Linux to CD as instructed, I boot with CD:

-shows a plain purple screen with a little graphic of a keyboard and a person in a ring on it.

-screen goes blank for ages, no mouse, keyboard, or any input whatsoever.

-then my mouse appears, and shortly afterwards a login screen turns up. I have control of mouse, keyboard, but absolutely no idea for the username and password, as it never asked for me to create an account...have run the CD several times, same effect each time.
Not a complete software idiot, just a Linux newbie. :(

Have googled the problem, no hits.
(trying) to use natty narwhal, on an XP computer.

Any help is much appreciated, and if you want more detail, I can supply that.
Oh, btw, I'm a teenager, so don't expect too much of me please!

---

### Post by Mr. Shannon on 2011-06-06
You could try using the alternate installer found [[COLOR="Navy"][COLOR="Blue"]here[/COLOR][/COLOR]]("http://www.ubuntu.com/download/ubuntu/alternative-download").  Also remember to burn the disk on a slow speed.

---

### Post by alphacrucis2 on 2011-06-06
> **mrawson said:**
> Hello everyone :D

(very) new user here, burned Linux to CD as instructed, I boot with CD:

-shows a plain purple screen with a little graphic of a keyboard and a person in a ring on it.

-screen goes blank for ages, no mouse, keyboard, or any input whatsoever.

-then my mouse appears, and shortly afterwards a login screen turns up. I have control of mouse, keyboard, but absolutely no idea for the username and password, as it never asked for me to create an account...have run the CD several times, same effect each time.
Not a complete software idiot, just a Linux newbie. :(

Have googled the problem, no hits.
(trying) to use natty narwhal, on an XP computer.

Any help is much appreciated, and if you want more detail, I can supply that.
Oh, btw, I'm a teenager, so don't expect too much of me please!

That is odd. The live CD should not require you to login. Maybe your burn is corrupt. Try to burn the iso again at lower speed. Also a good idea to verify the md5 hash of the iso to make sure it downloaded ok. Don't expect speed when loading from live CD as CD/DVD drives are vastly slower than hard disk, especially doing seeks.

---

### Post by wildmanne39 on 2011-06-06
> **mrawson said:**
> Hello everyone :D

(very) new user here, burned Linux to CD as instructed, I boot with CD:

-shows a plain purple screen with a little graphic of a keyboard and a person in a ring on it.

-screen goes blank for ages, no mouse, keyboard, or any input whatsoever.

-then my mouse appears, and shortly afterwards a login screen turns up. I have control of mouse, keyboard, but absolutely no idea for the username and password, as it never asked for me to create an account...have run the CD several times, same effect each time.
Not a complete software idiot, just a Linux newbie. :(

Have googled the problem, no hits.
(trying) to use natty narwhal, on an XP computer.

Any help is much appreciated, and if you want more detail, I can supply that.
Oh, btw, I'm a teenager, so don't expect too much of me please!
Hi, also if your system allow you to boot from usb you can create a boot usb stick and boot from it, I tried that the other day and the usb stick boot and ran almost like having it on my hard drive it work much better then the livecd.

---

### Post by DogMatix on 2011-06-06
I have heard of issues similar to this you could try

user: ubuntu
pass:<none> just hit enter

---

### Post by collisionystm on 2011-06-06
> **mrawson said:**
> Hello everyone :D

(very) new user here, burned Linux to CD as instructed, I boot with CD:

-shows a plain purple screen with a little graphic of a keyboard and a person in a ring on it.

-screen goes blank for ages, no mouse, keyboard, or any input whatsoever.

-then my mouse appears, and shortly afterwards a login screen turns up. I have control of mouse, keyboard, but absolutely no idea for the username and password, as it never asked for me to create an account...have run the CD several times, same effect each time.
Not a complete software idiot, just a Linux newbie. :(

Have googled the problem, no hits.
(trying) to use natty narwhal, on an XP computer.

Any help is much appreciated, and if you want more detail, I can supply that.
Oh, btw, I'm a teenager, so don't expect too much of me please!


where did you get your cd? I have never been prompted for a login lol

---

### Post by coffeecat on 2011-06-06
If the live CD asks you to login first time around, it usually means it is faulty. This is not uncommon as a problem. Possibly a bad burn, a corrupted ISO or simply dust on the CD. The login details for the live CD (and live USB) are:

username = ubuntu
password = blank (just press enter).. **EDIT**: just noticed DogMatix already posted the login details. :)

These work if you logout and into a live session but usually do not if you are prompted when booting up, simply for the reason stated above.

Check the md5sum of the downloaded ISO. See here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that's OK, burn another CD, but at a low speed. I always use x4.

---

### Post by DevilSolution on 2011-06-06
> **mrawson said:**
> Hello everyone :D

(very) new user here, burned Linux to CD as instructed, I boot with CD:

-shows a plain purple screen with a little graphic of a keyboard and a person in a ring on it.

-screen goes blank for ages, no mouse, keyboard, or any input whatsoever.

-then my mouse appears, and shortly afterwards a login screen turns up. I have control of mouse, keyboard, but absolutely no idea for the username and password, as it never asked for me to create an account...have run the CD several times, same effect each time.
Not a complete software idiot, just a Linux newbie. :(

Have googled the problem, no hits.
(trying) to use natty narwhal, on an XP computer.

Any help is much appreciated, and if you want more detail, I can supply that.
Oh, btw, I'm a teenager, so don't expect too much of me please!


are you running the cd from boot or from inside xp? if your running from boot, as far as im aware you get a screen asking which type of boot you want, i.e. full install, practice run, memory test, safe mode etc... my presumption (although im also a linux newb) is that perhaps whatever graphics card you are using is not loading properly during this screen and is then automatically choosing the "practice run" option after some sort of time await.

The best solution i can think of if this is the case is if you have a new graphics card installed (any AGP,PCI-E etc) then just temporarily take it out and use the built in graphics that almost every PC has.

If however your using the built in graphics already then my presumption is your disk image isnt honest (I.E you've downloaded a modded iso image with a built in user and no install option), this means get the official ISO from ubuntu not a 3rd party website.

if the 2 above proposals are void(it is the official download and your graphics card/built in graphics should be 100% readable by ubuntu) then it could simply be down to a bad CD such that you need to re-burn a new disk. i would suggest a parity checker for good measure but it doesnt matter a great deal

hope this helps

Also if you do manage to install it and your graphics card needs 3rd party drivers (this is usually the case) you may not be able to boot into unity or classic ubuntu(gnome), my solution was to boot into classical(without special effects) and then install the 3rd party drivers from the additional-drivers program located in system > administration > additional-drivers

*forgot to mention* you do this during logon, you select the user and then at the bottom a few option pop up, the one your after is towards the bottom right

---

### Post by mrawson on 2011-06-07
Thank you, all who replied. Haven't quite worked out the md5sum checker thingy yet, so will try another cd/memory stick/login as ubuntu/try and find original graphics card.

Sorry if I'm late replying, not through lack of compunction, couldn't find my thread, originally posted somewhere else, it got moved, I lost it, my own fault.

 Any way, thankyou for posting, really good to ha :Dve support

---

### Post by mike555 on 2011-06-07
Yes, this forum moves quickly, you might just hit the "search" and " find all your posts" ..............

---

