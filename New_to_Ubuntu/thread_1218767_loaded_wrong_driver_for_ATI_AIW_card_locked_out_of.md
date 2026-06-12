---
title: "loaded wrong driver for ATI AIW card locked out of Ubuntu on my dual boot machine"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by 321limelight on 2009-07-21
This is my second time trying to post onto a forum. (Hopefully in the right category and area this time)

I have been mussing with Ubuntu for over a year, and I have an ATI All-In-Wonder 9600XT video card which had installed well using the Ubuntu defaults when I moved up to 9.04. In an attempt to gain the functionality of the built in TV tuner, I checked off to load the proprietary drivers for ATI in the Add/Remove software section of my system. On my next reboot I get splashed/ smeared video where I should be seeing my Ubuntu splash (boot graphic) screen.

I have spent hours searching on the net and all over these forums trying to find a way to remove the downloaded driver. At this point seems fairly obvious I need to revert back to the open source default driver. My card is legacy now and was running well with the open source drivers until I picked a fight with it.

 I am having some challenges even getting to a command line, as my graphics splash me all over the monitor after I hit the Ubuntu splash screen after leaving Grub, and my computer does not seem to want to let me boot Parted Magic from my optical drive despite my efforts in BIOS setup and hitting a good variety of keys during boot. [sigh] 

I have tried using all the options in the recovery mode, and it did not help at all. On the forums I found as a possibility:

[B]sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f[/B]
(reboot)

Would that be what I would type into the command line [once I find a way in] to manually re-install the default open source video drivers? So I can get back into my Add/remove software or Synaptic and uninstall the troublesome proprietary restricted ATI package. 

Barring that possiblility if I do a full fresh install of Ubuntu 9.04 onto my machine do I lose my settings and files? Other than now being locked out by my frozen video card my machine was running top form for an old beater. And yes it is a dual boot I'm over on the XP side to do the search and recovery research.

Am I on the right track? Can anyone offer thoughts or insight?

---

### Post by yeats on 2009-07-21
Quick forum posting tip:  try to boil your need down to a question, and put it up front.  You'll get better responses :-).

> My card is legacy now and was running well with the open source drivers until I picked a fight with it.

I understand that support for older ATI graphics cards is not great in Jaunty - you might consider reverting to Intrepid... just a thought.

From XP, see if you can get to your files.  If you can't try this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

it will give Windows the tools it needs to "see" Ubuntu.  Then copy your files to the Windows side and reinstall.  I think that might be the best option considering your situation.  (Others may disagree :-) ).

---

### Post by Ernesto RD on 2009-07-21
I also tried the crappy ATI propietary driver and got the same results (an unusable system)
i removed the driver using this...

```
$ sudo apt-get remove --purge xorg-driver-fglrx
```

After that, ubuntu loaded as nicely as allways :)
Hope this helps

---

### Post by Ernesto RD on 2009-07-21
> **Ernesto RD said:**
> I also tried the crappy ATI propietary driver and got the same results (an unusable system)
i removed the driver using this...

```
$ sudo apt-get remove --purge xorg-driver-fglrx
```After that, ubuntu loaded as nicely as allways :)
Hope this helpsi forgot, to access the terminal to type the above, select the recovery mode on the grub menu, and then the drop to terminal option.

Cheers!

---

### Post by oldrocker99 on 2009-07-21
That advice on going back to 8.10 is exactly what I did. The ATI 9.03 drivers at least work fine under 8.10. The biggest thing to miss is the automatic opening of new directories.

:guitar:

---

### Post by 321limelight on 2009-07-25
I tried exactly as you had suggested and it removed the package and booted perfectly. The problem is solved. YAHOO. Thank you so very much Ernesto RD. Thank you all for your time and help.

---

### Post by vtuttle on 2009-09-26
> **Ernesto RD said:**
> I also tried the crappy ATI propietary driver and got the same results (an unusable system)
i removed the driver using this...

```
$ sudo apt-get remove --purge xorg-driver-fglrx
```

After that, ubuntu loaded as nicely as allways :)
Hope this helps
Thanks so much from an Edubuntu NOOB technology coordinator with three weeks of student work locked inside 2 stations with this exact issue!  I thank you, and my students thank you!  Drat!!! Now I have to grade their work...

---

