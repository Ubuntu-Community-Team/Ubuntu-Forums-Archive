---
title: "Just a quick nvidia question"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by Duskao on 2009-05-08
For those of whom have a newer nvidia graphics card 2xx series. Are the drivers working well with them? I'm asking because I picked up a Radeon 4850 and the drivers are pretty much terrible at this point, at least in 9.04, so I switched back to 8.10 and they are a bit better, but still nothing to write home about. Please let me know, I am wondering about 3d applications and games with or without wine. Thanks in advance guys. 
BTW, I'm looking into a GTS 250. (I'm aware of the rebadging... doesn't bother me)

---

### Post by Kareeser on 2009-05-08
Assuming they can run off the drivers provided by Ubuntu or straight from the nvidia website, there should be no problems.

Driver support for nvidia is remarkably better than ATi. YMMV.

---

### Post by halovivek on 2009-05-08
you can check [this ]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html")more details and help.

---

### Post by djuke04 on 2009-05-09
I'm currently fighting with a GTS250 card and Intrepid.  The "new" drivers found under hardware drivers don't work, and the previous available driver only works right with D-Sub.  Also, when I installed the card, all my sound stopped working.  


As far as the graphics go, it's gorgeous.  It idles at about 2300 fps and under a pretty full load with two virtual machines open, some video playing and 3d effects messing with the cube it sits down around 300-350.  

I just need to get it working the rest of the way, but who knows - it might just be my system that's fighting so hard, I can't find much else about it here.

---

### Post by Duskao on 2009-05-09
Djuke04, Thanks so much for the reply. That is pretty much what I wanted to know. Don't get me wrong, I'm not happy that your card isn't working entirely perfectly, but I'm glad that you replied because that is the card I was looking into. But I am thinking I might try to stick it out with my Radeon 4850 since AMD just released so much info on about the cards to the open source community. I am crossing my fingers that it won't be long till there are some good Ati drivers. Wish me and all use die hard Ati fans luck with the new drivers :D.

Oh yeah, and Djuke04 if you read this again. You might want to check out EnvyNG. Its a really nice little program that will find the best drivers for your card and the system you are using. I'm using it and it is working really well, I have heard the same from other nvidia users as well.

---

### Post by alexsys on 2009-05-09
Yes, try EnvyNG. I use it with my nvidia 8500GT and it was a lot easier. Also remember to load the nvidia application in terminal: sudo nvidia-settings. You cant save changes if you just load it from the system menu.

---

### Post by djuke04 on 2009-05-11
I actually did try EnvyNG.  From my experience with it, it seems like a really nice utility.  The interface is simple and intuitive and it was nice, but it didn't seem to work for my system.  I'm not sure what the issue is, but MY particular hardware combination seems to not get along well with 8.10.  I'm not sure if it's my motherboard and graphics card or what, but I've had some weird fighty issues since the beginning.

I have a P5G43 ICH10 motherboard that I wanted to use onboard AV for as a media center PC.  But as the enhanced graphics work, the frame rates were getting super slow.  Also when I played 1080p movies, it would freeze, the audio would not sync, and it would pop up messages saying there were too many packets in the buffer, so I decided to upgrade the graphics to something with some more memory.  

Enter the GTS250 - what should be a gorgeous functioning graphics card - and absolutely is stunning when I boot up in windows.  But shoot, that's not the point, who WANTS to use windows?! Haha, so I've been messing around with Ubuntu trying to make things work.

NVIDIA actually has a really awesome write up for how to install the drivers.  I followed their steps as best I could, and wound up being halfway successful.  The graphics work pretty well now! 

My sound doesn't though.  It can't make sounds, and any program that needs to make sounds freezes.  So that's where I am, but I'm still working on it!  I'm guessing that I'll have to also get a sound card now, but would like to avoid it if I can.

---

