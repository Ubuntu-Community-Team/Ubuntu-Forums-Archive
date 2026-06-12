---
title: "Java, drivers, WINE, VSTs... what works w/ 64 bit now?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by mrowth on 2009-02-10
4GB RAM, I take it, require a 64 bit OS. I'm running Hardy 32 bit, but I'm willing to give 64 bit another try. What's it like these days? Will the following work? 

* Scanner with ancient firmware (Agfa Snapscan 1212u)
* Flash plugin (no tricks!)
* Java plugin (no tricks!)
* Java itself (Sun) 
* Win32 apps (with WINE, naturally)
* Win32 VST plugins in Linux-native [Renoise](http://www.renoise.com/about/screenshots/) 
* rt kernel (& JACK)
* Audio/video codecs 
* DVD playback

Oh, and this looks like another Hardy installation. There are (perhaps, soon, "were"?) some show-stopping issues with both Intrepid and KDE 4. Also, I'm all set up with KDE 3.5.10 and its apps, I don't want to toss all that.

Anyone want to assuage my fears?

---

### Post by adam_kimber on 2009-02-10
I have Hardy, I can surf the web using my phone as a modem without doing anything other than clicking an icon! I can play DVDs, playback all videos that I have, run Steam without that many problems (had a hardware lockup today for the first time in a long time in wine), Java is fine unless you want to upload files to Facebook then you have a problem (there are workarounds, a newer version of Java is out that works on 64bit Ubuntu, but is not that easy to install), Flash works unless you open another Firefox and then it doesn't, well for me anyway. Scanner if it worked before in Linux / Ubuntu there is really no reason it won't work this time...... No Openoffice 3 as of yet though. However there is a seperate repo for that. Jaunty will have the Openoffice and Java problems solved I hope. That is due out soon. 

Give Ibex a try. [http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695) might help with your KDE problem. If you want to use the upgrade feature then sure. I found a flatten and reinstall is the best way. Remember if you go down this road to back up your files in your home directory including the ones starting with . (the hidden ones). I generally create a seperate partition for my /home and therefore on reinstall i don't have to delete it nor do i lose my settings. :D If you want any help on those issues ask or even better have a search around the forum!

PS If you install a 32bit OS then there are no problems with Java.

---

### Post by RomeReactor on 2009-02-10
Hi. I would say 64 bit is pretty much stable now, and you shouldn't have issues with it, but it does vary case to case. Regarding your questions:
 
* Scanner with ancient firmware (Agfa Snapscan 1212u)
Not sure, but maybe [this thread]("http://ubuntuforums.org/archive/index.php/t-438164.html") can help.


* Flash plugin (no tricks!)
There's a [native 64 bit plugin]("http://ubuntuforums.org/showpost.php?p=6700030&postcount=13") now. Just close Firefox before installing, or restart it afterwards.


* Java plugin (no tricks!)
Haven't tried this myself, but there's now a [64 bit plugin]("http://java.sun.com/javase/downloads/index.jsp") as well. Uninstall IcedTea before installing it.


* Java itself (Sun)
64 bit as well. as far as I know.


* Win32 apps (with WINE, naturally)
They should work the same as with Ubuntu 32 bit, but it can vary.


* Win32 VST plugins in Linux-native Renoise
Not sure.


* rt kernel (& JACK)
Not sure either.

* Audio/video codecs
Should work the same as with your 32 installation.


* DVD playback
See above.

As for KDE 4, I tried it a couple of weeks ago and aside form a few bugs, it worked well.

---

### Post by mrowth on 2009-02-10
> run Steam without that many problems (had a hardware lockup today for the first time in a long time in wine)
Okay, this may be a stupid question, but I'm not a gamer, and never investigated the problem... do you have to install DirectX for WINE or something? Because I installed Steam once and tried the Half Life 2 demo, and I got what looked like 0.1 FPS...

> [http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695) might help with your KDE problem. 
Ah! That might tide me over until KDE 4 works right. 

Although: that won't give me the realtime kernel.  Ubuntustudio still suggests the Hardy-based release. So if Hardy 64 bit isn't any wonkier than Hardy 32, I would actually rather stick with it and wait how 9.04 or 9.10 turn out. 

> If you want to use the upgrade feature then sure. I found a flatten and reinstall is the best way. 
If I'm going to switch to 64 bit I'll have to start over clean anyway, right? (I do have a /home partition.)

...

The reason I was asking about the scanner is that I have to point SANE at a firmware .bin from the Win32 driver CD... and I'm not always sure how all this "combines" - why you can run 32 bit applications on a 64 bit OS, but not use 32 bit browser plugins, drivers (?), or codecs (???). So there's some fuel for uncertainty, and that's why I'm wondering about VSTs, too.

---

### Post by mrowth on 2009-02-10
> **RomeReactor said:**
> * Win32 VST plugins in Linux-native Renoise
Not sure.


* rt kernel (& JACK)
Not sure either.

Hmmmmmm. Those are pretty much required. But thanks for the reassurance on the other points. Couple things less to worry about. RT kernel/JACK shouldn't actually be a problem. Ubuntustudio does have a 64 bit release, after all.

> As for KDE 4, I tried it a couple of weeks ago and aside form a few bugs, it worked well.
The problems I'm having are rather discouraging. Neither Twinview nor separate X screens work properly, switching TTYs gets me a blank or garbled desktop, kdeinit and klauncher notifications kick me back out to the login, Konqueror forgets settings, and so on. 'course, that's with KDE 4.1.something, and some of that might be fixed already. But I can't upgrade to Intrepid if there's no properly working -rt kernel for it. So until the stars are right I'm sticking with Hardy.

---

### Post by RomeReactor on 2009-02-10
> **mrowth said:**
> Hmmmmmm. Those are pretty much required. But thanks for the reassurance on the other points. Couple things less to worry about. RT kernel/JACK shouldn't actually be a problem. Ubuntustudio does have a 64 bit release, after all.
If you have a dual core processor, there's a [bug in SMP support in Intrepid's rt kernel]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498"), so you'd probably want to keep your current Hardy installation, or use Hardy 64 bit.

