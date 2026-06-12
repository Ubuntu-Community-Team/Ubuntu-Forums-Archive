---
title: "Video in GNOME smooth...in KDE periodic choppiness"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by zlapidus on 2010-08-27
Hi, I'm running 10.04, used GNOME for a while, then decided to take KDE for a spin.  I have a GTX 285 as my graphics card, which i installed the drivers for when I was using GNOME. Video played back full screen flawlessly, even at my resolution (1080p), and I was very happy.  I installed the kubuntu-desktop package and actually like it very much, but with an annoying issue. I typically watch a lot of movies on my computer, so video playback is an issue for me. In every player I've tried, KMPlayer, SMplayer, vlc, etc. video will play very smoothly for a while, like 10 seconds, then there'll be a second where the framerate of the video drops noticably - it's not horrible, but it's certainly distracting, and will really disrupt an action sequence or, actually really anything with motion. The thing that perplexes me is that I am using identical settings in GNOME, as far as I can tell, and if I switch back to GNOME playback is flawless.  I don't want to have to switch back to GNOME every time I want to watch a video. Also, I've been liking GNOME less since installing KDE has changed the cursors, and I feel like the appearance of some of my applications as well. The Elegant Gnome theme also looks really bizarre now.  I'm a linux newbie, is there anything you can think of that might help me solve this problem of intermittent video choppiness? Thanks a lot!

---

### Post by ankspo71 on 2010-08-28
Hi,
I don't know what it could be for sure, but I have some general advice...

You might want to fine tune your kde settings so that the desktop performs a little better if you haven't already. I wrote a little something about how to do it for Kubuntu 10.04: [http://sticky-bones.blogspot.com/2010/07/how-to-tweak-kde4-for-perfmormance.html](http://sticky-bones.blogspot.com/2010/07/how-to-tweak-kde4-for-perfmormance.html) 

Check to see if playing videos in fullscreen causes your computer to start using swap. You can do this by maximizing the video's window so that it is the size of fullscreen but not in fullscreen mode (so you can switch between windows), then open a Konsole (or any other terminal) window and run the 'top' command. Using swap is considerably slower and slow enough to make anything become choppy IMOP. While you are running top, check to see if anything else is consuming too much CPU and memory. firefox-bin while playing flash videos can reach as high as 120% CPU on my Pentium4 3.0 cpu w/hyperthreading enabled. (I'm assuming you have some trouble playing flash videos too)

Also, If it helps any... flash videos (and web apps) when displayed with Adobe Flash in Linux have a higher demand for resources as seen here: [http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/) . Also, I have noticed that chromium displays flash videos and games a little better than firefox (I'm still a bigger firefox fan though :D)
Hope something I said helps.

---

### Post by zlapidus on 2010-08-28
Thanks a lot for your reply, it's very helpful. After doing some diagnosis, I've noticed that the slowdown happens when it's in a window, too -- and not a screen-sized window, it happens in the triscuit sized window of the video at normal size, as well.

I messed with some config things, but it doesn't seem to make a difference. Thanks a lot for your help. I think I'll give it a little longer and then maybe just move back to Gnome, because that "just works" for me.

---

