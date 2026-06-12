---
title: "[SOLVED] Help!  Compiz killed my account! Purple screen of death!"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by lariosa42 on 2008-12-09
I was playing around with compiz today, and under System-->Preferences-->Apperence-->Visual Effects-->Preferences-->Accesibilty, I clicked "area zoom" just to see what it would do.  Boy did I find out!  My whole screen suddenly went purple (it looked like a field of repeating ASCII symbols on a black background).  After waiting a minute or so, it brought me back to the login screen.  If I started up in any mode besides "safe terminal" (or whatever it is called), I got the same purple screen of death (PSOD) and got sent back to the login screen.

I tried logging into a "test" account I had set up (with full permissions) earlier, and had no problems.  Hoping to fix the problem on my main account, I went into synaptic and did a full remove on everything containing the word "compiz."  When I logged out, the PSOD flashed up again, but then I was able to log into my main account with no PSOD.  I re-installed compiz, restarted, and logged back in to my account.  But then: PSOD! I went BACK to my test account and deleted everything in the main account's ~/.config/compiz and ~/.compiz directories, but this did not solve the problem.

Can anyone help?  I'm desperate here!

---

### Post by gettinoriginal on 2008-12-09
Acessability seems to be your problem.  If you have CCSM installed and can acess it, then uncheck all options in that field.

---

### Post by lariosa42 on 2008-12-09
OK, I did another full remove of Compiz, but this time I rebooted afterwards.  I logged in to my main account and reinstalled compiz and the CCSM.  Then, I disabled any "zoom" features in CCSM under "accesibilty."  Hopefully this will work, but now I am afraid to reboot.  I don't want to have to do this all over again, especially as I'm not sure why this happened in the first place.  Could anyone lend a hand in helping me understand this?

BTW, I forgot to provide my setup in the last post:

Processor:  Intel Core 2 Duo 1.83 GHz
Video Card: Intel 945GM/GMS/GME, 943/940GML Express
            (I've heard it is a weak video card)
OS:         Ubuntu Intrepid 8.10

---

### Post by gettinoriginal on 2008-12-09
I really have no idea what happened, but I would not be afraid to reboot.  After all, the nice thing about running linux is being able to fix it.  LOL

Good Luck :p   If you consider this problem solved, please go to tools and mark it as solved.

---

### Post by lariosa42 on 2008-12-09
Thanks for the reminder about the "solved" tool (I have negleted this before).  I will wait until I reboot (I have to do this in a few hours) and then mark it solved if things seem fixed.  Either way, it would be nice to know what happened.  Until then,  I'll be afraid to play with compiz at all.

---

### Post by gettinoriginal on 2008-12-10
I will stay subscribed to this thread until you mark it solved :p

---

### Post by lariosa42 on 2008-12-10
OK, I figured it out.  After I got back into my account (see above), I opened ccsm and found a "reset to defaults"  button (after some searching).  To do this:

System-->Preferences-->CompizConfig Settings Manager

Then click "Preferences" and then "Reset to defaults."

It would be nice to know a command-line way to do this so that it could be done by booting into the command-line only interface.  This works for now though.

Thanks for your help!

---

### Post by gettinoriginal on 2008-12-10
Alt F2 > command > gconftool-2 –recursive-unset /apps/compiz 

This will reset defaults in compiz

Glad it's working though. :p

---

### Post by lariosa42 on 2008-12-11
Thanks for this.  I had actually already seen this on other forums, but it doesn't seem to work due to the lack of an /apps directory in ubuntu.  There are a few files named compiz, stored for example at:
/etc/compizconfig/compiz
or
/usr/bin/compiz
and maybe others.  Hopefully this helps someone.

EDIT:
I just typed 
```

whereis compiz

```
into the terminal and found some more places where files called "compiz" are stored.  Since my system might be different then yours, I won't post mine here.  If you find this post and want to reset your compiz defaults from the command line, try using
```

gconftool-2 &#8211;recursive-unset whereever_compiz_is_on_your_system

```
where "whereever_compiz_is_on_your_system" might be "/apps/compiz" as mentioned above, or maybe "/usr/bin/compiz," or something else that comes up when you type in "whereis compiz".  NOTE: I haven't tried this myself (now that it's working, I don't want to mess things up), so use at your own risk.

---

