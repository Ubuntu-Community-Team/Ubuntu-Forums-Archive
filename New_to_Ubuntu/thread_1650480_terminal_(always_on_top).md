---
title: "terminal (always on top)"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by Johnny420 on 2010-12-21
I am a NooB and I have been using the terminal for a lot of stuff and its always getting lost behind other stuff (firefox). I know that I can right click the header and click always on top but I don't want to if I don't have to. So is there a way to set up certain Apps to always open with the always on top option clicked
                                                             THANX
                                                                      Johnny420

---

### Post by Verbeck on 2010-12-21
if you've enabled desktop effect, install the compiz config settings manager
```
sudo apt-get install compizconfig-settings-manager
```after that, open it from system>preferences>CompizConfig Settings Manager and enable the plugin, 'window rules'. then open the plugin preferences and add stuff in the 'Above' field eg, class=Firefox
for multiple windows, use a | to separate them
eg, class=Firefox | class=Nautilus

---

### Post by Johnny420 on 2010-12-21
thanx for the help and your advice was good.....My problem is that I want my Terminal to always be on top. I tried class=Terminal and I tried class=GNOME Terminal that didn't work

---

### Post by Johnny420 on 2010-12-21
it took a few tries but I got it!!!
class=Gnome-terminal
DUH!!!!! Thanx again

---

### Post by Verbeck on 2010-12-21
use Gnome-terminal

edit: looks like you got there first

---

### Post by stormeruk on 2011-09-05
Hi,

Many thanks for the info, managed to get it to work OK, keeping the terminal window on top of the firefox window, only problem is when I make the firefox window fullscreen (F11) then I lose the terminal window and FF is now top, anyway to stop FF from completely taking over when in fullscreen mode ?

Thanks in advance

---

### Post by neiljansons on 2012-02-01
I have a problem that my terminal always appears on top even when it is not active.
How can I stop it from being on top?
(BTW right-click the top frame and "only on this workspace" is selected.)

---

### Post by Paqman on 2012-02-01
You could try using an alternative terminal like [guake]("apt:guake"). When invoked it slides down from the top of the screen and is always on top.

---

### Post by neiljansons on 2012-02-01
thanks @paqman
guake looks like it will solve my immediate problems

it would appear that my problem is listed as a bug with no apparent answer
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/869802](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/869802)

---

