---
title: "very slow internet"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by tame_lx_tech on 2010-11-13
hello

My internet varies between being normal and completely not working, but the network is still working (i'm using wifi). I have a laptop next to me and that can still use the internet at normal speed even when my computer can't. 

I have absoloutely no idea where to start, so any help would be appreciated.

thanks

---

### Post by pizza-is-good on 2010-11-13
What I would do:

Try [speedtest.net]("http://speedtest.net") on both of your computers running side by side and see what happens.

Look through your settings to see if there is an option to 'negotiate to lowest possible link speed' or something like that. The option may be at the BIOS level. It should be disabled.

Are you running any peer2peer programs or is anyone streaming video in your network?
What Ubuntu are you running? What are your hardware specs?
Does that computer multi-boot? If so, does the same problem happen in windows?

~pizza

---

### Post by tame_lx_tech on 2010-11-13
I tried running that test and it wouldn't load, and i haven't been able to find an option for link speed.
No P2P software running, and i'm streaming a video at the moment wit no effect.
I'm running ubuntu 10.10 with 384MB RAM (BIOS said something about 128MB UMA frame buffer) and a pentium 4 i think at 3 GHz and 60GB HDD, and i'm not multibooting.

thanks

---

### Post by pizza-is-good on 2010-11-13
> **tame_lx_tech said:**
> I tried running that test and it wouldn't load, and i haven't been able to find an option for link speed.
No P2P software running, and i'm streaming a video at the moment wit no effect.
I'm running ubuntu 10.10 with **384MB RAM** (BIOS said something about 128MB UMA frame buffer) and a pentium 4 i think at 3 GHz and 60GB HDD, and i'm not multibooting.

thanks

Wow! That's really little RAM!
While it is enough to run Ubuntu, it is likely that you won't be able to do much else.

Go to System>>Administration>>System Monitor. Under the 'Resources' tab, you'll see how much RAM is being used? What's it say?

Try to use Chrome for a bit. In my opinion it uses less RAM.

---

### Post by tame_lx_tech on 2010-11-13
i'm using about 75%
would taking memory from the UMA frame buffer help anything?

---

### Post by tame_lx_tech on 2010-11-13
i'll be back tomorrow, thanks for you help

---

### Post by pizza-is-good on 2010-11-13
> **tame_lx_tech said:**
> i'm using about 75%
would taking memory from the UMA frame buffer help anything?

OK. Wow. Is it 75% while browsing? or just when the computer idles?

Yeah, you could go ahead and try to reduce the UMA. See if it helps. Unfortunately, I've never dealt with the UMA, so I can't recommend how much to reduce it by.

On another note, you might need to get a 'lighter' version of Ubuntu if you want to do browsing. I imagine you installed Gnome, the default download. There are some version of Ubuntu which are meant to run in lower-memory, such as Xubuntu and Lubuntu. I have used Lubuntu and must say it looks fairly nice.

---

### Post by tame_lx_tech on 2010-11-14
Hey, i've now reduced the frame buffer to 32MB, and graphics still look the same (i don't game, so its not too graphics intensive).
The RAM is running about 59% under the same conditions as before (listening to music and browsing).
As you guessed, i am running gnome. Is it possible to install lubuntu without uninstalling what i currently have?

---

### Post by pizza-is-good on 2010-11-15
> **tame_lx_tech said:**
> Hey, i've now reduced the frame buffer to 32MB, and graphics still look the same (i don't game, so its not too graphics intensive).
The RAM is running about 59% under the same conditions as before (listening to music and browsing).
As you guessed, i am running gnome. Is it possible to install lubuntu without uninstalling what i currently have?

Well, that is a pretty good improvement, but I think you'd be doing better with lubuntu.
Yes, it is possible to install lubuntu without removing gnome.
Lubuntu is Ubuntu with Lxde as the default desktop environment, just as Kubuntu is Ubuntu with KDE as a desktop environment.

To install lxde, open up your software center, and search for lxde. The package you have to install will say: ```
LXDE (the Lightweight X11 Desktop Environment
```.

It has to download a lot of files, so the installation might take a while. You might also have to run updates after the installation is complete.

When it is all done, you can choose which Desktop Environment you want to log in with when you get to the log in screen. At the bottom of the screen you can choose between Gnome, Failsafe Gnome, Terminal, and LXDE. Just select LXDE and you'll be good to go. All your files and programs will still be there.

Post back when you are done!

~pizza

Edit: I was curious so I installed Lxde. WOW! It has improved a lot since I last used it. It looks very nice. Shiny would be a good word for it.

---

### Post by tame_lx_tech on 2010-11-16
Yeah, it does look shiny. Tho only problem is that it won't connect to my wifi. The settings for the network are there, but nothing happens.
Also, last night i went on facebook, looked at photos then my internet basically died again. I managed to do a speed test, and my computer got 0.2 MB/s while the laptop got 2.2MB/s. After that, i had no internet at all for the rest of the evening.
Thanks

---

### Post by uRock on 2010-11-16
What networking hardware does your system have? 

You may need to install the Windows XP driver using NDISWrapper to get the full capabilities of the hardware.

---

### Post by cavh on 2010-11-16
A friend of mine running Lucid as a newbie had very slow internet - try disabling IPv6 support in Firefox (presuming that's your browser). No idea how you do this, try Googling it.

---

### Post by tame_lx_tech on 2010-11-17
ok, i've disabled ipv6 but i haven't tried the NDISwrapper yet. I'm using a USB wifi dongle (Dlink) and a home router (Thomson TG585).
Internet is still slow :( I tried to ping my router and got 85% packet loss. Any thoughts? 
thanks

---

### Post by tame_lx_tech on 2010-11-17
I've just been on my router page and its using the name that my computer used to be while on XP, and the status changes between active and incative.
Would it be any use re-installing Ubuntu?

---

### Post by tame_lx_tech on 2010-11-17
I've just been on my router page and its using the name that my computer used to be while on XP, and the status changes between active and incative.
Would it be any use re-installing Ubuntu?

---

### Post by samhax on 2010-12-11
This seems to have solved the problem for me. I use a desktop with some pretty big specs, but everyone seems to be complaining of superslow or nonexistent internet speed. Try the 5th point, Disabling IPv6 from [_this place.:popcorn:_]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

Enjoy
[__]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

