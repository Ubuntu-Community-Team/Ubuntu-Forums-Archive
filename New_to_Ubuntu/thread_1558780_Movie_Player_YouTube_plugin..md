---
title: "Movie Player YouTube plugin."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by LinuxFox on 2010-08-22
I have a question about this feature.  I notice on the Ubuntu [Tour page]("http://www.ubuntu.com/desktop/features"), they show Totem Movie Player playing a Shrek trailer via YouTube.  I notice whenever I try it out, it doesn't work.

I know I might need some sort of plug in, but if it doesn't work out of the box, why does Ubuntu promote the feature?  I'd just like an answer please.

---

### Post by howefield on 2010-08-22
Have you got flash installed ?

---

### Post by davidmohammed on 2010-08-22
Suggest install ubuntu-restricted-extras (from synaptic or software centre).  Should make totem behave better.

---

### Post by LinuxFox on 2010-08-22
> **howefield said:**
> Have you got flash installed ?I do and it works in the browser, I'm talking about a feature in Totem.

davidmohammad, Thanks for the advice, I would, but that message about legal info kind of scares me.  I just wanted to know if it's a feature, why doesn't it work out of the box.

---

### Post by davidmohammed on 2010-08-22
... dont worry about that legal stuff - unless you live in america...

---

### Post by LinuxFox on 2010-08-22
> **davidmohammed said:**
> ... dont worry about that legal stuff - unless you live in america...Actually, I do, that's kind of the reason why I worry.  I just wanted to know about the feature that's all.  It's kind of a begginer's question for me since it seems new to me.  I don't remember it in Ubuntu 8.04.

---

### Post by davidmohammed on 2010-08-22
... I would surmise that whoever wrote that part of the install didnt live in america...

Remember the choice of whether to install or not is yours.  Is the government really monitoring your internet usage..?!

---

### Post by howefield on 2010-08-22
> **LinuxFox said:**
> I'm talking about a feature in Totem.

The plugin should be enabled by default in Totem.

Have a browse here....

[http://www.cyberciti.biz/tips/linux-watch-youtube-movie-bbc-content.html](http://www.cyberciti.biz/tips/linux-watch-youtube-movie-bbc-content.html)

---

### Post by bergfly on 2010-08-22
Here is the interesting thing. If you load a video in youtube, and the open your file browser, click on file system on the right and then look in the /tmp directory , then as long as your browser is trying to play the video, you will have a tmp file starting with the letter F, that is the video.

As long as the browser window is open, you can load the file and totem should play it. close the window/tab in your browser, and the file is gone. copy the file somewhere else and..............


Works with almost all flash video sites, not just youtube. Don't know if that answered your questions, but certainly is a bit of knowledge I have found very useful

---

