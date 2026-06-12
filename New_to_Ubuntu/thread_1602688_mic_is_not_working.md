---
title: "mic is not working"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by sallam on 2010-10-21
Greetings

I failed to make the mic work in my laptop, both the internal (built-in mic) and the external. I've run the system test, and they both failed. The report said:
>     alsa_record_playback_internal    FAILED    
    alsa_record_playback_external    FAILED

Any ideas how to fix this issue please?
The mic works properly under Win7..
It even worked under ubuntu a couple of weeks ago. But testing today, it stopped working..
I also tested it in gmail voice chat, not working.
And in sound recorder, nothing either..

---

### Post by sallam on 2010-10-21
That was easy to solve.
I've clicked the speaker icon > sound preferences > input
Somehow the mute had a tick next to it. I've un-ticked it and now all is well!
I hope this helps someone else having similar issue.

---

### Post by migs73 on 2010-10-21
If you mark the thread as solved (Thread Tools at the top of your first post) it'll help people filter for things that work.

---

### Post by sallam on 2010-10-22
Thanks for the tip. I just did that.
This is a great forum.

---

### Post by honeybear on 2010-10-22
> **sallam said:**
> That was easy to solve.
I've clicked the speaker icon > sound preferences > input
Somehow the mute had a tick next to it. I've un-ticked it and now all is well!
I hope this helps someone else having similar issue.

great it works

```
xterm -e alsamixer & echo "Press F6 in alsa" & printf "Enter 0, 1 or 2 or 3" ; read i ;  arecord -Dplughw:$i,0 -f cd -vv "mymicrecordfile.wav"
```
will let you record even !:guitar:

---

