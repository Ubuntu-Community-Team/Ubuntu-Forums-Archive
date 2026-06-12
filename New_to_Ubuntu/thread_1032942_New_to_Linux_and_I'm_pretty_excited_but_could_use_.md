---
title: "New to Linux and I'm pretty excited but could use some help."
date: 2009-01-06
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-06
Alright so I'm finished with M$ and I'm not ready to skip a thousand 99 cent coffees to buy a low end macbook with OS X.

So I looked toward Ubuntu, and the installation was great, after an unsuccessful dualboot with windows (just in case). Anyway, I'm 100% Linux now and am requesting a quick start guide. Can you tell me any good tips with linux? application recommendations? And most importantly, what's the best guide for compiling source codes, cause half the stuff I wanna get is code.

If there's anything else you think a linux-newb should know, please tell me!

Thanks a lot, love linux!

**Sorry, just noticed "Absolute Beginner Talk" sorry about posting here.

---

### Post by ByKeLaO on 2009-01-06
> **Sorry, just noticed "Absolute Beginner Talk" sorry about posting here.
That's OK, the forum moderators will move it into the correct forum.

Welcome to Ubuntu!
The first thing you might want to take a look at is the "Add/Remove" button in the Applications menu. Unlike in Windows, programs are installed in Ubuntu using a centralised package manager. That means in most cases you won't need to hunt for an installer on the internet, just open up your package manager and choose the program you want to install!

If you're interested in compiling stuff from source, you'll want to grab the "build-essential" package. There are 2 ways to do this:
1. Go to System->Administration->Synaptic Package Manager and install it there
or 2. Open up a terminal (Applications->Accessories->Terminal) and type:
```
sudo apt-get install build-essential
```

---

### Post by Sef on 2009-01-06
Moved to Absolute Beginners.

About installing, check out [How to Install Anything in Linux]("http://amitech.50webs.com/installing/index.php.html").

As for applications, it really is preference.   You just have to try different applications if you don't like the default one.

---

### Post by bowens44 on 2009-01-06
This link will show you some linux alternatives to popular windows software.

[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by 73ckn797 on 2009-01-06
Read all of the sticky notes at the top of the forum sections, particularly the Absolute Beginner Talk.

Make use of these sources:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Browse all of the menus and choices within Ubuntu. Get familiar with what you already have available.

Search, search, search, then ask questions. You may just find your questions have already been addressed.

---

### Post by dynathi on 2009-01-06
[http://ubuntuguide.org/]("http://ubuntuguide.org/") Has been really helpful to me in the past. And of course, the Ubuntu Forums :D

I usually install VLC media player right away. I find it much better than the default Totem Movie Player.

If you ever run into a position where you need to get a Windows-only program running, you can try Wine (do "sudo apt-get install wine" in the terminal). You can also install Windows into VirtualBox or VMWare, as per my signature.

If you want to start compiling source code, you will need to do:
```

sudo apt-get install build-essential

```
To get all the compilers and header files you need. If you have the source code to some program in a .tar.gz file, just go:
```

cd WhereEverTheTarGzIsLocated
tar -xzf WhatEverTheFileIs.tar.gz
cd WhatEverTheNewDirectoryIs
./configure
./make
./make install

```
However, under Ubuntu you pretty much will never have to do this ;)

That's all I can think of right now. Have fun in Linux!

---

### Post by hyper_ch on 2009-01-07
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by thegreatbitbucket on 2009-01-07
When I got started in Linux a loooooooooong time ago... I used a lot of "podcasts" to help me out.

Try listening to the "Going Linux" Podcast at [http://www.goinglinux.com/](http://www.goinglinux.com/)

That helps a lot. Also you should know about [http://help.ubuntu.com/](http://help.ubuntu.com/)

That's just the tip of the iceberg, but I hope that helps...

Emmanuel

---

### Post by Efros on 2009-01-07
Pretty much all you need is dogged determination and good Googling skills, I have managed to solve all of my issues with Ubuntu through these forums and Google. Which is more than can be said for my previous issues with XP, BSOD usually only soluble by reinstallation. Also keep an eye on the 6 monthly releases, if there's something that you miss or want it sometimes pops up in the new versions.

---

### Post by mattbutsko on 2009-01-07
Hey thanks for all the feedback, at school right now so I'll have to take a look later. Thanks for moving the post!

---

### Post by scouser73 on 2009-01-07
Hi Matt, this site on free e-books should also be of use to you, and welcome to the forums.

---

