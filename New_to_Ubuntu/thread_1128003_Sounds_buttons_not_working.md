---
title: "Sounds buttons not working"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by Pollox on 2009-04-17
The sound buttons on my Thinkpad T60 are not working since I upgraded from Intrepid to Jaunty (they were working before).  When I go to "Keyboard Shortcuts", it does not even register that I am pressing the sound buttons when I try to assign them to something.  How can I fix this?

---

### Post by kpkeerthi on 2009-04-17
Can you post of output of
```
xev -pke
```?

---

### Post by Pollox on 2009-04-17
> **kpkeerthi said:**
> Can you post of output of
```
xev -pke
```?

usage:  xev [-options ...]
where options include:
    -display displayname                X server to contact
    -geometry geom                      size and location of window
    -bw pixels                          border width in pixels
    -bs {NotUseful,WhenMapped,Always}   backingstore attribute
    -id windowid                        use existing window
    -s                                  set save-unders attribute
    -name string                        window name
    -rv                                 reverse video

It doesn't seem to like that argument.

---

### Post by kpkeerthi on 2009-04-17
Sorry. That ought to be ```
xmodmap -pke
```

---

### Post by Pollox on 2009-04-17
Here's the output of that command.

---

### Post by Pollox on 2009-04-21
(bump)  Anyone have any ideas?  Some package/driver I can try reinstalling?

---

### Post by muteXe on 2009-04-21
Jaunty isn't released yet. Why post here?

---

### Post by Pollox on 2009-04-22
> **muteXe said:**
> Jaunty isn't released yet. Why post here?

Because I'm using Jaunty, and I need help with a problem I'm having.  Why wouldn't I post to ask for help?  The beta is out, and a number of people are using it who might be able to help.  When in doubt, Beginner Talk seems like a good place to post.  If you have a suggestion of a better spot to post/move the post, that's fine, but I'm not going to not ask the question just because it's in beta.

---

### Post by Pollox on 2009-04-23
I've found that these keys produce no output in xev.  But they used to work in Intrepid.  Is this a bug in some piece of software?

---

