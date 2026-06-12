---
title: "No Sound in TuxGuitar"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Papenco on 2008-12-31
This used to work in Windows. Is there anything I can do?
Thanks

---

### Post by MyR on 2008-12-31
> **Papenco said:**
> This used to work in Windows. Is there anything I can do?
Thanks

What if you close all other applications, then close and reopen tuxguitar? does it have sound then?  I notice that it doesn't like to share with other apps.

peace

---

### Post by bryncoles on 2008-12-31
i suspect i know the problem.... look here:

[http://ubuntuforums.org/showthread.php?t=1001563](http://ubuntuforums.org/showthread.php?t=1001563)

and try what i suggest in the second post!

if thats not the solution, then please give more details about the tuxguitar sound issue you're having, and possibly even start tuxguitar from the terminal and see if it kicks out any error message you can post. 

more detail = better help = faster solution = happy days!

---

### Post by Papenco on 2008-12-31
Okey, first of all, thanks. I've tried what you said and none of them worked. The terminal doesn't give any errors because in fact that there's not an error, it just doesn't sound. Maybe I have to activate Midi sound or something like that.
Thanks again.

---

### Post by MyR on 2008-12-31
you did install java, correct? it is necessary for tuxguitar to play sound. it should automatically install as a dependency, but you never know.

peace

---

### Post by Papenco on 2008-12-31
Well, I already had Java when I posted this. But I installed Timidity as Bryncoles said. Though it works, there are still some instruments that doesn't sound, I've tried all ports.
Thanks

---

### Post by bryncoles on 2009-01-02
bum! thats me out of ideas then...

perhaps you need an alternative midi emulator from timidity....?

---

### Post by Jota37 on 2009-01-13
> **bryncoles said:**
> i suspect i know the problem.... look here:

[http://ubuntuforums.org/showthread.php?t=1001563](http://ubuntuforums.org/showthread.php?t=1001563)



I posted a reply to that with what solved the problem for me (installing the tuxguitar-jsa plugin and disabling the ALSA and OSS plugins in tuxplayer)

Good luck! :-)

---

