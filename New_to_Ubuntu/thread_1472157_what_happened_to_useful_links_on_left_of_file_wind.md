---
title: "what happened to useful links on left of file window"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by ave2 on 2010-05-04
one of the features I used all the time was the short cuts on the left of nautilus file manager- in 10.04 its mostly still there, but all the useful links have been removed- ie cd rom, hard drives, any flash drives. 

now if I want to access my cd, hard drive etc I have to go to places> computer. same to eject flash drive

is there something wrong, or have these been taken out in the latest release?

---

### Post by jvc26 on 2010-05-04
Its still there in mine, in the panel on the left there is a dropdown selection box at the top, mine reads 'Places' what does yours - it may have been switched to a different mode.

J

---

### Post by lotharmat on 2010-05-04
Press F9 - This will bring back the places menu

---

### Post by ranch hand on 2010-05-04
I have no idea why you do not have those things in your nautilus display.

I have several installations of 10.04, one of which goes back to the first Thursday in November when th tool chain went up for 10.04-testing, they all, including the clean install from the Final Release testing ISO, display everything that is running on my box.

I would check your configuration including the gconf-editor under apps>nautilus.

Nautilus seems to work better than it has in past releases for me.

---

### Post by ave2 on 2010-05-04
yeah mine also in set to places- 
it shows- user, desktop, file system, network, floppy0, trash

(except I dont have a floppy drive)

it doesn't show other partitions, cd rom, or any flash drives


> **ranch hand said:**
> 

I would check your configuration including the gconf-editor under apps>nautilus.


I looked through the gconf-editor but couldn't find anything that seems relevant- what should I be looking for?

---

### Post by ranch hand on 2010-05-04
Places is where you want it set.  Should work.

If you can not get it to work after checing you configuration, file a bug;
```

ubuntu-bug nautilus

```
will collect the needed information and transmit it to Launchpad.  You do need an account there, easy to set up when you file the bug.

For more info read this from the stickies for this forum;

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

