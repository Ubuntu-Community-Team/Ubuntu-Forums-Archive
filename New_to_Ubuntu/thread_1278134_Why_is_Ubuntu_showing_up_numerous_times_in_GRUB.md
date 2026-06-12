---
title: "Why is Ubuntu showing up numerous times in GRUB?"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by random turnip on 2009-09-29
What's going on here?
I turn on my computer and it loads GRUB automatically, but in the list there are like 4 versions of Ubuntu that are all exactly the same.  When i first installed there was only 1, then after a while there was 2, then a few days later 3 and now 4 with Vista sitting at the bottom.

How do i stop this happening and get rid of the 3 duplicates?

---

### Post by goodvikings on 2009-09-29
Usually there's a few different ones to start with, rather than gradually getting more, at least, that's my experience.

If I'm not mistaken, they refer to different kernel's?

---

### Post by djyoung4 on 2009-09-29
try that
[http://http://ubuntuforums.org/showthread.php?t=1170142]("http://http://ubuntuforums.org/showthread.php?t=1170142")

---

### Post by random turnip on 2009-09-29
I don't know, they're all the same.
I noticed once it happened when my laptop ran out of battery (forgot to switch plug on, lol) so it could be something to do with errors, but i'm not 100% sure as i don't remember it crashing that many times.

They are definitely duplicates and not loads of different ones.


[edit]
djyoung4 posted while i was posting.

Thank you, i think that's the problem now i think about it, this post in particular seemed like it could work:
> **raymondhenson said:**
> Hello,

as a follow to this ... you can install startupmanager (thru synaptic or terminal)...it'll give you the option to choose a default boot as well as hide the kernels (not erase them)

in terminal

sudo apt-get install startupmanager

Once installed, you'll find it in system > administration

Here's the official link

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Regards,

Thanks :)
I'll say if it works or not when i've had chance to try it out.

---

### Post by JohnLM_the_Ghost on 2009-09-29
> **random turnip said:**
> What's going on here?
I turn on my computer and it loads GRUB automatically, but in the list there are like 4 versions of Ubuntu that are all exactly the same.  When i first installed there was only 1, then after a while there was 2, then a few days later 3 and now 4 with Vista sitting at the bottom.

How do i stop this happening and get rid of the 3 duplicates?

By default there should be 3.
- Usual one
- Recovery (sort of safe mode)
- Memtest (which is not Ubuntu really :) )

and then you got usually two more per newly installed kernels.

To get rid of additional ones you simply need to uninstall old kernels.
They are not removed automatically because it provides you a way to boot into old kernel if new one doesn't work for you. (Believe me, it happens)

Anyway post contents of your /boot/grub/menu.lst so we actually see what's in there.

---

### Post by random turnip on 2009-09-29
I won't be uninstalling them then, lol.
I'll probably hide all but 2, just in case it won't boot at all (happened in 8.10 to me).
Thanks again.

---

### Post by slakkie on 2009-09-29
If you know the new kernel is working you can safely remove them:

```

sudo aptitude purge $(dpkg -l | egrep "linux-(image|headers)" | egrep -v  "$(uname -r | sed -e 's/-generic//' -e 's/-server//' -e 's/-virtual//')|linux-(image|headers)-(generic|server|virtual)" | awk '{print $2}')

```

This bit of code will remove all kernels, except for the running kernel..

---

### Post by egalvan on 2009-09-29
I add my vote for StartUp-Manager.

It will let you choose how many kernels to keep,
among other boot-time options.

The recommended is two...
the current one, and the previous one.
This allows you to boot with the known-good previous,
in the rare instance that a kernel up-grade goes bad.

The un-needed kernels can then be removed with a simple

```
sudo apt-get autoremove
```

You can also remove the "memory test" option, and the "recovery mode" option, to further reduce the menu "clutter",
and turn on "pretty-colors" to make it look nicer.

Note that all the options in StartUp-Manager can be edited by hand...
using the command line to edit different files, such as menu.lst.
StartUp-Manager is simply a GUI-way to safely change these items.

And if you don't have it installed,
Synaptic is the easy GUI-way to install software,
and it gives you a lot of information.

---

### Post by wojox on 2009-09-29
I like slakkies way but he left a few out:

[php]#!/bin/bash
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
sudo apt-get purge $OLDKERNELS[/php]

---

### Post by random turnip on 2009-09-29
> **egalvan said:**
> I add my vote for StartUp-Manager.

It will let you choose how many kernels to keep,
among other boot-time options.

The recommended is two...
the current one, and the previous one.
This allows you to boot with the known-good previous,
in the rare instance that a kernel up-grade goes bad.

The un-needed kernels can then be removed with a simple

```
sudo apt-get autoremove
```

You can also remove the "memory test" option, and the "recovery mode" option, to further reduce the menu "clutter",
and turn on "pretty-colors" to make it look nicer.

Note that all the options in StartUp-Manager can be edited by hand...
using the command line to edit different files, such as menu.lst.
StartUp-Manager is **simply** a **GUI**-way to **safe**ly change these items.

And if you don't have it installed,
Synaptic is the easy GUI-way to install software,
and it gives you a lot of information.

"simple", "GUI" and "safe" are 3 things i like to see in suggestions, lol.
I'll instal it and give it a try.

---

### Post by slakkie on 2009-09-29
> **wojox said:**
> I like slakkies way but he left a few out:

[php]#!/bin/bash
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
sudo apt-get purge $OLDKERNELS[/php]



Thnx, I made the modifications, seems you missed one as well ;)

```

rmkernel() {
    local cur_kernel=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
    local kernel_pkg="linux-(image|headers|ubuntu-modules|restricted-modules)"
    local meta_pkg="${kernel_pkg}-(generic|i386|server|common|rt|xen|ec2)"
    sudo aptitude purge $(dpkg -l | egrep $kernel_pkg | egrep -v "${cur_kernel}|${meta_pkg}" | awk '{print $2}')
}

```

You can put this in your .bashrc and then you will always have it. I need to check if this is compatible with 8.04.x btw.

---

