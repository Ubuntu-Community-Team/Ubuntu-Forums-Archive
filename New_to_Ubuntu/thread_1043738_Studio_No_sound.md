---
title: "Studio No sound"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by trucker33377 on 2009-01-18
I think I have to get to my master surround sound to turn it up on hardy all i did was go to the icon Studio has no icon.
I know this can be found by using the term, just not real sure how.

trucker@ubuntu:~$ alsa
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
trucker@ubuntu:~$ alsa config
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
trucker@ubuntu:~$ 
I see it in the gui how do you adjust it there?
HDA Intel (Alsa mixer)

---

### Post by llamakc on 2009-01-18
Run (from a Terminal) `alsamixer` without the backticks. Like this:

```

alsamixer

```

---

### Post by trucker33377 on 2009-01-19
thanks got it

---

