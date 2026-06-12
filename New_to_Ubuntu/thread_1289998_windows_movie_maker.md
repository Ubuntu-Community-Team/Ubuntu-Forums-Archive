---
title: "windows movie maker"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by misswham on 2009-10-13
Hello all.  Which software in linux is comparable to windows movie maker with the timelines, transitions, storyboards, and effects?

---

### Post by Perfect Storm on 2009-10-13
Give **kdenlive** a try.

```
sudo apt-get install kdenlive
```

---

### Post by kellemes on 2009-10-13
Indeed.. kdenlive.
I recommend the latest release (0.7.6), [more info]("http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages")..

---

### Post by misswham on 2009-10-13
Thank you but I have Hardy and I click the link to ubuntu and then hardy 8.04 and the site said not to use because it is too old.  What do u all think?

---

### Post by Perfect Storm on 2009-10-13
Perhaps make a move to a newer release of ubuntu?
9.10 will be out the 31th October.

---

### Post by Cope57 on 2009-10-13
Cinelerra is a complete audio and video authoring tool. It understands a lot of multimedia formats (quicktime, avi, ogg) and audio/video compression codecs (divx, xvid, mpeg1/2, ...)

---

### Post by vinutux on 2009-10-13
Try openshot.........

---

### Post by Marlonsm on 2009-10-13
Always you need a program in Ubuntu, go to Applications > Add/Remove.

You'll find quite some video editors, the one that I liked the best is Kdenlive.

---

### Post by kellemes on 2009-10-14
> **misswham said:**
> Thank you but I have Hardy and I click the link to ubuntu and then hardy 8.04 and the site said not to use because it is too old.  What do u all think?

[Upgrade]("http://www.ubuntu.com/getubuntu/download")
You can also wait 2 weeks for Ubuntu's newest release to be out and available.

---

### Post by ArielEnter on 2009-12-09
Hi. A few days ago I was looking for a good replacement for that video creator included with windows. I wanted to create a photo presentation like I do it in that software.

I found Kdenlive, and I think is the best choice between all the other options I tried because of it similarities with Movie Make to establish the the default duration of Still Pictures.

In MM you go to tool>options and to the Advance Tab. Then you just change the value in Picture Duration. Very similar, in Kdenlive you go to Settings>Configure Kdenlive and you change the field that says: “Default duration, image clips”. You do the exact same thing for transitions in both programs.

You import pictures, videos and sound the same way you do it in MM.

Another great similarity between them is their time line. Kdenlive doesn't have a Story Board, but its time line looks very similar to MM´s.

Kdenlive doesn't have a Auto Movie yet, but I´m sure they are going to implement it soon. Until then you could use this script [http://www.kdenlive.org/forum/photo-slider-random-effects-script](http://www.kdenlive.org/forum/photo-slider-random-effects-script). It needs to be change a little by replacing “prm” with “prm.png” in the code to work with the current version (0.7.6), but it works.

Kdenlive 0.7.5 available at Ubuntu's repositories is an OLD RELEASE, NOT SUPPORTED ANY MORE!
To installed the newest release you will have to do the following:
   1. go to System Menu > Software Sources > Third-Party Software;
   2. click add and paste this line in:
      ppa:sunab/ppa
   3. close software source and click reload.
   4. Find and install Kdenlive newest version.

If you got problems with the way the program is display, you may be having the same problem I got in this thread:
[http://ubuntuforums.org/showthread.php?t=1343142](http://ubuntuforums.org/showthread.php?t=1343142) it´s easy to solve.

You can mimic many MM's title and credit functions with the use of a text slide and a picture to picture transition. Even MM's “moving title”. An example of picture to picture transition can be found in the following video: [http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video](http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video)
Many other tutorials are found here as well:
[http://www.kdenlive.org/tutorial](http://www.kdenlive.org/tutorial)

I´ll make a template of a “moving title” in kdenlive very soon.

You will find that at the end, Kdenlive lets you do a lot more things than MM.

---

### Post by misswham on 2009-12-09
I tried to paste ppa:sunab/ppa in the apt line after i clicked add and when i tried to click add source, it wouldnt let me.  how can i add this?

---

### Post by bumanie on 2009-12-10
I use kino - only draw back it downloads via firewire only - if your dv camera has firewire, no problems.

---

### Post by bit mad on 2009-12-10
> **misswham said:**
> I tried to paste ppa:sunab/ppa in the apt line after i clicked add and when i tried to click add source, it wouldnt let me.  how can i add this?

For 9.10 you could try
[B][http://ppa.launchpad.net/sunab/ppa/ubuntu](http://ppa.launchpad.net/sunab/ppa/ubuntu)
karmic
main[/B]

but by the looks of [http://www.kdenlive.org/forum/kdenlive-076-ubuntu-karmic-jaunty-intrepid?page=1](http://www.kdenlive.org/forum/kdenlive-076-ubuntu-karmic-jaunty-intrepid?page=1) they've been having a few install problems.

---

### Post by 3rdalbum on 2009-12-10
I've never been able to install Kdenlive except for the Ubuntu repositories. I've tried building it from source, using the Debian Multimedia repository, and even getting some packages for a newer Ubuntu and copying the contents to my filesystem. The latter was the closest I got - Kdenlive ran but wouldn't actually work with any videos.

I suggest sticking with whatever version is in the repositories.

---

