---
title: "SSH help"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Guffmeister on 2010-06-11
Hi! I'm running Ubuntu on both my work computer and home computer, and I'm trying to connect to my work computer to track the progress of some simulations I'm running.

I'm connected up to the VPN from home, and SSHed through to my computer at work. I can see all my files, and see all my running processes just fine. However, I'd like to literally forward the visual output of an already running program to my computer here so that I can see what it's doing, and I don't know how to do that.

Previously I had Windows XP at work, and I could rdesktop to it and get a full image of my desktop, which was pretty useful, and I'm guessing if it's possible with Windows it must be possible with Linux somehow. 

It would be possible to have my script output a text file periodically so that I could at least open that, but ideally I'd just like to see the program itself to get a full picture of what's going on.

Thanks in advance for your help.

---

### Post by KdotJ on 2010-06-11
Have you tried tunnelling the X server? 
For example to test, ssh into your machine as normal but add -X

```
ssh -X user@host
```

Then test it with something... let's say gedit

```
gedit
```

Now, hopefully gedit should open on the remote machine but the interface for it should open on your machine

---

### Post by Guffmeister on 2010-06-11
Hi! Thanks for your reply.

Yes, that's what I do now and it works fine, but it opens up a new program. What I want to do is to forward an existing program which is running now, so that I can see what happening on my screen at home.

---

### Post by BoneKracker on 2010-06-11
freenx is pretty awesome too (it minimizes latency that can be a problem over some internet connections)
[http://freenx.berlios.de/info.php](http://freenx.berlios.de/info.php)

---

### Post by KdotJ on 2010-06-11
> **Guffmeister said:**
> Hi! Thanks for your reply.

Yes, that's what I do now and it works fine, but it opens up a new program. What I want to do is to forward an existing program which is running now, so that I can see what happening on my screen at home.

Unfortunately this is where my knowledge of SSH runs out lol...
There must be a way of opening the GUI of a running process and someone here must know.

Sorry I can't help you further, but atleast this will bump your thread.

---

### Post by bodhi.zazen on 2010-06-11
> **Guffmeister said:**
> Hi! Thanks for your reply.

Yes, that's what I do now and it works fine, but it opens up a new program. What I want to do is to forward an existing program which is running now, so that I can see what happening on my screen at home.

You can not do that with ssh.

The closest you can come is via a shared screen session which you can connect to via ssh. From there you can run any command line editor.

To share graphical apps I think you need VNC (FreeNX would be one option).

---

