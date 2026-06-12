---
title: "Two part question: ATI RAGE 128 Pro+USB TV tuner"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Famicommander on 2009-01-12
Alright guys. My first question is concerning my video card, which is an ATI RAGE 128 Pro with 32MB of on board RAM. Sad, I know. Well, my problem is I don't seem to have the driver for it installed, and I cannot locate them.

Before I upgraded to Intrepid, my drivers were fine. I could play 3D games like Open Arena and DVDs looked crystal clear. Now, I can't do anything that requires 3D graphics and DVDs, while still playable, just don't seem to look very good.

So, is there a driver for my card that I am not finding, or am I just screwed?

And my second question involves this:
[http://www.amazon.com/gp/product/B0007LBMR2/sr=8-3/qid=1231750573/ref=olp_product_details?ie=UTF8&me=&qid=1231750573&sr=8-3&seller=](http://www.amazon.com/gp/product/B0007LBMR2/sr=8-3/qid=1231750573/ref=olp_product_details?ie=UTF8&me=&qid=1231750573&sr=8-3&seller=)

1. What are the odds that this will work with Ubuntu?

2. What are the odds that this will work with my card?

3. If this won't work, can you recommend something similar that will?

I'm looking to play some of my older video game systems on my PC monitor, and I wouldn't mind running cable to this thing, either.

Here are my other system specs:
768MB PC 133 RAM
Intel Pentium IV processor @2.0ghz
20GB IDE hard drive
And yeah, the 32MB ATI RAGE 128 Pro graphics card

Any insight would be great.

---

### Post by Terl on 2009-01-12
Regarding your amazon question for the tv tuner, a quick search of the brand and model with a + linux after it finds:  [This.]("http://www.avsforum.com/avs-vb/showthread.php?t=920008")  Always try googling :)

---

### Post by Famicommander on 2009-01-12
So you found a forum where someone else asked for the PClinuxOS driver. I don't understand how that helps me with either problem.

---

### Post by Famicommander on 2009-01-12
So is my video card going to roadblock this or not? And I don't know anything about PClinuxOS; I googled around for the Ubuntu drivers and came up with nothing.

---

### Post by handydan918 on 2009-01-12
AFAIK, there is no ATI driver for linux for the 128 rage pro. It will work with the vesa driver, but as far as the folks getting 3D, IDK....

---

### Post by Famicommander on 2009-01-12
> **handydan918 said:**
> AFAIK, there is no ATI driver for linux for the 128 rage pro. It will work with the vesa driver, but as far as the folks getting 3D, IDK....

I had it working fine on Hardy Heron. I was running 3D games and playing DVDs in fullscreen without a hitch.

---

### Post by WitchCraft on 2009-01-12
> **Famicommander said:**
> I had it working fine on Hardy Heron. I was running 3D games and playing DVDs in fullscreen without a hitch.

AFAIK, there is an ATI driver for linux for the 128 rage pro

I have one on my Debian PPC Linux, and I can play OpenArena without problems...

I don't know anymore if the driver is in here, but I think it is in the standard mesa stuff.

For OpenGL, you need (i think one package is called differently in ubuntu)
```

apt-get install xlibmesa-dri xlibmesa-gl xlibmesa-glu mesa-utils libgl1-mesa-dri libgl1-mesa-glx

```

afterwards run:
```

glxinfo | grep "direct rendering"

```

which should output
```

direct rendering: Yes

```

---

### Post by Terl on 2009-01-12
> **Famicommander said:**
> So you found a forum where someone else asked for the PClinuxOS driver. I don't understand how that helps me with either problem.

You asked if it would work with Ubuntu.  Ubuntu is Linux as is PC LinuxOS.  So, yes, it can work with Linux.  Sorry, I should have taken more time to explain; I was at work when I wrote that :)

One thing to remember when you are looking into whether things may work or not, that it is often the chipset that matters and not the brand; you may have to dig deeper to see what the guts of the thing is made of to see if it will work.

---

### Post by WitchCraft on 2009-01-12
> **Terl said:**
> You asked if it would work with Ubuntu.  Ubuntu is Linux as is PC LinuxOS.  So, yes, it can work with Linux.  Sorry, I should have taken more time to explain; I was at work when I wrote that :)

One thing to remember when you are looking into whether things may work or not, that it is often the chipset that matters and not the brand; you may have to dig deeper to see what the guts of the thing is made of to see if it will work.

although pclinuxos is red hat based, it should work, because there is only one Linux kernel, and that is the one of Linus Torvalds.

However, you might run into problems with the install subroutines. I would try mesa first. If it doesn't work, you can still try compiling the pclinuxos driver

---

### Post by Terl on 2009-01-12
> **WitchCraft said:**
> although pclinuxos is red hat based, it should work, because there is only one Linux kernel, and that is the one of Linus Torvalds.

However, you might run into problems with the install subroutines. I would try mesa first. If it doesn't work, you can still try compiling the pclinuxos driver

My answer was regarding the tuner card and not the ATI rage card.

---

### Post by Famicommander on 2009-01-12
```
jason@jason-desktop:~$ sudo apt-get install xlibmesa-dri xlibmesa-gl xlibmesa-glu mesa-utils libgl1-mesa-dri libgl1-mesa-glx
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibmesa-dri is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgl1-mesa-dri
E: Package xlibmesa-dri has no installation candidate
jason@jason-desktop:~$ 

```

I don't know what the issue is here, but that's the first command you told me to input.

---

### Post by Famicommander on 2009-01-12
> **Terl said:**
> You asked if it would work with Ubuntu.  Ubuntu is Linux as is PC LinuxOS.  So, yes, it can work with Linux.  Sorry, I should have taken more time to explain; I was at work when I wrote that :)

One thing to remember when you are looking into whether things may work or not, that it is often the chipset that matters and not the brand; you may have to dig deeper to see what the guts of the thing is made of to see if it will work.

Yes, I gathered that it may work. What I want to know is *how* to make it work.

---

### Post by Famicommander on 2009-01-12
Ah, I fixed the error in the first command. I then ran this:
```
glxinfo | grep "direct rendering"
```

Which output this:
```
jason@jason-desktop:~$ glxinfo | grep "direct rendering"
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
jason@jason-desktop:~$ 

```

---

### Post by Famicommander on 2009-01-12
I tried to play Open Arena, and this is what I got:
```
jason@jason-desktop:~$ openarena
ioq3+oa 1.35 linux-i386 Sep 10 2008
----- FS_Startup -----
Current search path:
/home/jason/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak7-patch.pk3 (12 files)
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (204 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (15 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1720 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (1 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (610 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (234 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (89 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (988 files)
/usr/share/games/openarena/baseoa

----------------------
3873 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO )... OK
Initializing OpenGL display
Estimated display aspect: 1.250
...setting mode 0: 320 240
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
jason@jason-desktop:~$ 

```

---

### Post by Famicommander on 2009-01-13
Still getting the same two errors listed in the previous post.

---

