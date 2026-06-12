---
title: "AVG 8.5 for Ubuntu 9.04 AMD 64 bit problem"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Chino355 on 2009-06-13
Just wondering if anyone has  succesfully install** _AVG 8.5_** not 7.5 on ubuntu 9.04 64bit AMD?

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

I tried with the 7.5 instruction and filled in the blanks with (avg85lms-r287-a2601.i386.deb)

using this post [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064) for ref

changing .i386 to .AMD64 and got errors after making .deb :(

and avggui I somehow screwed up:(

and if we could stick to the subject of _**AVG 8.5**_ ubuntu 64bit AMD it would muchly appreciated;)

any help on how to or insight would be very welcomed, thanks!;)

---

### Post by donkyhotay on 2009-06-13
Umm... I just have to ask *why* you're installing an antivirus program onto ubuntu? If you're trying to help keep your windows system free from viruses thats one thing but linux itself doesn't need a virus scanner to keep itself safe. And if you're one of those people that think they need one 'just in case' then read the following:






Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

&#8220;Master Foo,&#8221; he asked &#8220;why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?&#8221;

Master Foo smiled, and said &#8220;When your house is well constructed, there is no need to add pillars to keep the roof in place.&#8221;

The novice replied &#8220;Would it not be better to use these things anyway, just to be certain?&#8221;

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

&#8220;What are you doing?&#8221; the novice asked in surprise.

Master Foo replied simply: &#8220;Tying your shoes.&#8221;

Upon hearing this, the novice was enlightened.

---

### Post by Chino355 on 2009-06-13
I will be transfering old back up files avi,pictures,music etc. from former M$$computer

(backed up on external HD usb)

under M$$crap i was runing the headache of Norton the F'n program at that time the scan came back with trojans and bots

so with that said, I would like to avoid the transfer of these particulars and prevent them 

from being transfered;)

Soooooo0000

do I need it or not? ](*,)

---

### Post by donkyhotay on 2009-06-13
In that case yes you will want an anti-virus. The reason I asked is because many people migrating from windows to linux think they need anti-virus because it's was necessary under windows. Although some people that ask that question are like yourself and want to prevent viruses from infecting a windows system, *most* people that ask about antivirus here are trying to protect themselves from linux viruses. Since linux itself is all the protection you need it just gets in the way.

---

### Post by Chino355 on 2009-06-13
Thanks for the quick reply

I don't want to mess up my ubuntu 

I spent a lot of time with the tweaks and eye candy designs 

and the installation of programs

I would hate to start all over again

because of something I could have prevented

specs:

Ubuntu 9.04 (jaunty) AMD 64

M2A-VM series

2 GB ram

AMD Sempron 3500+

120 GB HD WD 

=D>

I still don't know how to install AVG 8.5 any thoughts?

thanks:D

---

### Post by Amilo1718 on 2009-06-13
just don't install avg
but if you[ insist]("http://free.avg.com/download?prd=afl")

---

### Post by Chino355 on 2009-06-13
What's better?:-\"

---

### Post by Chino355 on 2009-06-13
oh ya and free:mrgreen:

---

### Post by anjilslaire on 2009-06-13
He's already tried that link.
Have you tried clamav, fre and in the repos?
```

sudo apt-get install clamav

```

---

### Post by Chino355 on 2009-06-13
its free?

easy to use?

---

### Post by donkyhotay on 2009-06-13
I generally use clamav which is in the repos for the few times I need to scan something. It's CLI only (no GUI) but works well. Remember that the only reason for the antivirus is to avoid spreading viruses to others as you are already immune. If you are never going to pass the files to a windows machine you don't need anything. If you are going to pass the files back to a windows machine (which is my guess from what you describe) you will want to run the scan once to make certain you aren't spreading anything around then I'd delete the anti-virus.

---

### Post by Amilo1718 on 2009-06-13
tried [this]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") one?

---

### Post by Chino355 on 2009-06-13
Like to give a big shout out to the following members):P

donkyhotay

Amilo1718

anjilslaire

thanks for your help:guitar:

KlamAV it is,fits my cheap *** budget:mrgreen:

and installed like a charm:tongue:

---

### Post by donkyhotay on 2009-06-13
No problem, Welcome to ubuntu! (c:

---

### Post by spangaer on 2010-09-24
on amd64 you need libc6-i386
aftwards the 386 .deb avg installer works just fine with gdebi

---

