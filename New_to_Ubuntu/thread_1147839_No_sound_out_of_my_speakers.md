---
title: "No sound out of my speakers"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Lil Jimmy on 2009-05-03
I haven't had this problem since I normally use my USB headset, but I have a set of speakers and I don't know how to make sound come out of them. How would I do that?

Also, I'd like to know how to easily switch between speakers and headset.

Thanks!

---

### Post by mahimahi42 on 2009-05-03
Are your speakers plugged into the back of your tower? That might be your problem.

---

### Post by ubudog on 2009-05-03
Is your PCM turned up?

---

### Post by qjmoss on 2009-05-03
Go to the top pannel, right click on your volume control, open volume control.

Turn your PCM all the way up.

This should fix your problem..

Maybe

---

### Post by Lil Jimmy on 2009-05-03
Pcm? :3

---

### Post by mahimahi42 on 2009-05-03
Your master volume =)

---

### Post by Lil Jimmy on 2009-05-03
They're at the max. nothing.

---

### Post by ubudog on 2009-05-03
What is your sound input (in master volume control.)

---

### Post by fooman on 2009-05-03
try installing the gnome-alsamixer....it has more options then the default alsamixer.

you can find it in synaptic (system > administration > synaptic package manager....search for gnome-alsamixer)  or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```after it installs,  find it in applications > sound & video > gnome alsamixer

open it see that all the sliders are unmuted and turned up all the way.

hope that helps.

---

