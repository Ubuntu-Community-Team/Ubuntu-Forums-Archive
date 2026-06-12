---
title: "A few newbie problems"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Hribar74 on 2009-11-30
Hi,
I'm new to Linux, and after installing Ubuntu Desktop 9.10, I think I'm in love.  The GUI is much easier than Windows to use, and it has some really nice features.  I originally installed it because I'm working on a computer science and networking degree and thought that this would be good thing to learn.  Well, with most things computer, it didn't go off without a few hitches.:-k

My first problem is sound.  I think I saw someone had a problem with sound not working on 9.10, but I can't find the post now. :-( No matter what I do to the volume control, I can't play any sounds.  Is this a known issue and are there any fixes?

#2, I dual booted with Vista, but now I can't start Vista.  I select Vista in the GRUB menu and it goes to a blank screen with a flashing cursor.  While I would love to do everything in Ubuntu, I need to use office 2007 and SolidWorks, and have some games that I love, all of which need Windows to run.

Thanks!
Dave

---

### Post by laidback on 2009-11-30
Hribar74
Welcome to the wonderful world of Linux and especially Ubuntu.
I'm not using 9.10 so my suggestions need to be viewed wisely, however:-

Sound:-
Test via System>Preferences>Sound
There are test buttons and drop downs to make device selections. I've noticed a number of Posts re 9.10 sound, there will be a solution I have no doubt.

Re Dual boot. I'm not experienced with this but have read recently that there are solutions, the worst case is to boot from your Windows CD (possibly recovery partition) and run the option that repairs the MBR (sets it back to initial state, I suspect you lose Ubuntu now), but I would strongly urge you to get other advice before rushing off with this option and most definitely research further. I mention it simply to give you hope that all is not lost.

Keep digging.

---

### Post by NoaHall on 2009-11-30
I have a solution for the sound, but it might break your set up.
Let me know if you want to try it. Try using "sudo update-grub" to update grub.

---

### Post by Hribar74 on 2009-11-30
Will updating GRUB cause any risk to my Ubuntu installation?  Had to install Ubuntu twice yesterday to get it working.

---

### Post by Geoff918 on 2009-11-30
> **Hribar74 said:**
> Will updating GRUB cause any risk to my Ubuntu installation?  Had to install Ubuntu twice yesterday to get it working.

Not the command he gave you. That would just look for any and all bootable setups (including Windows or any old kernels).

Just a quick question: Have you updated everything?

If not, try Update Manager in the System - Administration menu.

Or, if you want to do it command line you can do the following:

Applications - Accessories - Terminal

sudo aptitude update
sudo aptitude safe-upgrade

install all. If you haven't done that since your first boot, you may wish to. There are always plenty of security patches and bug fixes that come down the pipeline. Most especially right after a new distro release. 9.10 has only been out publicly for about one-month.

Have fun!

---

### Post by Hribar74 on 2009-12-01
Thanks all!

I did an update last night.  Actually had to stay up and start it at 2am.  Stupid Hughes Net bandwidth limits.  I'll see how everything works out when I get home today.:)

---

### Post by jotto! on 2009-12-01
A simple one to check....9.10 comes with sound muted by default! not sure why but a simple click with the mouse and you may have sound!

Good luck!

---

### Post by Bartender on 2009-12-01
I haven't downloaded this yet, so not familiar with it, but a number of regulars have recommended it as an easy way to fix Vista MBR problems.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Apparently MS released this package.  From what I've read it's basically the Recovery Console, tweaked so that it can run as as stand-alone application rather than part of a Vista install disc.

So you probably want to fix the Vista MBR first.

Then you can breathe a sigh of relief and think about whether you maybe want to install Ubuntu to a second HDD, or an external HDD, or try dual-booting again.  If you burned your installation disc at a high speed it might be corrupted.

---

### Post by Arthur_D on 2009-12-01
> **Hribar74 said:**
> My first problem is sound.  I think I saw someone had a problem with sound not working on 9.10, but I can't find the post now. :-( No matter what I do to the volume control, I can't play any sounds.  Is this a known issue and are there any fixes?
What sound card are you using?

---

### Post by Hribar74 on 2009-12-01
Bartender: Much thanks, I was one of those that had a recovery partition and no CD or DVD to boot from because the manufacturer was too cheap to include one.:D

jotto: Thanks, I know from doing some tech support at the workplace that the simplest things can bone you.;)  I did check the mute and it doesn't do anything.

Everyone else:  Thanks for the help, everyone here is great!

---

### Post by Primefalcon on 2009-12-01
try right clicking on the speaker in your bar and clicking sound preferences

select the output tab, check which device you want to use and make sure the sound isn't muted and is turned up for that device... welcome to the joys of pulseaudio

---

### Post by mjhouska on 2009-12-01
not sure about Vista and it's been a while but i think you can use the windows licence key on the computer case with any install cd. borrow a cd from a buddy and enter you key

---

### Post by mjhouska on 2009-12-01
It's the licence that needs to be legit not the cd. though i'd get it from someone you know

---

### Post by mjhouska on 2009-12-01
p.s make sure you got a copy of your network drivers first(experience talking!)  ;)

---

### Post by Primefalcon on 2009-12-01
> **mjhouska said:**
> It's the licence that needs to be legit not the cd. though i'd get it from someone you know
There's plenty of places you can get it from just do a search around, install a copy and you need to just insert the key using one of the many tools out there

after a quick search I found this

[http://www.shivaranjan.com/2006/09/18/how-to-find-and-change-windows-product-key-and-registration-information/](http://www.shivaranjan.com/2006/09/18/how-to-find-and-change-windows-product-key-and-registration-information/)

just insert your legitimate key using that, easy peasy

---

### Post by Hribar74 on 2009-12-01
I think the problem might possibly be with GRUB, I hope someone can look at this and let me know if this looks normal.

Here's the listing from the GRUB config file (The Windows boot section):

```
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 06c484ccc484c003
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 889ca0ac9ca0966a
    chainloader +1
}
```I really don't know what I'm looking at here yet, but I loaded it within windows on my laptop and it looked different.

Edit: I also tried the Vista recovery CD and it didn't do anything. :-(

---

### Post by sandyd on 2009-12-01
are you sure. very sure. that your clicking on the right vista menu.
as for sound, run 
```

alsamixer

```in the terminal and see if anythings muted.

edit: did you try using your vista recovery partition?
from what i see here, grub2 added an entry for it.

---

### Post by Hribar74 on 2009-12-02
> **carlee said:**
> are you sure. very sure. that your clicking on the right vista menu.
as for sound, run 
```

alsamixer

```in the terminal and see if anythings muted.

edit: did you try using your vista recovery partition?
from what i see here, grub2 added an entry for it.

Alsamixer appears to show everything at 100%.  

I did try the recovery partition's and it does exactly the same thing.

---

### Post by Hribar74 on 2009-12-02
Well, I did a few reinstalls of both OS's and it didn't fix it no matter what I did, so I just installed it inside of windows for the time being.  Not a great solution, but it'll work until I find some other way to fix it.

Thanks for all the idea's everyone!:D

---

### Post by Chris Edgell on 2009-12-02
Speaking of serendipity, I just solved my sound problem and had just posted the solution for the benefit of anyone who looked at my thread.

So imagine my surprise to go on down the posts and run on to this one and find someone else talking about the mute by default...which mine must have been.  Such a simple fix after so much else.  (Although it had been necessary for me to go through a couple of other steps described in my thread)

But just this hour...I HAVE SOUND...all because of that little red mute button being clicked.

Hope it solves your sound problem.

---

