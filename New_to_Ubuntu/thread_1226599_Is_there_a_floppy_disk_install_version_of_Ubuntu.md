---
title: "Is there a floppy disk install version of Ubuntu?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Captain Spaulding on 2009-07-29
I was hoping to put ubuntu on a retro computer of my in laws.  I don't think it has a cd player or usb capabilities?  Am I out of luck?

---

### Post by philinux on 2009-07-29
Ubuntu install disk is 700 meg lol.

Even Damn Small Linux is ~50 meg.

---

### Post by lisati on 2009-07-29
There is a "minimal install" cd image available somewhere, but I'm not sure if it can be put onto floppy.

---

### Post by Captain Spaulding on 2009-07-29
> **philinux said:**
> Ubuntu install disk is 700 meg lol.
that is one of the problems i saw but hoped there was a way around it.  If not, what other linux is small enough to do a floppy install if possibly at all?

---

### Post by philinux on 2009-07-29
Floppy disk is 1.44 meg there is no way around that.

Whats the spec of the old pc?

Ha ha. [http://www.linfo.org/mulinux.html](http://www.linfo.org/mulinux.html)

[http://mulinux.sunsite.dk/](http://mulinux.sunsite.dk/)

No idea if this is any good whatsoever.

---

### Post by Captain Spaulding on 2009-07-29
> **philinux said:**
> Floppy disk is 1.44 meg there is no way around that.

Whats the spec of the old pc?

Unfortunately, I don't have access to the computer right now since it is in another state.  Guess that is my next job since this is going to require a bit of research.

---

### Post by CatKiller on 2009-07-29
If the computer is too old to have anything other than a floppy drive then it's probably too old to run a modern Linux distro. While you could do a net install, it probably isn't worth your time.

---

### Post by jerome1232 on 2009-07-29
Debian can do it

[http://www.debian.org/distrib/netinst#verysmall](http://www.debian.org/distrib/netinst#verysmall)

I would recomend a bare install, xserver and a light weight wm. Figure out what apps are needed and add them as you go.

---

### Post by lisati on 2009-07-29
Take a look here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)



edit: I've spotted my blunder (mini.iso won't fit on a floppy), I haven't regularly used floppies for some time. I'll leave the link here for now for the benefit of others who might be reading this thread for ideas

---

### Post by Captain Spaulding on 2009-07-29
> **CatKiller said:**
> If the computer is too old to have anything other than a floppy drive then it's probably too old to run a modern Linux distro. While you could do a net install, it probably isn't worth your time.

i will keep that in mind.  I have heard that linux is good for older machines but don't hav3 a clue on ho old is too old.

---

### Post by halitech on 2009-07-29
I've used the instructions here to install on a P266 laptop with 96meg of ram

[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

Thankfully it booted from cd but I know debian old-stable could boot from floopy but debian stable (Lenny 5.0) will only boot from cd due to the size of the kernel now. You could always see if you can find a copy of the floppies to do the install (or hope it will boot from cd and has a cd)

---

### Post by CatKiller on 2009-07-29
> **Captain Spaulding said:**
> i will keep that in mind.  I have heard that linux is good for older machines but don't hav3 a clue on ho old is too old.

The specs for DSL say "Run light enough to power a 486DX with 16MB of Ram," so that old is about the limit. DSL is remarkably stripped-down, though. You may need to adjust your expectations of what you'll be able to do when you find out the specs of the machine. Especially in terms of the hand-holding and automatic stuff that you get out of something like Ubuntu.

---

### Post by nhasian on 2009-07-29
you may want to hop onto craig's list for your inlaws and find a more modern computer for around $100 in their area they could pick up cheaply.  If their old computer that doesnt have a cdrom or any usb is running fine i wouldnt mess with it!

---

### Post by Captain Spaulding on 2009-07-29
> **nhasian said:**
> you may want to hop onto craig's list for your inlaws and find a more modern computer for around $100 in their area they could pick up cheaply.  If their old computer that doesnt have a cdrom or any usb is running fine i wouldnt mess with it!

they have a newer computer, this is just a case of wanting to see what i can do with an old computer that is not being used.  Thanks for the informatoin everyone.

---

### Post by Captain Spaulding on 2009-07-29
And just as an additional note, my mother is law is helping with a charity that helps lower income people and i thought this might be a way of getting used computers into their hands

---

### Post by jmszr on 2009-07-29
Captain Spaulding,

This site has quite a list of small Linux distributions: [http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/) .

This one looks like it might work for you: [http://tiny.seul.org/en/](http://tiny.seul.org/en/)

Interesting project.

---

### Post by cwsnyder on 2009-07-29
If you are running less than 4M RAM in the computer (pre-Win95 machine), you may as well bite the bullet and stay with Windows 3.1 or whatever version of DOS is on the machine.  Windows 95 wanted 4M RAM minimum, while Windows 3.1 would run down to 1M RAM.  OS/2 wanted 2M minimum, if I remember correctly.  Other GUIs of the time frame were available, but not much better than Windows 3.1, and less software was available for those platforms.  Even X-Windows was pretty clunky in Hurd and Linux on the less than 4M machines running 386sx-16MHz.

Remember, you are going to be working with ISA architecture, not PCI bus architecture.  No plug & play BIOS here.  No hard disks recognized over about 500M (possibly 1G) and you may not have PATA (aka IDE) hard drives.  That may be why a CD is not an option.

---

### Post by llamabr on 2009-07-29
> **CatKiller said:**
> If the computer is too old to have anything other than a floppy drive then it's probably too old to run a modern Linux distro. While you could do a net install, it probably isn't worth your time.

That's just not true.  You can put linux on anything.  A guy in my lug put it on an old broken ATM, just to prove he could.  a 486 with 16 megs of ram will run linux just fine.

You wouldn't want to put a new ubuntu on it, and you don't want to spend all day trading out floppies.  You could remove the hd, put it in something with a cd rom, install, and them put it back.  they also make backpack cd roms that run over serial port.  Or at least they used to.

---

### Post by Captain Spaulding on 2009-07-29
> **llamabr said:**
> That's just not true.  You can put linux on anything.  A guy in my lug put it on an old broken ATM, just to prove he could.  a 486 with 16 megs of ram will run linux just fine.

You wouldn't want to put a new ubuntu on it, and you don't want to spend all day trading out floppies.  You could remove the hd, put it in something with a cd rom, install, and them put it back.  they also make backpack cd roms that run over serial port.  Or at least they used to.

running it over a serial port just got me thinking about a couple of work arounds i can do.  some of them more Frankenstein in nature than others but I have some ideas now especially in concert with all the info in.  now if I can go to sleep instead of coming up with ideas and checking specs

---

### Post by ericab on 2009-07-29
> **jerome1232 said:**
> Debian can do it

[http://www.debian.org/distrib/netinst#verysmall](http://www.debian.org/distrib/netinst#verysmall)

I would recomend a bare install, xserver and a light weight wm. Figure out what apps are needed and add them as you go.

he is correct, debian does a floppy install.
i used this method some years back; worked fine.
somewhat time consuming though, and requires a decent i-net connection

---

### Post by CatKiller on 2009-07-30
> **llamabr said:**
> That's just not true.  You can put linux on anything.  A guy in my lug put it on an old broken ATM, just to prove he could.  a 486 with 16 megs of ram will run linux just fine.

You wouldn't want to put a new ubuntu on it, and you don't want to spend all day trading out floppies.

That's exactly what I said. Even down to the 486 with 16 MB of RAM. So I think your "that's just not true," is just not true.

---

### Post by starcannon on 2009-07-30
I'd likely recommend starting here:
[http://www.damnsmalllinux.org/network-install.html](http://www.damnsmalllinux.org/network-install.html)

You can get the Damn Small Linux distro here: 
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

50mb of Penguin Power; it'll let them do lite web surfing, check email, word processing, spread sheets, etc... I used to use it all the time on some old PII laptops. 

GL and HF

---

