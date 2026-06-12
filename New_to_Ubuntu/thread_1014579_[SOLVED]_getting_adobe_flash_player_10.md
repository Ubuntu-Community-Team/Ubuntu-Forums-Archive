---
title: "[SOLVED] getting adobe flash player 10?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by moose12 on 2008-12-18
several things have said they need this and i cant seem to obtain it! i tried downloading the .deb file and it said i have the wrong architecture!

---

### Post by overdrank on 2008-12-18
> **moose12 said:**
> several things have said they need this and i cant seem to obtain it! i tried downloading the .deb file and it said i have the wrong architecture!

Hi and some more info would help. Specs on the system version of Ubuntu.

---

### Post by moose12 on 2008-12-18
sorry, ubuntu 8.04, i have the flashplugin-nonfree but several things are not working, i.e. videos on facebook, flash games, etc

---

### Post by hellion0 on 2008-12-18
I believe overdrank meant what build of Ubuntu (x86, x64, etc.)

---

### Post by moose12 on 2008-12-18
i think its x86 and i know this makes me sound like a totall noob but is there a way to check?

---

### Post by perlluver on 2008-12-18
Could you open a terminal, and list what the following two commands output: ```
lsb_release -a
``` and ```
uname -r
```.

---

### Post by mc4man on 2008-12-18
The easiest thing to try using firefox is go to a major site that uses flash. like msnbc.com, click on a video and you'll get a prompt to install flash player.
Click yes, ok, whatever and in the list choose linux. In the next pop up choose 'deb for ubuntu 8.04+' and that'll do it.

---

### Post by bwang on 2008-12-18
If you have 64 bit, go here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by moose12 on 2008-12-18
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

and

2.6.24-22-generic

does that help?

---

### Post by moose12 on 2008-12-18
> **mc4man said:**
> The easiest thing to try using firefox is go to a major site that uses flash. like msnbc.com, click on a video and you'll get a prompt to install flash player.
Click yes, ok, whatever and in the list choose linux. In the next pop up choose 'deb for ubuntu 8.04+' and that'll do it.

tried this and it didnt work!

---

### Post by moose12 on 2008-12-18
> **bwang said:**
> If you have 64 bit, go here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

also didnt work!

---

### Post by hellion0 on 2008-12-18
Try this:
```
uname -m
```
Then report back what that gives you.

---

### Post by moose12 on 2008-12-18
x86_64


i think this is what your looking for right?

i was right too it is 86!

---

### Post by perlluver on 2008-12-18
> **moose12 said:**
> x86_64


i think this is what your looking for right?

i was right too it is 86!

That would be x86_64, which means you have the 64 bit version of Ubuntu installed.

---

### Post by the_zoor on 2008-12-18
I have the same problem. Cant seem to get the flash plugin to work. I have tried to install gnash, which didn't work so I removed it. I've also tried to install " flashplugin-nonfree " and " swfdec-mozilla ". Neither of the packages worked so I removed both of them. Of course I installed them one at a time. I also tried to go to adobe and install flash player 10 directly. Didn't work either.

Now... here is my output:

zoor@zoor-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.10
Release:    8.10
Codename:    intrepid
zoor@zoor-desktop:~$ uname -r
2.6.27-9-generic
zoor@zoor-desktop:~$ uname -m
i686


What am I doing wrong?

---

### Post by perlluver on 2008-12-18
the_zoor, remove flashplugin-nonfree then go to [http://www.adobe.com](http://www.adobe.com), and install the Ubuntu 8.04+ deb file.

---

### Post by moose12 on 2008-12-18
its the x86..., i didnt think there were any 86 bit computers out there, doesnt it go in powers of two which would make the next bit number 128?(if there is way more to this than i am understanding dont bother telling me about it. i realize there are alot of things i dont understand and although im intrigued this is not the issue at hand) but o well its x86_64 whatever that means to whoever needed it to help with the prob

---

### Post by the_zoor on 2008-12-18
Great!! Now it works. But whats the difference between flashplugin-nonfree and the file on adobe? I find it strange that neither of the files worked linked in synaptic.

Anyway, thanks!

---

### Post by perlluver on 2008-12-18
> **moose12 said:**
> its the x86, i didnt think there were any 86 bit computers out there, doesnt it go in powers of two which would make the next bit number 128?(if there is way more to this than i am understanding dont bother telling me about it. i realize there are alot of things i dont understand and although im intrigued this is not the issue at hand) but o well its x86_64 whatever that means to whoever needed it to help with the prob

That means that your OS is 64 bit, and some flash sites will not work with 64 bit implemented flash.  The wrong architecture type statement comes from it being 64 bit instead of 32 bit.

---

### Post by perlluver on 2008-12-18
> **the_zoor said:**
> Great!! Now it works. But whats the difference between flashplugin-nonfree and the file on adobe? I find it strange that neither of the files worked linked in synaptic.

Anyway, thanks!

Nothing really, it is just the fact that the installer from the repos is not working right now, for whatever reason.

---

### Post by moose12 on 2008-12-18
ok but im running on a reinstall (8.10 wipe and back again to 8.04) and before on 8.04 it was working great, now whats the deal?

---

### Post by moose12 on 2008-12-18
the link provided earlier for 64bit only gave me a .so file and i couldn't seem to do anything with that. perhaps im missing something there?

---

### Post by moose12 on 2008-12-19
i removed swfdec-mozilla using synaptics package manager and everything works fine!

---

