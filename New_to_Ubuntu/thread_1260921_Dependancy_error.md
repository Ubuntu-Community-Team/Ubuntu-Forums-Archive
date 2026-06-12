---
title: "Dependancy error"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Rufus T. Firefly on 2009-09-08
Hello.

I am new to all this in every sense. I'm very used to XP Pro though currently running the home edition. I installed Ubuntu via the Wubi facility and would like to connect to the internet from Ubuntu.

I have a speedTouch 330 modem and have read this post from vladi11:

[http://ubuntuforums.org/showthread.php?t=797804](http://ubuntuforums.org/showthread.php?t=797804)

However, when I try to install at step 6 (gnome extras) I get an error report:

[COLOR=Red]Dependancy not satisfied: ifibb4 (I think)

[COLOR=Black]I note that the page that vladi11 refers to indicates that the downloads are for Intel x86 whereas my processor is an Athlon, model unknown. Could this have something to do with it?

My apologies if something of this nature is posted elsewhere but it'll take me a little while to find my way round.

Any help and advice appreciated.

R.
[/COLOR][/COLOR]

---

### Post by dearingj on 2009-09-08
> **Rufus T. Firefly said:**
> Hello.
[COLOR=Black]I note that the page that vladi11 refers to indicates that the downloads are for Intel x86 whereas my processor is an Athlon, model unknown. Could this have something to do with it?
[/COLOR]

I don't think that would have anything to do with it, as Wikipedia says that the Athlon processors use the x86 architecture, with the exception of Athlon 64 which uses amd64.

[http://en.wikipedia.org/wiki/Athlon](http://en.wikipedia.org/wiki/Athlon)

You also might want to check the name of the missing dependency; I searched through Synaptic and [http://packages.ubuntu.com](http://packages.ubuntu.com) and couldn't find anything named ifibb4.


Edit: I did find a package on [http://packages.ubuntu.com](http://packages.ubuntu.com) called libffi4. Is that it?

---

### Post by Rufus T. Firefly on 2009-09-08
Thanks for the reply.

It is indeed libffi4 however I cannot find it on the page you linked to. Where should I be looking?

R.

---

### Post by halitech on 2009-09-08
just open a terminal and run
```
sudo apt-get install libffi4
```

---

### Post by dearingj on 2009-09-08
Which version of Ubuntu are you running?

Here's the link for ffi4 assuming you're running Hardy (8.04):
[http://packages.ubuntu.com/hardy/libffi4](http://packages.ubuntu.com/hardy/libffi4)

---

### Post by Rufus T. Firefly on 2009-09-08
I've only recently installed it. I believe it's 9.04 Jaunty Jalopy or some such.

I'm afraid I don't know what Hardy is, sorry.

halitech, wouldn't I need an internet connection to be able to do that?

Anyway, thanks for the link, dearingj. Let's see what happens:confused:

R.

---

### Post by halitech on 2009-09-08
sorry, yes you would, didn't think about that

---

### Post by dearingj on 2009-09-08
> **Rufus T. Firefly said:**
> I've only recently installed it. I believe it's 9.04 Jaunty Jalopy or some such.

I'm afraid I don't know what Hardy is, sorry.

halitech, wouldn't I need an internet connection to be able to do that?

Anyway, thanks for the link, dearingj. Let's see what happens:confused:

R.

The links in the tutorial you found are for hardy, aka Ubuntu 8.04, which is a year older than the version of Ubuntu that you have. Here are the packages you want to install instead:
[http://packages.ubuntu.com/jaunty/libgda3-common](http://packages.ubuntu.com/jaunty/libgda3-common)
[http://packages.ubuntu.com/jaunty/libgda3-3](http://packages.ubuntu.com/jaunty/libgda3-3)
[http://packages.ubuntu.com/jaunty/libgdl-1-common](http://packages.ubuntu.com/jaunty/libgdl-1-common)
[http://packages.ubuntu.com/jaunty/libgdl-1-0](http://packages.ubuntu.com/jaunty/libgdl-1-0)
[http://packages.ubuntu.com/jaunty/python/python-gnome2-extras](http://packages.ubuntu.com/jaunty/python/python-gnome2-extras)

Good luck

---

### Post by Rufus T. Firefly on 2009-09-08
[I][B]Success!!!

[/B][/I]Many thanks, dearingj, for all your help. As it happened I couldn't install one of your links but it turned out not to matter.

Now then, I found I couldn't log in to here from Ubuntu as one of my password characters is an Alt symbol. How do I get these things to work in Ubuntu?

Regards,

R.

---

### Post by dearingj on 2009-09-08
> **Rufus T. Firefly said:**
> [I][B]Success!!!

[/B][/I]Many thanks, dearingj, for all your help. As it happened I couldn't install one of your links but it turned out not to matter.

Now then, I found I couldn't log in to here from Ubuntu as one of my password characters is an Alt symbol. How do I get these things to work in Ubuntu?

Regards,

R.

Glad to hear you got it working :)

As for your password, sorry but that's beyond my knowledge. I'd suggest you start a separate thread if you haven't already, since that's a separate problem from the one we just solved.

---

### Post by Rufus T. Firefly on 2009-09-08
> **dearingj said:**
> Glad to hear you got it working :)

As for your password, sorry but that's beyond my knowledge. I'd suggest you start a separate thread if you haven't already, since that's a separate problem from the one we just solved.


Cheers! (insert thumbs up emoticon!)

Someone else  has started an Alt+ thread and, from that, it appears not to be possible. Looks like I'll just have to change my password.

R.

---

