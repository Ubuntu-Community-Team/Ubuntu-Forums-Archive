---
title: "unable to play video using VLC"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by koyakishore on 2009-06-25
hi friends..

i'm unable to play videos using VLC player..

dis problem started rite from today..
previously it worked well..

help me out of diss...:)

---

### Post by Divider on 2009-06-25
Make sure your playback option is set to X11 and your choosing VLC to open as the default program. If it still doesn't work try:

```
sudo apt-get autoremove vlc
```

let it finish and:

```
sudo apt-get install vlc
```

---

### Post by koyakishore on 2009-06-25
actually...
i'm not getting enuf time to make those changes..

i mean.. the moment i open a video file..
VLC player is opening..and gettin clossed in few seconds..

will try those commands and get back to you..
thanks for ur reply..:)

---

### Post by koyakishore on 2009-06-25
in the terminal..

when i entered command to remove vlc..

it got displayed as..

After this operation, 93.1MB disk space will be freed.
Do you want to continue [Y/n]? 

is that ok..??

---

### Post by waspbr on 2009-06-25
yep

---

