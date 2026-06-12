---
title: "language switcher in Lubuntu"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by al.adab on 2010-10-10
I'm forced to run

*setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar*

every time I need to switch to writing in Arabic. After entering this command, I can use the language switcher in the taskbar (I'm in LUBUNTU). 

If I re-boot, the language switcher no longer works - the alternative would be to hit ALT+SHIFT, but that's gone too. 

Is there any way I can fix this? For some reason, in Lubuntu the Preferences>Keyboard options are very limited.

---

### Post by TeoBigusGeekus on 2010-10-10
Well, put the
```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar
```
command in your autostart script.

---

### Post by al.adab on 2010-10-10
er...how do I do that? :)

---

### Post by TeoBigusGeekus on 2010-10-10
```
~/.config/openbox/autostart.sh
```

---

### Post by al.adab on 2010-10-10
afraid, it didn't work

(in Lubuntu) if I type *sudo leafpad ~/.config/openbox/autostart.sh*

I get an empty file...

any idea?

---

### Post by TeoBigusGeekus on 2010-10-10
Obviously it didn't exist.
Put
```
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar
```
in it, save and exit.
Log out, log in and see if it works.

---

### Post by al.adab on 2010-10-10
I did insert 

*setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar*

in the empty *~/.config/openbox/autostart.sh*
plus logged out + back in again, and it didn't work.

---

### Post by TeoBigusGeekus on 2010-10-10
Oh God, just found out by googling that lubuntu doesn't use the standard openbox startup conventions.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1518818]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1518818")

---

### Post by mikewhatever on 2010-10-10
Here is an interesting solution for Lubuntu.
[http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html](http://foo-gr.blogspot.com/2010/04/keyboard-layout-configuration-for.html)

---

### Post by al.adab on 2010-10-10
it's a great solution! :) 
thanks!!!

---

### Post by lianazaman on 2011-11-03
Hi, I tried your solution for my Lubuntu 11.10, but still can't. It says directory not available.

---

### Post by amjjawad on 2011-11-04
> **lianazaman said:**
> Hi, I tried your solution for my Lubuntu 11.10, but still can't. It says directory not available.

It's an old thread ;)

Have you tired what I posted for you previously?

> Hi,

as I got a lot of requests to implement an autostart feature for
lxkeymap I did it.
LXKeymap 0.5 is now capable to store its keymap configuration into a
file that it reads out during autostart.
Therefore I wrote a little *.desktop file that I put in the global
/etc/xdg/autostart which contains the new command "lxkeymap -a" to
trigger the autostart function of lxkeymap. The Keymap configuration
will be stored locally in your home directory ( ~/.config/lxkeymap.cfg)
and is easily editable either by using lxkeymap and set a new keymap or
by editing it by hand.
You can get this version from here:
[http://content.wuala.com/contents/leszek/Dokumente/Share/lxkeymap_0.5-0ubuntu1_all.deb?dl=1](http://content.wuala.com/contents/leszek/Dokumente/Share/lxkeymap_0.5-0ubuntu1_all.deb?dl=1)

If you notice any bugs then report them here: [http://launchpad.net/lxkeymap](http://launchpad.net/lxkeymap)

Also I guess there is a bug in lxdm, because changing the keyboard
layout in the session and logging out to lxdm does not restore the
global keymap but uses the one choosen in the session.
This could be also fixed by simply calling "lxkeymap -a" from within
lxdm but as lxkeymap uses only a local configuration it would then
create and use the root accounts .config/lxkeymap.cfg file. So you need
to create this first by executing lxkeymap as root if you want to have a
different keymap globally+lxdm and your user accounts.

By the way, the above quoted message is not from me, it's by one of Lubuntu's Dev.

---

