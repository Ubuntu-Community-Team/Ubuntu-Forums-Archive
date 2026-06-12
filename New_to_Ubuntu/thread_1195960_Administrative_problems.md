---
title: "Administrative problems"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-06-24
Hello all!
I have some strange problems with my system...First, my system monitor is not working anymore. If I click on it nothing happens and if I run it in a terminal I get:
```
troll@my-precious:~$ gnome-system-monitor

** (gnome-system-monitor:23639): WARNING **: SELinux was found but is not enabled.


** ERROR **: Child 23640 failed with status 256
aborting...
Aborted
``` 
Then, my Hardware Drivers and Software sources stopped working too.... I don't know the commands to run them in a terminal, so at least I can see the error messages.
Can someone help?

---

### Post by carml on 2009-06-24
Did you try to reboot and choose the recovery mode->try to fix broken packages? However it's a shot in the dark.

---

### Post by Troll_the_Great on 2009-06-24
> **carml said:**
> Did you try to reboot and choose the recovery mode->try to fix broken packages? However it's a shot in the dark.

No use... :(

PS: what is this SELinux anyway? I had used Hardy for over a year now and never heard or had problems with it...

---

### Post by carml on 2009-06-24
Sorry,the one I suggested you is at the moment my last resort.
SELinux is a word I see on boot,if I recall correct, sorry:(.
What you was doing before that error?

---

### Post by decoherence on 2009-06-24
> **Troll_the_Great said:**
> No use... :(

PS: what is this SELinux anyway? I had used Hardy for over a year now and never heard or had problems with it...

Hi there,

The SELinux warning probably isn't important. I get the same warning and it runs fine for me. FYI, SELinux is a security framework. It is included in Ubuntu but not enabled by default because it's overkill for what most people need and complicates the system.

According to Google, there are others who have had this problem but the issues seem to resolve themselves or are resolved by installing additional packages from the repository (neither of which makes sense.)

I used the search terms > gnome-system-monitor "failed with status 256"

I'm not going to suggest a solution because they all suck. Take your pick! ;)

Also, if you have the time take a [look at this]("https://wiki.ubuntu.com/DebuggingProgramCrash") and see if you can get a bug report going.

ADD: you may have difficulty following the directions in that link. It appears there is something wrong with Ubuntu's keyserver. Very, very unfortunate :( I'll start up a new thread for that. For now, you can ignore the parts about adding signed keys -- it'll work anyway.

---

### Post by Troll_the_Great on 2009-06-24
> **carml said:**
> What you was doing before that error?
Well....nothing, or nothing noticeable to recall.It just stopped working, along with Hardware Drivers and Software Sources...

---

### Post by carml on 2009-06-24
I looked for SELinux on Google and I found the same result:it's a security feature.
Did you try to reboot the system and find out if the problem pops up again? :confused:

---

### Post by Troll_the_Great on 2009-06-29
Hy all! I figured out what my problem was, and it had nothing to do with SELinux. I found a chap with similar problems here: [http://tech.element77.com/2008/08/ubuntu-lsbrelease-nameerror-global-name.html](http://tech.element77.com/2008/08/ubuntu-lsbrelease-nameerror-global-name.html) It seems that *apt* failed due to an internal failure in *lsb_release*. I corrected it by removing ```
deb http://security.debian.org/ etch/updates main contrib non-free
``` from /etc/apt/sources.list .I don't know why it suddenly stopped  working, but I'm glad I fixed it.
Cheers!

PS:Now that I found out what SELinux is, do I need it? Should I install it?

---

### Post by mcduck on 2009-06-29
> **Troll_the_Great said:**
> 
PS:Now that I found out what SELinux is, do I need it? Should I install it?
You already have it installed, and no, you don't need it unless you work for NSA or some other shady government agency or other organization that requires *extremely* high security.

For any normal use, be it in home or in corporate environment, SELinux is overkill.

---