> The bugs I encountered were rather show-stopping. Twinview, separate X screens, switching ttys, kdeinit and klauncher notifications kicking me back out to the login, Konqueror forgetting settings, and so on. 'course, that's with KDE 4.1.something, and some of that might be fixed already. Anyway, I'm looking forward to KDE 4 - just not necessarily right now.
Nothing so critical here, but there *were* quite a few usability bugs. Haven't tried KDE 4.2 yet. Then again, I didn't try KDE 4 in Hardy.

---

### Post by mrowth on 2009-02-10
> **RomeReactor said:**
> If you have a dual core processor, there's a [bug in SMP support in Intrepid's rt kernel]("https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498"), so you'd probably want to keep your current Hardy installation, or use Hardy 64 bit.
Yeah, I have an AMD X2 4800+. Suspend/Hibernate aren't working either, they say... not that I ever got Hibernate to work in the first place, but I'm rather addicted to Suspend-to-RAM. I don't really want an all new OS, anyway... Ideally, I'd just pop in 4*1GB CL2 RAM and continue as before. (Okay, and get my video card to perform better, but that's a different (so far unanswered) topic.)

Edit: 

Looks like my mainboard may downgrade the RAM clock (or... whatever) if all 4 DIMM slots are populated, and I can't quite tell if setting it manually in the BIOS setup will override that. It *sounds* like it, but elsewhere I saw a statement to the contrary.

Sigh. I suppose I could find out if I had a program to report the actual speed; I already have 4 DIMMS inserted (1 GB, 512 MB, 1 GB, 512 MB).

[quote="Asus website"]Problem  
Why does A8V Deluxe automatically down-grade from DDR400 to DDR333 when four DIMMs of memory are plugged?

Answer
It is a protective function when system cannot boot up or any instable symptoms due to memory itself.
Please go to Advanced --> CPU Configuration --> Memory Configuration --> Memory Configuration in BIOS, and manually adjust memory frequency to 200MHz. Please refer to Chapter 4.3 in the manual for more details. [/quote]

---

### Post by mrowth on 2009-02-15
> * Win32 VST plugins in Linux-native [Renoise](http://www.renoise.com/about/screenshots/) 
Nevermind, was too happy with Renoise coming to Linux to notice it "only" supports Linux-native VSTs.

But I have another question; if I upgrade an existing Hardy installation "in place" to Intrepid, will I still be able to use the Hardy-era 2.6.24 kernels (rt in particular)?

---

### Post by RomeReactor on 2009-02-15
> **mrowth said:**
> But I have another question; if I upgrade an existing Hardy installation "in place" to Intrepid, will I still be able to use the Hardy-era 2.6.24 kernels (rt in particular)?

No. There's only one 2.6.25-X for 32 bit installations; [the rest are 2.6.27-X]("http://packages.ubuntu.com/intrepid/linux-image").

---

### Post by mrowth on 2009-02-15
> **RomeReactor said:**
> No. There's only one 2.6.25-X for 32 bit installations; [the rest are 2.6.27-X]("http://packages.ubuntu.com/intrepid/linux-image").

Would the upgrade delete the 2.6.24 kernels? Or would booting them just not work (properly)?

---

### Post by RomeReactor on 2009-02-15
> **mrowth said:**
> Would the upgrade delete the 2.6.24 kernels? Or would booting them just not work (properly)?

I think the Hardy kernels will be removed as part of the upgrade. I've been upgrading since Edgy or Feisty, and the only kernels available in my Intrepid installation are 2.6.27-X.

---

### Post by mrowth on 2009-02-15
Okay, thanks for the answers.

---

### Post by presence1960 on 2009-02-15
To make it short & sweet, why don't you check out the stickys on 64 bit users forum. I followed the directions there and have no problems with 64bit java or flash on Kubuntu 8.10 or Linux Mint 5 (Hardy). I don't know about wine but I installed Sun Virtual Box to run XP Pro so I can use Adobe Acrobat Profesional for work.

---

### Post by mrowth on 2009-02-15
> **presence1960 said:**
> To make it short & sweet, why don't you check out the stickys on 64 bit users forum. I followed the directions there and have no problems with 64bit java or flash on Kubuntu 8.10 or Linux Mint 5 (Hardy). I don't know about wine but I installed Sun Virtual Box to run XP Pro so I can use Adobe Acrobat Profesional for work.
Okay... I was impatient, sorry. I've tried going 64 bit before and after trying various workarounds went back to 32 bit. 

I depend on (a few) Win32 apps + VST plugins, old scanner firmware (not an issue? but I wouldn't really know), realtime kernel support, ACPI suspend, RAM/mainboard issues, a few apps I have to compile from source -- mostly things I've half-given up asking for help about. I doubt those stickies address those problems. And many of the threads they link to actually petered out in 2006 or 2007. 

Seems there's still no 64 bit Java plugin from Sun? If I installed an open source Java plugin concurrently with the Sun Java JDK, would this get messy? 

Also, I can't seem to find out if WINE on 64 bit Hardy will run Win32 apps. WineHQ's Wiki says the 64 bit port is not yet functional; there's an AMD64 WINE package in their Ubuntu repository, though. Does it work for Win64 apps only? I don't think i can procure those in my case.

---

### Post by presence1960 on 2009-02-15
You haven't **REALLY** looked at those stickys then, because if you have you could not make the statement that the threads they linked to petered out in 2006. There are current posts which deal with Flash and Java in Hardy, Ibex and Jackalope. Unless I am hallucinating these weren't around in 2006. But as the old saying goes: you can lead a horse to water but you can't make him drink it. It is your choice  so enjoy it.

---

### Post by mrowth on 2009-02-15
> **presence1960 said:**
> You haven't **REALLY** looked at those stickys then, because if you have you could not make the statement that the threads they linked to petered out in 2006. There are current posts which deal with Flash and Java in Hardy, Ibex and Jackalope. Unless I am hallucinating these weren't around in 2006. But as the old saying goes: you can lead a horse to water but you can't make him drink it. It is your choice  so enjoy it.
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) links to over a dozen threads, all from the forum archive; 'fraid I did get discouraged too easily. However, there has - from the start - been more to it than installing two browser plugins, and the unresolved bugs and varied uncertainties have been piling up, and the spirit may be willing, but the flesh is weak, and so instead of googling & sifting at a dozen+ *additional* fronts I fired off a request for "orientation". 

(Yes, there's a 64 bit Flash 9 plugin in the repos. No, 64 bit Flash 10 and Java plugins must be installed manually. Some say "32 bit browser", or "open source java"; Sun 64 bit JRE & JDK done but missing plugin; alpha available (functionality?); other questions remain unaddressed. . . etc.)

---

### Post by presence1960 on 2009-02-15
more specifically : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

my bad, i should have posted it the first time

---

### Post by presence1960 on 2009-02-15
Mrowth:
I tried wine and hated it, found Sun Virtual Box more up to the task since I can run windows and install any windows software I need (which isn't much these days. currently have only Adobe Acrobat Professional on Windows). I am hoping I can learn scribus  and see if it will be a suitable replacement for Adobe.

Maybe you should check out Kilz's posts on getting 64bit going. Reading his posts is what got me to give it a whirl in spite of all the negative stuff I read. The bottom line is you gotta go with what works for you. That's what choice is all about, right?

---

### Post by mrowth on 2009-02-16
> **presence1960 said:**
> Mrowth:
I tried wine and hated it, found Sun Virtual Box more up to the task since I can run windows and install any windows software I need (which isn't much these days. currently have only Adobe Acrobat Professional on Windows). I am hoping I can learn scribus  and see if it will be a suitable replacement for Adobe.
I like running my (mostly small-ish) Windows apps alongside Linux apps. They can use the same filesystems, and integrate in a JACK setup, and with binfmt-support I don't even need to remember to "wine <app.exe>" them. Sure, there're some snags and the GUI feels off... hm. Might try Virtual Box, didn't actually know it existed (and was free). Not sure it'll be right for my purposes, or for my iron age PC.

> Maybe you should check out Kilz's posts on getting 64bit going. Reading his posts is what got me to give it a whirl in spite of all the negative stuff I read. The bottom line is you gotta go with what works for you. That's what choice is all about, right?
I just wish choice were about style/taste only, say: KDE vs. Gnome vs. Xfce vs. Fluxbox - rather than functionality "either/or"s.

Installing 64 bit Java & Flash plugins seems rather straightforward these days (no weird tricks), although I suppose there's no guarantee what'll work with alpha/beta releases.  I didn't find much - or anything - about some of my questions. Will just have to give it a try again and see for myself, yes - but this time without wiping the 32 bit install!

---

