---
title: "how to output and remove current song in MPD"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by iconoclast hero on 2011-08-28
Since gmpc won't do this directly, I'm looking for an easy way to delete the current song from the current playlist.  On the MPD server, I do have mpc so basically it is a matter of running mpc to get the current song number and then mpc del <current song>

so the output from mpc is
```
Bob Dylan - Need A Woman
[playing] #670/8716   0:00/5:44 (0%)
volume:100%   repeat: on    random: on    single: off   consume: off

```
and I need to extract the characters between the # and the first /, 670 in this case.  Once I have that I need to feed that back into an mpc command, mpc del 670 to remove the current song.  I would like to have a short simple command for this.  I think it might be possible to do this from a client computer if I have it set up properly, but for now, doing it from the server computer works too.

---

