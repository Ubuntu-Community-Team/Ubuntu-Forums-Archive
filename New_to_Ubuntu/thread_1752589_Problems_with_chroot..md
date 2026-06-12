---
title: "Problems with chroot."
date: 2011-05-08
forum: New to Ubuntu
---

### Post by TheManno1 on 2011-05-08
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)   perl: warning: Please check that your locale settings: 	LANGUAGE = "en_AU:en", 	LC_ALL = (unset), 	LANG = "en_AU.UTF-8"     are supported and installed on your system. perl: warning: Falling back to the standard locale ("C"). locale: Cannot set LC_CTYPE to default locale: No such file or directory locale: Cannot set LC_MESSAGES to default locale: No such file or directory locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by wilee-nilee on 2011-05-08
You might state your problem that makes you need to chroot in, so far to most forum members this is gibberish.

As your thread here asking how has gotten no answer.
[http://ubuntuforums.org/showthread.php?t=1752540](http://ubuntuforums.org/showthread.php?t=1752540)

---

### Post by TheManno1 on 2011-05-08
To run pcsx2 the playstation 2 emulator. in 64 bit linux. I am using this advice from the forum because it seems easier then the wiki. Step 1 last instruction dpkg-reconfigure locales

---

### Post by yetiman64 on 2011-05-08
> **TheManno1 said:**
> To run pcsx2 the playstation 2 emulator. in 64 bit linux. I am using this advice from the forum because it seems easier then the wiki. Step 1 last instruction dpkg-reconfigure locales

32 bit chroots are the older method to do things, it is better if you can try and install the emulator directly with ia32libs installed and use "dpkg -i --force-architecture". I don't know if forcing architecture will work for that package though, it will take some testing.

I personally maintain a 32 bit chroot environment (note **schroot is used from Karmic on**, not dchroot further complicating matters) for mplayer and a raft of programs that use mencoder (I do it for full codec support as w64codecs is limited in scope imo).

It is a very complex method requiring bind mounting not only of system folders but your home directory and media folders and is potentially VERY dangerous to your data if you make a mistake. Some rather dirty/nasty hacks are required and as such I could not post the details here in ABT or on the forum in general as I suspect some of my changes here are a potential security problem. 

I recommend you look at alternate methods to install the emulator particularly with ia32libs.

**Edit**: pay particular note to the date of the thread post you are following, it is from **2005**. Last edited May 14th 2005.

---

### Post by TheManno1 on 2011-05-08
**IA32 libs / Multi-arch**

[INDENT]Some distributions give you  the ability to install 32 bit libraries in an amd64 architecture. Note:  it is still necessary to install the 64 bit development packages, and  some distributions miss some of the required libraries:  
[LIST=1]
[*]Debian / Ubuntu:
[LIST=1]
[*]ia32-libs-dev and ia32-libs-gtk.  Unfortunately it misses multiple libraries. These packages will  disappear in favor of real multi-arch. Here the missing 32 bits  libraries. **At your own risk** you can try to install them manually.
[LIST]
[*]libportaudio
[*]libglew
[*]libwxbase2.8 and libwxgtk2.8
[*]nvidia-cg-toolkit
[/LIST]
[*]Future: multi-arch which allow to install any architecture library in any architecture system (ease also cross-compilation).
[LIST]
[*]Ubuntu: expected in 11.10 and later.
[*]Debian: expected in Wheezy and later.
[/LIST]
[/LIST]
[/LIST]
[/INDENT]

---

### Post by TheManno1 on 2011-05-08
What are the terminal commands for this and will it work.

---

### Post by yetiman64 on 2011-05-08
> **TheManno1 said:**
> What are the terminal commands for this and will it work.

Do further research for that emulator and ia32libs, or wait for someone else to answer with specific knowledge of that idea.

I have ia32libs installed here from the repos and have forced the install of Nero Linux 3 and Avast4Workstation with the "dpkg -i --force-architecture <packagename>.deb" and had it work fine. I don't specifically know about that emulator though.

If your thread gets little response it is because it is a very specific question, bump your thread only once every 24 hours if needed, any double or cross posting is frowned upon [[COLOR=RoyalBlue]--see here for posting rules--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=885580") paricularly #s 4 & 8 in the second list.

Regards from yetiman64

---

### Post by TheManno1 on 2011-05-08
So if I create a thread on how to install extra 32 bits  libraries. Is that okay.

[LIST]
[*]libportaudio
[*]libglew
[*]libwxbase2.8 and libwxgtk2.8
[*]nvidia-cg-toolkit
[/LIST]

---

### Post by yetiman64 on 2011-05-08
> **TheManno1 said:**
> So if I create a thread on how to install extra 32 bits  libraries. Is that okay.

[LIST]
[*]libportaudio
[*]libglew
[*]libwxbase2.8 and libwxgtk2.8
[*]nvidia-cg-toolkit
[/LIST]


As you have basically asked it here and it relates to installing the emulator, I would suggest you change the thread title if you can. You may need to contact a moderator to change the title if you can't edit yourself - use the report post button on your first post to ask for help in doing so, if needed. 

Something like "Problems with chroot/ia32libs for pcsx2". Just an example, but ask a mod if in doubt. Just keeping each topic to one thread helps out the mods on a forum this big. 

I note you are still waiting on replies in this thread as well, [http://ubuntuforums.org/showthread.php?t=1712017&page=2](http://ubuntuforums.org/showthread.php?t=1712017&page=2)

Your patience is appreciated.

Cheers and good luck. yetiman64

---

