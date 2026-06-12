---
title: "Synaptic not working"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Tholley on 2009-07-24
I was trying to install Virtualbox, from instructions from this website, [http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop](http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop) 

It did not work after I did "sudo aptitude update", so I went to the Ubuntu documentation like I should have to begin with, and when I try to load Synaptic Package Manager I get this error msg:

 E: Malformed line 55 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

the only option is to click close, then synaptic closes.

I'm thinking I may just have to "undu" what I have done. Hoping it will be as easy as that if someone can tell me how to go about it.

Thanks ahead of time!

---

### Post by drs305 on 2009-07-24
There is at least one error, beginning on line 55. Open sources.list as root and take a look at the line. It should start with "deb" or a comment symbol.

```

gksudo gedit +55 /etc/apt/source.list

```

All normal lines in sources.list should begin with either a comment symbol # or "deb". Anything else will produce an error. 

If this is near the last line of the file, chances are good that line 55 and everything below it is not supposed to be in the file. If you aren't sure, post the contents here and we can help.

---

### Post by starcraft.man on 2009-07-24
The line you added to the sources list must not have been formatted properly. Please open back the /etc/apt/sources.list via any text editor (if you want gedit like the instructions had you) and paste the entire output in a reply with code (# on gui) tags. Often people just forget to put deb at the front of a line and a space then the long url with options. In any case, easy to spot and fix.

Edit: Well drs faster than my typing tonight. Mind you, I'm hampered by a tasty chocolate doughnut. Hard to keep both hands typing... :D

---

### Post by colau on 2009-07-24
> **Tholley said:**
> I was trying to install Virtualbox, from instructions from this website, [http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop](http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop) 

It did not work after I did "sudo aptitude update", so I went to the Ubuntu documentation like I should have to begin with, and when I try to load Synaptic Package Manager I get this error msg:

 E: Malformed line 55 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

the only option is to click close, then synaptic closes.

I'm thinking I may just have to "undu" what I have done. Hoping it will be as easy as that if someone can tell me how to go about it.

Thanks ahead of time!

Can you post: 
```

cat /etc/apt/sources.list

```

---

### Post by Tholley on 2009-07-24
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)

---

### Post by drs305 on 2009-07-24
The last line
> **Tholley said:**
> 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
**deb [http://download.virtualbox.org/virtualbox/**](http://download.virtualbox.org/virtualbox/**)


should be:
> 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free


---

### Post by starcraft.man on 2009-07-24
drs noted you the correct line. You were missing the modifiers, telling the manager where to look in the repository (for jaunty and the nonfree version).

Also, I'd just like to note your medibuntu repo is commented out, did you intend that? Just noting. Take care in future when adding lines.

---

### Post by Tholley on 2009-07-24
> **drs305 said:**
> The last line


should be:

Thanks for the quick response and fix! that worked!

I had a feeling it was something simple.

Thanks again!

---

### Post by Tholley on 2009-07-24
> **starcraft.man said:**
> 
Also, I'd just like to note your medibuntu repo is commented out, did you intend that? Just noting. Take care in future when adding lines.

commented out? What does that mean?

---

### Post by drs305 on 2009-07-24
> **Tholley said:**
> commented out? What does that mean?

The second to last line begins with a # symbol. This is referred to as a "comment" symbol because lines beginning with this symbol (usually) are not acted upon. They are called comments because you can place a descriptive comment after the symbol.

So starcraft.man was pointing out that the medibuntu line had a comment in front of it and that it wasn't being used. By taking out the # symbol you could "activate" that line. Note that if you do you next may get messages about not having the proper key. If that happens, go here:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Here is a link on Repositories and how they work:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by starcraft.man on 2009-07-24
> **Tholley said:**
> commented out? What does that mean?

Apologies, using technical word. You'll notice that in front of the line is a # sign. This is a fairly universal means by which advanced users/programmers leave comments in scripts and text files that get parsed (i.e. used or referenced by programs) For example synaptic parses your sources to see where it should look for programs. The pound sign basically tells the program to ignore the entire line after #. You'll notice much text on the sources.list, this isn't deemed malformed because it's all preceded by a comment which precludes it from being looked at by programs using the file. You'd probably want the repo enabled unless you've a reason to disable it.

For a longer explanation, please see my guide on installation.

Edit: Darn it, man, I wasn't eating that time.... You make me feel slow drs305 :p.

---

### Post by drs305 on 2009-07-24
> **starcraft.man said:**
> Edit: Darn it, man, I wasn't eating that time.... You make me feel slow drs305 :p.

But your entry was so much better technically! 


;-)

---

### Post by Tholley on 2009-07-24
I don't remember if I was told to disable it or not. I followed several guides that were recommended in this forum when I first set up Ubuntu. I took the # out and see it I notice any changes.

---

