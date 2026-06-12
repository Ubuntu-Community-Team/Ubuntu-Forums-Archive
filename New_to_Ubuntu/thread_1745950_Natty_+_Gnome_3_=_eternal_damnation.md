---
title: "Natty + Gnome 3 = eternal damnation?"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Zerberus on 2011-05-01
Hey there,

I am a happy ubuntu user since a couple of months time, I have a small netbook, and despite the fact that unity was made for netbooks I never ever liked or looked at unity, I never liked it, and it probably never will be my cup of tea. 

Anyway so I am actually running my netbook from my livecd/liveusb, cause actually after every natty + gnome 3 install my netbook enters in some "lost in blackhole" mode, and never starts up, I am not a advanced user to fix the problems in command line or in whatever other commands I have to use.

My simple question, does natty work with gnome 3? or should I stick with gnome 2 until oneiric comes out?

I know shuttleworth might not be too happy about my rant about unity, but I am really not a fan of it to be honest...

---

### Post by Quackers on 2011-05-01
Yes it does :-)
I am using gnome-shell with Natty. You must first disable autologin, otherwise you won't get to the desktop (unless that has now been fixed, but I don't think so).
Obviously gnome-shell (gnome3) is still in its infancy.
How did you install it? Via the gnome3team.ppa?

---

### Post by Jesus_Valdez on 2011-05-01
Are you upgrading to gnome 3 using a ppa? 

Are you following some of the HOWTOS that appear in the forums?

Anyway, you can have the Gnome Shell alongside with Unity without much trouble if you compile it yourself.

---

### Post by gemoyeni on 2011-05-01
I agree this is the worst version of ubuntu,been using ubuntu since 6.10,going back to 10.10 today,if I want a netbook I will buy a netbook.

---

### Post by Zerberus on 2011-05-01
> **Quackers said:**
> Yes it does :-)
I am using gnome-shell with Natty. You must first disable autologin, otherwise you won't get to the desktop (unless that has now been fixed, but I don't think so).
Obviously gnome-shell (gnome3) is still in its infancy.
How did you install it? Via the gnome3team.ppa?

Well after I added the gnome 3 ppa through ubuntu tweak
I entered the following code
```

sudo apt-get update
sudo apt-get dist-upgrade

```


> **Jesus_Valdez said:**
> Are you upgrading to gnome 3 using a ppa? 

Are you following some of the HOWTOS that appear in the forums?

Anyway, you can have the Gnome Shell alongside with Unity without much trouble if you compile it yourself.

Yes I have used the ppa, I did not use a howto I thought using my brain and being partially computer literate would be enough to tell my computer to upgrade the files that are required for gnome 3 through ppa with the command lines above.

Hmm but I do have to say that compiling it myself is out of my depth, I usually use gambas for any compilations or well the make and make install commands, but thats as far as my knowledge goes, I know of git, and subversion as well, but it wouldn't help much either by compiling from scratch, I would have been happier if they would have just supplied natty with gnome as a alternative.

Maybe mint will have gnome 3 i hope.

---

### Post by Quackers on 2011-05-01
If you have added the gnome3team.ppa you don't need any command line stuff (unless something goes wrong) you just need to update with Synaptic. Or that's all I did originally. All the needed packages were installed at once.
Admittedly all did not go perfectly at first, but it's been working well for about 3 weeks.
See this (long) thread :-)
[http://ubuntuforums.org/showthread.php?t=1722627](http://ubuntuforums.org/showthread.php?t=1722627)

---

### Post by scott-ian on 2011-05-01
I'm running Natty with Gnome 3.  You can see my blog post about it:
[Ubuntu Natty Narwhal with Gnome Shell]("http://ian.perebruin.com/articles/natty-gnome-shell.html")
It worked fine for me, but I am unable to load unity.  Not that bothered.

---

### Post by Zerberus on 2011-05-02
I got around to installing it from Git

using this

[http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html](http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html)

and then making a session using this

[http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3](http://askubuntu.com/questions/22946/how-do-i-install-the-latest-version-of-gnome-3)

but to be honest, it doesnt work with the session and having to use terminal to swap between gnome 2 and 3 is just not doing it for me, I am dissapointed with natty, very much so....

---

