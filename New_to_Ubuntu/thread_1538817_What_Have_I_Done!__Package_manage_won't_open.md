---
title: "What Have I Done!  Package manage won't open"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by aaron_kai on 2010-07-25
oops.  Screwed something up.   The noob blunders again.  I know just enough to be dangerous to myself.

I was trying to get a zlib library installed for Python 2.4.6 to make Zope2 configure properly.  The package manager didn't seem to have it, so I thought I would install zlib in a directory inside Python 2.4.6 where the Zope was looking for it.  So I downloaded zlib from the website, moved it to the Python 2.4.6 directory, and configured/made/made installed it.  

Well, that didn't work, and in addition to not working, it has also killed my synaptic package manager (at least, I think that is what killed it.)  anyway, checking my syslog, I get the following message:

Jul 25 18:12:22 aaron-desktop kernel: [80285.299695] synaptic[11318]: segfault at 1c4f ip 059e6e21 sp bfff271c error 4 in libc-2.11.1.so[596d000+153000]

What the heck does that mean?  I'm seeing "libc" in there, which makes me think I screwed up some library somewhere.  God knows what else is affected.

What do I do/what did I do?

---

### Post by jtarin on 2010-07-25
Things to try when APT is acting up:

```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

You may have to run them more than once.

---

### Post by collinp on 2010-07-25
In addition, try running synaptic from a terminal session and seeing what kind of output comes from it.

---

### Post by aaron_kai on 2010-07-25
well, things just went from bad to worse.

 I read another post and removed some etc cache.  then I upgraded and updated.  no problem.   unfortunately, on my way to post that here, firefox quit and then wouldn't open.    I restarted my computer hoping that would help. 

Now the computer won't work at all.  I get a purple screen and hear a drum roll, but get no login screen.  

I've been looking at the forum trying to figure out how to fix this.  Holding escape doesn't seem to do anything.  I have a ubuntu 9 live cd, but I downloaded 10 off the internet, and was running this when my computer crashed.  Can I use the ubuntu 9 disc to reboot root?  Is that what I should do?  

 Now what?  I'm afraid this is new territory.

---

### Post by jtarin on 2010-07-25
> **aaron_kai said:**
> well, things just went from bad to worse.

 I read another post and removed some etc cache.  then I upgraded and updated.  no problem.   unfortunately, on my way to post that here, firefox quit and then wouldn't open.    I restarted my computer hoping that would help. 

Now the computer won't work at all.  I get a purple screen and hear a drum roll, but get no login screen.  

I've been looking at the forum trying to figure out how to fix this.  Holding escape doesn't seem to do anything.  I have a ubuntu 9 live cd, but I downloaded 10 off the internet, and was running this when my computer crashed.  Can I use the ubuntu 9 disc to reboot root?  Is that what I should do?  

 Now what?  I'm afraid this is new territory.

Do you get a Grub screen? Did you install Grub to the MBR? Are you dual booting? If not..... Go [here]("https://help.ubuntu.com/community/Grub2") and scroll down to "Reinstalling GRUB". Then boot and repair as I outlined above.

---

### Post by aaron_kai on 2010-07-26
> **jtarin said:**
> Do you get a Grub screen? Did you install Grub to the MBR? Are you dual booting? If not..... Go [here]("https://help.ubuntu.com/community/Grub2") and scroll down to "Reinstalling GRUB". Then boot and repair as I outlined above.

I did install Grub to the MBR.  I am not dual booting.  

I followed your link and reinstalled grub various ways.  After trying the chroot method, holding down shift at reboot did produce a screen where I chose recovery mode and repaired my packages.  I rebooted, only to find that I got the same purple screen with no way to input anything that I know of.

---

### Post by nothingspecial on 2010-07-26
> **aaron_kai said:**
> 

  I'm seeing "libc" in there, which makes me think I screwed up some library somewhere.  God knows what else is affected.


If libc is broken, then just about everything is broken. I`d boot your live cd, copy the stuff you don`t want to loose and start again. If you`ve already tried chrooting from the live cd then I don`t know how you are going to fix it.

Some one who actually knows what thy are talking about may come along and tell you.

I do know, though that you need libc (6), to run just about anything.

---

### Post by muteXe on 2010-07-26
if you're interested, this is the background on the nature of your first error:
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

---

