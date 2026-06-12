---
title: "Cleaning out pre installed apps. (read, ruining ubuntu for science)"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Qjet on 2009-02-14
One of the things I've always tried to do with operating systems is use third parties for whatever task i need to accomplish. For the most part ubuntu's defaults are really quiet good. With the exception of a few things

Don't like evolution,
Don't like totem,
Don't need orca,
Don't need f-spot,
Don't need toms notes,
Quiet a few other examples of stuff that doesn't really help me.

The trouble is removing these things is blocked by Add/remove
and involves removing some rather important packages with synaptic package manager. 

See being an absolute beginner [[SIZE="1"]note location of thread.[/SIZE]] is not knowing how linux works from the ground up, I'm not really an authority on what needs to be there for the OS to work. I also don't know what needs to be there for the programs that I do use in the OS to work either.

[[SIZE="1"]At this point I'd just like to mention if ubuntu had popped up with some sort of "Hey, you want any of this?" before the installation, then I would of being able to build what i wanted from the ground up. Removing the need for me to do the following[/SIZE]] 

I do want to have everything i put on my desktop there by me, SO TO THIS END, i've gone ahead and selected EVERYTHING in synaptic package manager for removal, with the exception of selecting no for the dialog "Hey this is going to turn your computer inside out, are you a masochist?" 

I am kind of aware this is going to backfire, but damn it, this is for science. [IMG]http://img253.imageshack.us/img253/1047/emoteducationam0.gif[/IMG]

So basically i'm going to remove everything and then go through the package manager and pick up whatever appears to be system essential packages (things like sudo) 

once THIS backfires i'm going to reinstall ubuntu and check back here to see if someone had posted the smart way to go about this. Something i would reeeally appreciate :).

---

### Post by geirha on 2009-02-14
Perhaps you want to do this in a virtual machine in virtualbox? You can do snapshots in virtualbox, basicly taking images of the virtual harddrive, so when it backfires, you can easily go back to the previous snapshot and try again ;)

Also, I think you should consider trying LFS (Linux from scratch). It's a GREAT resource for learning how linux distributions works. You basicly create your own linux from scratch, step by step, and with an explanation of what each step does.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by Qjet on 2009-02-14
not a bad suggestion <.X
those virtual boxs basically simulate computers right? Maybe i could combine those two suggestions...

---

### Post by llamabr on 2009-02-14
Unless you're really hurting for disk space, I don't really see the point of doing this.  Most of those apps will sit there forever, not hurting anyone, until you finally want to use them.

By going through synaptic and unclicking everything you've never heard of, you're almost certainly going to break your system.

