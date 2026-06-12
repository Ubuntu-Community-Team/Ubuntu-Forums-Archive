---
title: "Is there a way to get the windows 7 window snap function in Ubuntu?"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by venom104 on 2011-07-07
I'm talking about, when in windows 7, you drag a window to the left or right of the screen, it makes an outline of the window on half the screen and if you let the mouse button go, it resizing and repositions the window in half the screen.

---

### Post by Paqman on 2011-07-07
Ubuntu 11.04 does this, but earlier versions don't.

---

### Post by LowSky on 2011-07-07
> **Paqman said:**
> Ubuntu 11.04 does this, but earlier versions don't.

But you can get that function using Compiz

Its called 'snapping windows.'

---

### Post by venom104 on 2011-07-07
> **LowSky said:**
> But you can get that function using Compiz

Its called 'snapping windows.'


Could you instruct me on how to do this? I'm using Ubuntu 10.04.2 (lucid lynx)

---

### Post by MG&amp;TL on 2011-07-07
I can tell you how to get compiz, but from then  on, you'll need someone with expertise..:(

from terminal: (Ctrl-Alt-T)
type:

"sudo apt-get install compizconfig-settings-manager"

OR

from ubuntu software centre: (under applications at the bottom)

search for 'ccsm' and choose the 'advanced' one-the one with about 100 ratings.
apologies if you have compiz already.

---

