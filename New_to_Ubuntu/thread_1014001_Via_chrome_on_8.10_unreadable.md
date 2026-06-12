---
title: "Via chrome on 8.10 unreadable"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ebeard on 2008-12-17
How do I get readable desktop back?

I decided to try 8.10 to see if it had functional wireless. I successfully installed (got rid of 7.04), but part of the desktop (like the network icon) was off the screen. Simple fix I thought, I'll drop the resolution. Now the screen is totally unreadable. It has something tiled (the icons)with lines through them, can't read anything.  

Is there any way to get back what was there before or go to vesa? 

I tried several pages and instructions for reconfiguring xorg, but can't get any change to stick (it goes through keyboard config and then goes back to command line, never gives a video option). The xorg.conf file has no settings in it to change (accessed by nano).  Apparently you can't go to vesa like you could in older versions.  

via p4m900 integrated
dual boot with winxp

---

### Post by jerome1232 on 2008-12-17
have you tried (At least I believe this was the command to revert to a default xorg.conf)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ebeard on 2008-12-17
Yep. Tried that command in terminal mode (after stopping desktop).

No help

I meant to list as P4M800 (not the 900)

---

### Post by ebeard on 2008-12-17
Fixed (I think) 

Used these two threads if anyone else runs across this. 

[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)

and 

[http://ubuntuforums.org/showthread.php?t=966318&highlight=p4m800](http://ubuntuforums.org/showthread.php?t=966318&highlight=p4m800)

---

