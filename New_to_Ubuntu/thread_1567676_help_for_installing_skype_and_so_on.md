---
title: "help for installing skype and so on"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by soramia on 2010-09-04
hi! maybe it is not the righy forum, but please help me!
i am new linux user, after 20 window's years and it's very difficult for   me:

[LIST=1]
[*] i've tried to install skype   and it appears the error
[LIST=1]
[*]error:   dependency is not satisfiable libasound2
[/LIST]
 
[*]i received the upgrading from 8.04 version to 10.03.1 version. i   created the cd and, after restarting the pc....error
[LIST=1]
[*]E: Unable to locate any  package   files, perhaps this is not a Debian Disc
[/LIST]
 
[*]i have an external hard disk. i plugged it in the usb port and....   error:
[/LIST]
[INDENT]It's not possible to mount the drive

[/INDENT]I am crazy....i would format everything and reinstall   windows...but i want to win!
can you help me?
thank you
rosa:popcorn:):P


P.s. sorry for my english....i am italian!

---

### Post by mikewhatever on 2010-09-04
Would be interesting to see your sources list. What's the output of the command below?

cat /etc/apt/sources.list

---

### Post by soramia on 2010-09-04
deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

---

### Post by ronnielsen1 on 2010-09-04
NOT[COLOR=Blue] cat/etc/apt/sources.list[/COLOR]

BUT [COLOR=Blue]cat /etc/apt/sources.list[/COLOR]

You forgot the space

---

### Post by soramia on 2010-09-04
i wrote sudo before and the response is

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

---

### Post by ronnielsen1 on 2010-09-04
Are you trying to install skype from a downloaded version? What happens when you type sudo apt-get install skype in a terminal?

---

### Post by soramia on 2010-09-04
i'm trying....something happens...it's installing something.....:)

---

### Post by soramia on 2010-09-04
YYYYYYYYYYYYEEEEEEEESSSSSSSSSSSSS!!!
SKYPE WORKS
even if the version for windows is better and more beautiful!
but there is only one version for linux?

please, can you help me even for my other problems!
thank you, thank you so so much!
rosa:D

---

### Post by ronnielsen1 on 2010-09-04
You're running hardy. If you download a newer package off of the internet, it might need newer lib files than the ones that hardy uses. Unless you just need the latest and greatest, it's best to check synaptic or terminal first to make sure there's not a package already available

---

### Post by ronnielsen1 on 2010-09-04
> can you help me even for my other problems!

It's best to start new posts on new problems

---

### Post by soramia on 2010-09-04
i am sorry, but i don't understand very well your suggestion.
please excuse me!!!

---

### Post by soramia on 2010-09-04
ok thank you!

---

### Post by mikewhatever on 2010-09-04
According to your first post, you've upgraded to something you call 10.03.1. Can you provide more details. How exactly did you upgrade?

---

### Post by rjbl on 2010-09-04
> **soramia said:**
> hi! maybe it is not the righy forum, but please help me!
i am new linux user, after 20 window's years and it's very difficult for   me:

[LIST=1]
[*] i've tried to install skype   and it appears the error
[LIST=1]
[*]error:   dependency is not satisfiable libasound2
[/LIST]
 
[*]i received the upgrading from 8.04 version to 10.03.1 version. i   created the cd and, after restarting the pc....error
[LIST=1]
[*]E: Unable to locate any  package   files, perhaps this is not a Debian Disc
[/LIST]
 
[*]i have an external hard disk. i plugged it in the usb port and....   error:
[/LIST]
[INDENT]It's not possible to mount the drive

[/INDENT]I am crazy....i would format everything and reinstall   windows...but i want to win!
can you help me?
thank you
rosa:popcorn:):P


P.s. sorry for my english....i am italian!

I installed Skype using the Software Centre (Ub 10.04). No problems.

rjbl

---

### Post by soramia on 2010-09-06
sorry for the late....
i make a mistake. the version is 10.04.1
I received the upgrading from my preinstalled version 8.04 to the version 10.04.1
I transferred the iso file in a cd but, when I tried to launch the cd, I received the following error message

E: unable to locate any oackage files, perhaps this is not a Debian Disk.

I don't understand this message, because I am new Linux user...and I donknow what I have to do.
Please, can you help me?
thanks
rosa

---

### Post by mikewhatever on 2010-09-07
Why use the cd if you had already upgraded to 10.04.1? Skype is not there. Anyway, make sure you burn the cd as image not data or anything else.

---

### Post by pjmacdonald on 2010-11-26
i am having same problem, error message something about libasound 2

---