### Post by nerdy_kid on 2011-07-07
Ubuntu 10.04 does not have the compiz plugin.  You can use kwin (KDE's window manager) or you can upgrade to 11.04, or you can risk breaking your system by upgrading just compiz -- I did that with 10.10, but its not the "neat" way to go.

---

### Post by MG&amp;TL on 2011-07-07
You could try this:

[http://www.multimediaboom.com/how-to-enable-windows-7-aero-snap-in-ubuntu-tweak/]("http://www.multimediaboom.com/how-to-enable-windows-7-aero-snap-in-ubuntu-tweak/")

This is backed up on several different sites. However, none of them are official ubuntu ones, so be very careful if you do follow these instructions, or wait for an admin or someone to visit this thread. (I've bumped it enough now :))

EDIT: Ignore me, listen to nerdykid-he will know a lot more about it then me.

---

### Post by Frogs Hair on 2011-07-07
After installing the CCSM , open it and go to the window management section and place a check in the box next to snapping windows for the default setting .

---

### Post by venom104 on 2011-07-07
> **MG&TL said:**
> You could try this:

[http://www.multimediaboom.com/how-to-enable-windows-7-aero-snap-in-ubuntu-tweak/](http://www.multimediaboom.com/how-to-enable-windows-7-aero-snap-in-ubuntu-tweak/)

This is backed up on several different sites. However, none of them are official ubuntu ones, so be very careful if you do follow these instructions, or wait for an admin or someone to visit this thread. (I've bumped it enough now :))

EDIT: Ignore me, listen to nerdykid-he will know a lot more about it then me.

I did this and it didn't work, I'm guessing it's because 10.04 is missing the plugin like the other guy said. Oh well, guess I'll have to go without it.

---

### Post by alphacrucis2 on 2011-07-07
> **venom104 said:**
> I did this and it didn't work, I'm guessing it's because 10.04 is missing the plugin like the other guy said. Oh well, guess I'll have to go without it.

Does your graphics card driver support 3D accelleration? Compiz bling is not going to work with out that. If you have 3D then you will also want to install compiz-fusion-plugins-extra. 

Edit. I just checked on my old 10.04 machine. The support for snapping windows definitely exists in that version of compiz.

---

### Post by venom104 on 2011-07-07
> **alphacrucis2 said:**
> Does your graphics card driver support 3D accelleration? Compiz bling is not going to work with out that. If you have 3D then you will also want to install compiz-fusion-plugins-extra. 

Edit. I just checked on my old 10.04 machine. The support for snapping windows definitely exists in that version of compiz.


My graphics card should support 3d acceleration...it's an NVIDIA 9400 GT. I don't quite remember how to check if 3d acceleration is enabled, but I think it has something to to do with glxinfo...here is the output

```

glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce 9400 GT/PCI/SSE2/3DNOW!
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```

I followed the instructions to a T, and when I drag the windows to the left, right, or top of the screen and wait 1 second, NOTHING happens.

---

### Post by venom104 on 2011-07-07
I went back and retraced my steps again...and when I go to edge bindings, then assign values for "run command 0, 1, and 2, as left, right, and top...I get an error on each one. If I click on the pencil icon then type Left and press enter, a box pops up that says, " "" is not a valid edge mask ". I tried setting a key binding, but when I go to a window and press the key combination a box pops up that is titled "metacity" and says " an error has occurred"

I checked and I have the package compiz-fusion-plugins-extra installed.

EDIT: I tried key bindings for all the commands, and the only one that works in run command 2, the "top" one.

---

### Post by nerdy_kid on 2011-07-08
> **alphacrucis2 said:**
> Does your graphics card driver support 3D accelleration? Compiz bling is not going to work with out that. If you have 3D then you will also want to install compiz-fusion-plugins-extra. 

Edit. I just checked on my old 10.04 machine. The support for snapping windows definitely exists in that version of compiz.

Snapping windows is NOT the windows 7 style "snap".  The "snapping windows" plugin "Enables windows edges resistance" -- not what the OP is talking about.  The compiz plugin that he wants is called "Grid" and is available afaik only with compiz 9.x and Ubuntu Natty.

---

### Post by nerdy_kid on 2011-07-08
this is how to install the natty version of compiz.  Note that I only tried this on Maverick, and it didn't bust anything for me.  It very well might break something, and may not be very easily reversible.

run:
```

gksu gedit /etc/apt/sources.list

```

find:  "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted"

and change "lucid" to "natty" (without quotes)

find:  "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted" and change "lucid-updates" to "natty-updates".

Save the file, and close the text editor.  This is the dangerous part.
Run:
```

sudo apt-get update
sudo apt-get install compiz

```
When you run apt-get install compiz, it will present to you a list of packages that will need to be updated along with compiz.  You may want to post that list here to make sure there are no critical libraries being updated.  If you are confident that the update is safe without posting the output, then run the command through.  Once it has completed, rerun 
```

gksu gedit /etc/apt/sources.list

```
and reverse the changes you did to the file. Then save and close the text editor, and run
```

sudo apt-get update

```
and you should be all good.  Log out/back in for the changes to take effect, then open ccsm, find and enable the "grid" plugin.
Good luck :)

---

### Post by venom104 on 2011-07-08
> **nerdy_kid said:**
> this is how to install the natty version of compiz.  Note that I only tried this on Maverick, and it didn't bust anything for me.  It very well might break something, and may not be very easily reversible.

run:
```

gksu gedit /etc/apt/sources.list

```find:  "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted"

and change "lucid" to "natty" (without quotes)

find:  "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted" and change "lucid-updates" to "natty-updates".

Save the file, and close the text editor.  This is the dangerous part.
Run:
```

sudo apt-get update
sudo apt-get install compiz ccsm

```When you run apt-get install compiz ccsm, it will present to you a list of packages that will need to be updated along with compiz.  You may want to post that list here to make sure there are no critical libraries being updated.  If you are confident that the update is safe without posting the output, then run the command through.  Once it has completed, rerun 
```

gksu gedit /etc/apt/sources.list

```and reverse the changes you did to the file. Then save and close the text editor, and run
```

sudo apt-get update

```and you should be all good.  Log out/back in for the changes to take effect, then open ccsm, find and enable the "grid" plugin.
Good luck :)

Tried to do install the ccsm package and this is what happened
```

venom@secmorg:~$ sudo apt-get install compiz ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm

```Followed your directions exactly. I did a google search on why it wouldn't install and found this [http://ubuntuforums.org/showthread.php?t=614642](http://ubuntuforums.org/showthread.php?t=614642), I tried installing compizconfig-settings-manager and it said it was the correct version. I looked in symmantic and the only thing that was there was simple-cssm, I installed that, and nothing changed.

---

### Post by nerdy_kid on 2011-07-08
sorry about that -- just run

```

sudo apt-get install compiz

```

(post the output if you are worried about a broken system)
and follow the rest of my guide.

---

### Post by venom104 on 2011-07-09
> **nerdy_kid said:**
> sorry about that -- just run

```

sudo apt-get install compiz

```(post the output if you are worried about a broken system)
and follow the rest of my guide.

Here is the output, I'm starting to get a bit scared by the terminal output...I'd rather not break my system, I think I'll probably just leave everything the way it is, if resolving the dependencies is dangerous.


```

venom@secmorg:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-core (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2) but 1:0.8.4-0ubuntu15.3 is to be installed
          Depends: compiz-plugins (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2) but 1:0.8.4-0ubuntu15.3 is to be installed
          Depends: compiz-plugins-main (>= 0.9) but it is not going to be installed
          Depends: libcompizconfig0 (>= 0.9) but 0.8.4-0ubuntu2 is to be installed
E: Broken packages


```

---

### Post by CatKiller on 2011-07-10
> **venom104 said:**
> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been **moved out of Incoming**.

That doesn't look right. Can you post your sources.list? It looks to me like you've got some other repositories in there that you shouldn't.

---

### Post by Psyco430404 on 2011-07-10
Just use wmctrl, it allows you to manipulate your windows in the way your wanting to do and it doesn't require any unstable upgrades, or the risk of breaking you system.

[http://galigio.org/2011/04/11/enable-windows-7-aero-snap-in-ubuntu/](http://galigio.org/2011/04/11/enable-windows-7-aero-snap-in-ubuntu/)

that gives you everything you'll need and its ubuntu specific hope its what your wanting.

---

### Post by nerdy_kid on 2011-07-10
> **CatKiller said:**
> That doesn't look right. Can you post your sources.list? It looks to me like you've got some other repositories in there that you shouldn't.

read my howto to see what is wrong...

@OP

Alright, just reverse the changes to your sources.list and run sudo apt-get update.  It would probably be best to just upgrade the whole distro to natty anyway...

---

### Post by CatKiller on 2011-07-10
> **nerdy_kid said:**
> read my howto to see what is wrong...

If you mean your post, then that wouldn't explain it. Incoming is a Debian term. Ubuntu repositories don't use it. I suspect the OP has other random repositories listed that are causing dependency problems.

---

### Post by nerdy_kid on 2011-07-10
> **CatKiller said:**
> If you mean your post, then that wouldn't explain it. Incoming is a Debian term. Ubuntu repositories don't use it. I suspect the OP has other random repositories listed that are causing dependency problems.

no sorry -- I meant my big long how to thing here: [http://ubuntuforums.org/showpost.php?p=11026029&postcount=14](http://ubuntuforums.org/showpost.php?p=11026029&postcount=14)

Basically I had him use the natty repos just to upgrade his compiz with, it's something that isn't really supposed to be done, but I have tried it before (albeit with Maverick instead of Lucid).  I can't remember which repo (main, universe or multiverse) compiz+dependencys are in, which is probably why he is having trouble as I only had him change the main repo to natty.  I could find out, but it is probably best for him to just upgrade the whole system.

---

### Post by venom104 on 2011-07-13
> **Psyco430404 said:**
> Just use wmctrl, it allows you to manipulate your windows in the way your wanting to do and it doesn't require any unstable upgrades, or the risk of breaking you system.

[http://galigio.org/2011/04/11/enable-windows-7-aero-snap-in-ubuntu/](http://galigio.org/2011/04/11/enable-windows-7-aero-snap-in-ubuntu/)

that gives you everything you'll need and its ubuntu specific hope its what your wanting.

I followed the directions exactly, and it STILL doesn't work. Sorry for the late reply, I've been stuck on studying for  tests at school

Here is my sources list

EDIT: forgot to add, I changed the source deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted back to deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted.

# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by CatKiller on 2011-07-13
> **nerdy_kid said:**
>  I can't remember which repo (main, universe or multiverse) compiz+dependencys are in,

Grid is provided by *compiz-plugins-main*, which is in the main repository

>  I could find out, but it is probably best for him to just upgrade the whole system.

Probably.

> **venom104 said:**
> EDIT: forgot to add, I changed the source deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted back to deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted.

You need to do the main repository as well as the updates repository.

If you put big chunks of text output in Code tags it makes it easier to read.

---

