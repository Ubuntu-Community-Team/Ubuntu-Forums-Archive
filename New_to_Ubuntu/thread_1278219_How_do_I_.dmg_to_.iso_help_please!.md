---
title: "How do I? .dmg to .iso help please!"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by alive1dub on 2009-09-29
Hi
I am trying to convert a .dmg to an .iso which I can burn to disc with something like Brasero. Its a big file tho 6.7 gb. I have a DL DVD burner and the right discs etc.
I tried installing dmg2img but cannot for the life of me get it to function as others say it should.
Any help would be welcome

Thanks in advance

Al

---

### Post by mikeyphi on 2009-09-29
[http://www.icompositions.com/articles/article.php?pid=208](http://www.icompositions.com/articles/article.php?pid=208)

[http://sourceforge.net/projects/dmg2iso/](http://sourceforge.net/projects/dmg2iso/)

First site talks through but for windows, second site is for dmg2iso.

I think you will find that dmg2iso is what you want rather than dmg2img.

---

### Post by alive1dub on 2009-10-02
Thanks Mikey will check later on today


Al :)

---

### Post by ss73666 on 2009-10-02
You can use acetoniso. go here... [http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO) it is written on qt4 so have synaptic ready...

---

### Post by alive1dub on 2009-10-02
Hiya,

got this working but it wont work on folders  larger than 4gb :(
I still need to find a workaround.Any other ideas?

thanks for the help

Al

---

### Post by alive1dub on 2009-10-02
Tried this its for mac platforms only I am running Ubuntu jaunty

cheers tho
:)

---

### Post by cariboo on 2009-10-02
[Poweriso]("http://www.poweriso.com/download.htm") has a Linux version that will do what you need. It is a command line tool.

---

### Post by bulletxt on 2009-10-02
> **alive1dub said:**
> Hi
I am trying to convert a .dmg to an .iso which I can burn to disc with something like Brasero. Its a big file tho 6.7 gb. I have a DL DVD burner and the right discs etc.
I tried installing dmg2img but cannot for the life of me get it to function as others say it should.
Any help would be welcome

Thanks in advance

Al

First try AcetoneISO as someone suggested, if it doesn't work then this will work 100%:  [http://hem.bredband.net/catacombae/dmgx.html](http://hem.bredband.net/catacombae/dmgx.html)

If it doesn't, then forget about it (at least under linux). But I'm sure it will work.

As a very last resort, you can mount the image from a terminal:

sudo modprobe hfsplus
sudo mount -o loop,ro -t hfsplus imagefile.dmg /mnt/mountpoint

After mounting the image, you can create an iso of the mounted point folder with AcetoneISO and then finally burn it. If the image is bootable I'm not sure if after burning it it will still be bootable.

---

### Post by alive1dub on 2009-10-03
I have downloaded the linux version and extracted it to the desktop?
What do I do next to get it up and running?

thanx in advance

Al:)

---

### Post by bulletxt on 2009-10-03
> **alive1dub said:**
> I have downloaded the linux version and extracted it to the desktop?
What do I do next to get it up and running?

thanx in advance

Al:)

open a shell, get inside dmgextractor-0_70-bin/bin folder and type:
./dmgx.sh -gui

---

### Post by chriskin on 2009-10-03
"something" at 6.7gb at .dmg, might i say that you are asking for instructions to build a hackintosh?

---

### Post by alive1dub on 2009-10-04
Maybee... maybee not!

I intended to copy this file onto my portable drive so I could burn it with a mhackintosh but all attempyts to get it to work with Ubuntu failed and the drive is now corrupted:( Thats next on my list when I manage to burn the iso and get my mhack running again.

---

### Post by chriskin on 2009-10-04
am i the only one here thinking this is a forum that is about legal stuff like ,i don't know, linux?

---

### Post by alive1dub on 2009-10-06
File conversion is not illegal

I am using a linux platform to try and convert the files.

What I do with my backup disc image is I would imagine up to me?

If my Mac was up and running I would do the conversion with it and it would be far less painful an experience, as it is I was interested in using another platform to achieve this and learn something at the same time.

I have happily used Ubuntu for some years now and this is the only problem I have been unable to fix myself hence my using the forum to get help.

---

### Post by bulletxt on 2009-10-06
Ok, but did you ignore my post? I gave you exact details on how to get that image either converted to iso or mounted, so in either case you should be able to access the files and then if needed convert the folder to iso with AcetoneISO.

> **alive1dub said:**
> File conversion is not illegal

I am using a linux platform to try and convert the files.

What I do with my backup disc image is I would imagine up to me?

If my Mac was up and running I would do the conversion with it and it would be far less painful an experience, as it is I was interested in using another platform to achieve this and learn something at the same time.

I have happily used Ubuntu for some years now and this is the only problem I have been unable to fix myself hence my using the forum to get help.

---

### Post by alive1dub on 2009-10-08
All sorted now thanks for all the help everyone.

:)

---

### Post by TechZilla on 2011-04-19
hate to bring back such an old post, but having to deal with these .dmg's again.  

AcetoneISO is just a GUI for other tools, in regards to .dmg,
It mounts the image for files.  (trashes a boot record)
Or uses poweriso for conversion (just might work, not sure)

IMO, AcetoneISO is for people who don't like CLI, nothing more or less.  It, on its own, will not do anything other tools cannot due.  (not bashing, just think this needs clarity)

Also really need to comment on this nonsence,
> **chriskin said:**
> "something" at 6.7gb at .dmg, might i say that you are asking for instructions to build a hackintosh?
> **chriskin said:**
> am i the only one here thinking this is a forum that is about legal stuff like ,i don't know, linux?

For self-incriminating purposes, It is not acceptable to ask someone their intentions. It is not only unfriendly, but also brings an environment of fear and censorship to OUR forums.
IMO it is just as unfriendly as receiving a suspicious questioning from an officer of the law.  (not judging officers, just stating they don't work under the same premise as a helpful conversation between members)

I believe I speak for most people here, if it is not directly against the forums policy (which could always be discussed with a mod, or by cleared up by checking the COC) please refrain from coercing self-incriminating statements that suddenly make it so. 


this has been going on now for years, just really sick of this type of non-helpful, childish, tattling behavior.

---

### Post by chriskin on 2011-04-19
necromancer level +1
I don't even remember making that post any more. 

It is a little rude, yes, but the intentions of the op are rather obvious (and not exactly withing the rules he accepted when he created his account here)


anyway, just let the poor thread die - the answer has been given already.

---

### Post by Elfy on 2011-04-19
Closed

---

