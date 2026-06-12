---
title: "Just a few questions that probably have obvious answers."
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-04
1.  I was reading that Ubuntu Newbie's Guide and it said that Lilo.conf was the configuration for the boot screen, but it's pretty cryptic.  How would I go about changing the default option in the loader?

2.  What's the difference in utility between Ubuntu Software Center and Synaptic Package Manager?  It seems like there's a lot of overlap between the two.

3.  Everything non-Canonical utility I've downloaded so far (including Adobe Flash) has been in .tar.gz format without any sort of instructions explaining where to place the files and it's been a pain in the *** trying to divine where they go in this foreign file system.  What's the deal with that?  And is there some reason executables seem so rare compared to Windows?

---

### Post by J V on 2010-03-04
1. I was reading that Ubuntu Newbie's Guide and it said that Lilo.conf was the configuration for the boot screen, but it's pretty cryptic. How would I go about changing the default option in the loader?

I would install startupmanager if I were you, its a pain to keep track of the different grubs...

2. What's the difference in utility between Ubuntu Software Center and Synaptic Package Manager? It seems like there's a lot of overlap between the two.

They are both just frontends (Ways to display) to apt-get, apt-get does all the grunt work, these 2 just make it easier to use. Synaptic is for more advanced work (More features etc) and software center is for the "average joe"

3. Everything non-Canonical utility I've downloaded so far (including Adobe Flash) has been in .tar.gz format without any sort of instructions explaining where to place the files and it's been a pain in the *** trying to divine where they go in this foreign file system. What's the deal with that? And is there some reason executables seem so rare compared to Windows?

You have several thousand executables on your system right now... problem is they don't all end with exe...

Skype comes in deb, everything else I've looked for has come in a deb, and the rest has clear instructions on the page you download it from (including flash btw)

---

### Post by Everynameistaken on 2010-03-04
Hmm, I dunno.  Maybe I've been looking at the wrong files.

Oh, one last thing.  I installed a bunch of stuff from Synaptic and Software Center and now my /home/user folder has a ton of hidden folders in it.  Is that normal?  Are they necessary files?

---

### Post by oldos2er on 2010-03-04
Ubuntu uses grub, not lilo. 9.10 uses grub2, the configuration of which is somewhat more complicated than that of legacy grub, at least if you're unfamiliar with it. See [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

 If you install packages (e.g. flash) from the repositories, you can save yourself some grief. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

 The hidden folders in /home/user contain your configuration files for the apps they correspond to.

---

### Post by Everynameistaken on 2010-03-04
Alright.  How likely is it that I'm going to need to alter hidden files/folders in Ubuntu?  Is it as common to do as it is in Windows?  Because if it's unnecessary I'll just leave them hidden, I guess.

And one other thing, that Startup Manager didn't seem to work.  It starts and remembers the settings I choose and then says it's configuring the system, but the behavior of the Grub screen doesn't change.

---

### Post by ndefontenay on 2010-03-04
Hi.

Keep them hidden and ignore them until told otherwise (like delete the hidden open office file in your home to fix the recovery problem if it ever shows up)

Nico

---

### Post by sandyd on 2010-03-04
p.s. theirs a deb for flash (linux) on adobe's site. you just need to go to [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)
and choose "apt for ubuntu 9.04+"
if your using 64 bit linux, see my signature.

---

