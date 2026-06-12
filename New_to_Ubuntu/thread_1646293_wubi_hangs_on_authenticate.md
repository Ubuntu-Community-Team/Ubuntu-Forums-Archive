---
title: "wubi hangs on authenticate"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by degarb on 2010-12-15
I don't think 10.10- wubi is that great.   First, any OS- out of box - needs to play mp3, ogg, wma, mp4, flash, wmv.  Not the case here in wubi...  Theme is drab.  Okay, I can get over that.  Hey my Kodak printer doesn't have a driver--the hottest selling printer of 2010.  Okay, I can probably research and rig up some driver, maybe.

Then the worst part, now, on update manager and software center, after I type a password, there is some authenticate dialog.  Every time, it locks up indefinitely (over an hour at least).   I can't get rid of dialog, logout won't work.  So, I must push the reset button on machine for 15 seconds for hard boot into a working, perky xp.  (I tried regular install several times, but won't install on external drive the way I need.)  If I can't install updates, no point in running Wubi.  How do I remove this authenticate need or freeze? I don't see this behavior on 9.10.

---

### Post by degarb on 2010-12-15
I know my login,  but it tells me I don't have privileges to modify my password.

I just spent hours installing wubi for 7th time. Is there a way to repair an install, so I can at least test changing my password to fix this hang.

---

### Post by bcbc on 2010-12-15
That authenticate box... click on the X at the top and it's gone. It's not a wubi issue. 

PS don't do hard shutdowns - if you feel the need, hold down Alt+SysRq and then press R-S-U-B one after the other.

Re. mp3s etc. there are reasons they're not included by default. I thought that it's supposed to ask you if you want it with Maverick, but probably this isn't enabled with Wubi. Just install it and you're done.

You shouldn't have a problem changing your password. Not sure why that'd be an issue. Describe what you're doing in more detail.

---

### Post by degarb on 2010-12-15
> **bcbc said:**
> That authenticate box... click on the X at the top and it's gone. It's not a wubi issue. 

I figured out some package need cutting edge update.  It did take me some googling to figure out that I could get past this by clicking the x.

> **bcbc said:**
> PS don't do hard shutdowns - if you feel the need, hold down Alt+SysRq and then press R-S-U-B one after the other.

What is the sysrq button?

Of course I will need to reinstall wubi install, unless I get a life line.  Next time, I will avoid the python updates.

---

### Post by bcbc on 2010-12-15
> **degarb said:**
> 
What is the sysrq button?

Of course I will need to reinstall wubi install, unless I get a life line.  Next time, I will avoid the python updates.


Unless you have a Mac, there should be a button with SysRq on it - mine has the Prnt Scrn on the same button. In any case, try to avoid hard shutdowns (CTRL+ALT+t, or CTRL+ALT+F1 to get to a terminal, then "sudo shutdown -h now") or CTRL+ALT+DEL - anything is preferable to hard shutdowns (with wubi especially).

PS you can change your password from a terminal prompt too: "passwd"

---

### Post by degarb on 2010-12-15
> **bcbc said:**
> Unless you have a Mac, there should be a button with SysRq on it - mine has the Prnt Scrn on the same button. In any case, try to avoid hard shutdowns (CTRL+ALT+t, or CTRL+ALT+F1 to get to a terminal, then "sudo shutdown -h now") or CTRL+ALT+DEL - anything is preferable to hard shutdowns (with wubi especially).

PS you can change your password from a terminal prompt too: "passwd"

No Mac here.  Gear head keyboard, no sysrq

Can I sustitute scroll lock?

---

### Post by bcbc on 2010-12-16
> **degarb said:**
> No Mac here.  Gear head keyboard, no sysrq

Can I sustitute scroll lock?

Try printscreen if you have it. I'm not sure if you can just map it to another key as it's a kernel level interrupt (but to be honest I don't know - never had to do this - when you figure it out let me know ;) )

---

### Post by degarb on 2010-12-16
I put the install cd in and rebooted.  I see install or try.  Of course it hangs after first install dialog, so I didn't have the patience for 25 minutes that twice it took to get past (Once I gave up after an hour..also tried several downloads, checksums and burns)

---

### Post by 3ruce on 2011-02-26
> **bcbc said:**
> That authenticate box... click on the X at the top and it's gone. It's not a wubi issue. 

Thank you, thank you, thank you :-)

---

