---
title: "hulu video not working"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by eeeek on 2009-07-23
Hi,

I can't get Hulu video to load up. I can see the scrolling stuff on the homepage, but no videos load up. I tried reinstalling flash player. It's been working fine for a few months and now it doesn't.

I did all the updates, restarted the computer, etc. 

I'm running a 64-bit, Ubuntu 8.04 system - 4GB RAM, plenty of hardware power. 

Any ideas?

Hulu seems to stop working on me about once every 2-3 months. It kinda bugs. I have a Windows XP computer right beside me that runs Hulu videos just fine.

Oh, I also tried other sites - Vimeo, Youtube - and it plays fine.

Any ideas?

---

### Post by jbrown96 on 2009-07-24
Have you tried installing the 64-bit flash plugin? It seems to work a lot better but isn't in the repos. First remove everything related to flash. Open up Synaptic and search for flash; you will need to remove flashplugin-nonfree or similar and also make sure that gnash and swfdec-mozilla aren't installed. [Download the plugin]("http://labs.adobe.com/downloads/flashplayer10.html") Then close Firefox. You need to decompress it; easiest way is to right click and there will be an option. You should get a file named flashplugin.so or something similar; "cut" this file. Open up your home directory and show hidden files (I think ctrl+h in gnome). Browse to your .mozilla folder and create a folder called plugins and paste the plugin file in there. Restart firefox and it should work better. I have this version, and I just tried hulu and it worked fine. The only other thing that I might be doing different is using firefox 3.5, which is awesome btw and you can install it with ```
sudo apt-get install firefox-3.5
```

---

### Post by xx58 on 2009-07-24
:rolleyes: When I first made clean Install 9.04, then I had little problem, but everything was just work fine Hulu, now Hulu stop to work. Don't know what can be the problem. I have Flash Plag in latest.... I think it was come after I upgrade Firefox 3.0 to 3.5
Any help, advice???

---

### Post by eeeek on 2009-07-24
Hey jbrown96 - I followed your advice and it works. Thank you so much. Just what the forums are for.....

I really appreciate it.

---

