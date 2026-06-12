---
title: "keyboard problem on login only"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by donloveslinux on 2011-07-29
In June, I couldn't login so I reloaded 11.04.  Weeks later - same thing.  On forum, I learned to hold each key for one second logging in.  I tried Assistive Technology (under System > Personal) and adjusting keyboard speed but it has no effect.  I'm desperate enough to log in using a runlevel with text and then running X, but not sure how.  Swapped keyboards, no change.  Help!

---

### Post by donloveslinux on 2011-07-29
I also updated BIOS to latest version.  I have another pc running 11.04 that doesn't have this keyboard issue.  Anyone with ideas?  Thanks.

---

### Post by guilleme on 2011-07-29
Hi. This doesn't solve the problem, but makes the xserver program run only when you tell it to: 
[http://ubuntuforums.org/showthread.php?t=388344](http://ubuntuforums.org/showthread.php?t=388344)
Now, what happens when you try to log in? 
Do your keystrokes appear when you write your password, or the thing just sits there and does nothing?

---

### Post by donloveslinux on 2011-07-29
I don't see System > Administration > Services. Upper, right icon gets System Settings, but I don't see Admin, or things that get Services.
sudo sysv-rc-conf opens a old-style gui with gdm at left and 1, 2, 3, 4, 5, 0, 6, and S across top.  Space-bar toggles X in a column.  Should I put X in every col next to gdm?  Thanks.

---

### Post by donloveslinux on 2011-07-29
Using sysv-rc-conf, I put X under S, rebooted with no effect, then put X under every run level (beside gdm), rebooted and it started the gui (ie no terminal, same slow key hit needed).

---

### Post by guilleme on 2011-07-29
Sorry, I think those instructions are for an old version (7.*). I couldn't use them either... Me sorry...

---

### Post by donloveslinux on 2011-07-30
Anyone else know how to force 11.04 into a non-gui login?  As root, I created /etc/inittab and put id:1:initdefault: rebooted, and it printed text messages and hung.  In Recovery mode, I deleted inittab and now the gui with slow reader is back.  Any ideas how to fix keyboard problem or do text login? Why does mouse work great but not keyboard on gui login?

---

### Post by scorchgeek on 2011-07-30
Try this thread:
[http://ubuntuforums.org/showthread.php?t=1564671](http://ubuntuforums.org/showthread.php?t=1564671)

---

### Post by donloveslinux on 2011-07-30
Changed "quiet splash" to "single", ran sudo update-grub, rebooted and got terminal login.  Logged in.  Ran startx and got colored background without any menus, nothing to click on at all.  Using LIVE CD, tediously changed back to "quiet splash" and got back to slow key login.  Anyone know why menues are gone using terminal login?

---