On the other hand, you can safely remove those things you already mentioned (I don't use them either).  And it'll simultaneously remove all associated libraries and things.

Finally, if you want a very barebones install, ubuntu is not the way for you.  Ubuntu is purposefully bloated with everything you might want, for those users who want everything, or don't know what they want.  Check out something like [http://damnsmalllinux.org](http://damnsmalllinux.org)

---

### Post by geirha on 2009-02-14
> **Qjet said:**
> not a bad suggestion <.X
those virtual boxs basically simulate computers right? Maybe i could combine those two suggestions...

Yep, doing LFS in a virtualbox is a good idea. Compiling will probably take a bit longer, but on the plus side, you'll be able to "pause" it at any time by just suspending the virtual machine (it takes a rather long time to complete).

---

### Post by Kain000 on 2009-02-14
If you really like Ubuntu you may want to check this out

It's ubuntu without much of the extra bloat

[URL="https://help.ubuntu.com/community/Installation/MinimalCD"]
[/URL]

---

### Post by Qjet on 2009-02-14
> **llamabr said:**
> Unless you're really hurting for disk space, I don't really see the point of doing this.  Most of those apps will sit there forever, not hurting anyone, until you finally want to use them.
 Quiet right. My only issue is when those defaults start butting in the way of prefered programs. Like totem ineptly trying to play a video it doesn't have the codec for. Evolution trying to send emails for me, that kinda stuff.

> By going through synaptic and unclicking everything you've never heard of, you're almost certainly going to break your system. SCIENCE!

> On the other hand, you can safely remove those things you already mentioned (I don't use them either).  And it'll simultaneously remove all associated libraries and things.
yessir! I tried that. I think however some of totems packages have some essential parts of the GUI that depend on them, You know things like the gnome-bar. Same goes for evolution too. 

Maybe ubuntu isn't the right distro for me... buuut. Like if we could get some decaffeinated ubuntu, something that came with the tools we would need to expand the system. APT, x windows and gnome for easy interface, the sudo package, stuff like that. letting us pick our own front end tools. 

In any case LFS looks like it should be fun. I'm gonna take a week long whack at it.

Thanks for the advice!

---

### Post by llamabr on 2009-02-14
Nautilus is required for gnome, so you'll need to leave that alone.  You can adjust the mime settings for everything else.  Linux is infinately configurable, so if it's doing something you don't like, you can change it.

I believe xubuntu is a pared down version, that is, with all the stuff turned off by default.  But I've never tried it.

If what you want is barebones and simple, try changing your window manager, or switch to window maker.  It's my preferred slimmed down choice.

---

### Post by geirha on 2009-02-14
A few pointers on LFS in virtualbox. I just read the introduction of the latest stable LFS book. It mentions that the LFS liveCD is unfortunately no longer being maintained, but I suggest you try the latest LFS liveCD, and use the LFS book and packages it contains.

Once you've given virtualbox the lfslivecd iso as a cdrom and booted it, you can read the LFS book it contains by using the text web browsers w3m or lynx. E.g.
```
w3m /usr/share/LFS-BOOK-6.3-HTML/index.html
```

You'll need to switch to another terminal to run the actual commands it explains. You normally do that by hitting Ctrl+Alt+F1, Ctrl+Alt+F2 etc, but that will change to a virtual terminal on the host system, not the virtual machine. Instead you use the Host key. Host+F1, Host+F2 etc. The host key is by default the right Ctrl key.

If your mouse get trapped inside the virtual machine, hit the host key to untrap it. 

Hope this saves you some time :)

---

### Post by avtolle on 2009-02-14
Take a look at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) for a minimal installation. For some more information, [http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal).

---

### Post by the.phantom on 2009-02-14
> Quiet right. My only issue is when those defaults start butting in the way of prefered programs. Like totem ineptly trying to play a video it doesn't have the codec for. Evolution trying to send emails for me, that kinda stuff.


system/preferences/prefered applications

and you can change from evolution to t-bird and a few others

f-stop is a little different but you can kill it
with
places/home/ and in the window that pops up
on the top click EDIT
and then the multimedia tab

and tell f-stop not to open

and have you intalled the "restricted codex" for streaming and such

---

### Post by Charrlie on 2009-02-15
I have a similar question with regard to all the games and educational stuff for kids.  I am not sure if it is a Dell thing or was part of Ubuntu 8.0.4 but I really don't need or want that stuff and un-clicking does not seem to work. How do I get rid of them?  I doubt they are needed but if I am wrong please let me know so I can stop trying to get rid of them.

---

### Post by anjilslaire on 2009-02-15
If you really want to run Ubuntu wity only what you want installed, Install the OS with the Server ISO, and don't add anything.

This will leave you with a bare terminal prompt, with no GUI at all. after this, 1st step is 
```

sudo apt-get update
sudo apt-get upgrade

```

After this, install your basic desktop of choice, with no fluff:
```

sudo apt-get install gnome
```
or
```

sudo apt-get install kde
```
or
```

sudo apt-get install xfce
```

Then go from there via synaptic

---

### Post by Qjet on 2009-02-15
ooo. Also an effective method. Still gonna burn through LFS though.

---

### Post by Xiong Chiamiov on 2009-02-15
Thumbs up to minimal install.

I probably wouldn't recommend LFS for you, just since you're new to the game.  I've been slowly working my way towards that, but it also depends on whether or not you're trying to get an OS to *use*, or an OS to tinker with.  For me, Arch Linux has provided the happy medium between those, but the best one for you will depend on your personality and time constraints.

Recommended progression:
Ubuntu -> Debian -> Arch -> Slackware -> Gentoo -> LFS

---

