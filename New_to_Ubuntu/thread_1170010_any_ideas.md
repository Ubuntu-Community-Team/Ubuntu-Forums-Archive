---
title: "any ideas?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Leapin_Lee on 2009-05-25
Hi. I'm running Jaunty 64 bit. I'm running the desktop version dual boot. I'm very computer illiterate. When I first put jaunty on my computer There was an icon I guess you would call it at the top right next to my internet connection icon that said I should install newer drivers for my Nvidia video card. I thought that was why you tube wasn't working so I installed the drivers. I did this as soon as I installed Jaunty so at that point I had never shut down or restarted my puter. I know now that I just needed to install some other things for you tube but, now when restart Ubuntu and sometimes when I shut my computer down it tries but instead I just get a bunch of lines going across my screen and I have to unplug the puter to get it to quit. Is this because of the new driver's I was prompted to install? Any ideas on what might be wrong or how to correct it?

---

### Post by Steelmourne on 2009-05-25
The stuff that goes across your screen when you reboot or shutdown the pc is just ubuntu shutting down or rebooting. As for youtube go to add/remove applications and search for ubuntu restricted extras which should enable flash on youtube. To check if the graphics card drivers installed correctly check hardware drivers in the sytem menu under administration.

---

### Post by presence1960 on 2009-05-25
to install Flash you can do as Steelmourne said or try this from Ubuntu Forums 64bit users section: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

Works flawlessly for me. Used it in Hardy, Intrepid & Jaunty. But either method will give you Flash.

As far as the text every once in a blue moon I get that. Just be patient and allow it to shutdown

---

### Post by Leapin_Lee on 2009-05-25
I'm sorry guess I wasn't clear on the problem. I have installed all kinds of extras and youtube now works great. The problem is when I try to shut down or restart my computer when I'm using ubuntu it won't do either. I have to unplug the puter to get it to shut down. When I try to restart or shut down it acts like it's trying but once the lines start going across the screen they never stop. The lines will just continue and all I can do to shut the puter down is unplug it. Thank you in advance

---

### Post by Steelmourne on 2009-05-25
Try this:

[http://ubuntuforums.org/showthread.php?t=1134201&page=3](http://ubuntuforums.org/showthread.php?t=1134201&page=3)

It might be related to wireless issues.

---

### Post by bcoffield on 2009-05-25
What kind of stuff do the lines say?

---

### Post by Leapin_Lee on 2009-05-25
The lines don't say anything. They are just a bunch of horizontal lines flashing on the screen

---

### Post by ursaminor on 2009-05-28
I run Jaunty on desktop HP AMD64. I also had problems on shutdown. My problem was corrected by installing the 2.6.30-rc7 kernel. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368366]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368366"). This may help. But it may help to post a bug report or question on Launchpad for more help.

---

