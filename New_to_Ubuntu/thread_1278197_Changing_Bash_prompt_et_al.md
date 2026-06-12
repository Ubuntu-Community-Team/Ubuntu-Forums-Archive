---
title: "Changing Bash prompt et al"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by nnjond on 2009-09-29
Hi,

My prompt is x@x-desktop:~$, but I think there would be greater clarity if it was:

x@y-desktop:~$

Perhaps it would be altogether simpler if i could change the name of my pc. 
Does anyone forsee any hazards in either of these  changes? How do i do it?

thanks

---

### Post by m3wolf on 2009-09-29
Shouldn't be a problem to change your hostname unless your computer is acting as a server for something. 

To permanently change your hostname simply edit /etc/hostname to reflect the name you want:
```
# echo *newhostname* > /etc/hostname
``` This change will become active on next reboot. You can also run
```
# hostname *newhostname*
```and it will be active immediately until next reboot.

---

### Post by star3am on 2009-09-29
Sorry, I re-read the question, hostname would be the way to go, I'm leaving my reply just for whatever's sake :)

Try this, edit, ~/.bashrc 

look for these parts, mine looks like, 

```
force_color_prompt=yes
```

my promt is also gentoo style with colors, but not exactly like gentoo, but here you go, still in, ~/.bashrc

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

```

All the best, 
ciao/Riaan:popcorn:

---

