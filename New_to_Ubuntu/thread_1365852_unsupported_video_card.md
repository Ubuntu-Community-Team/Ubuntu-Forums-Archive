---
title: "unsupported video card?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Beastlicker on 2009-12-27
Hey. I've tried booting from the live cd plenty of times, and the only method that seems to work is through safe graphics. I used that mode to install ubuntu to my extra hdd.

Once installed, I enabled the restricted drivers for my nvidia geforce 9800 gt video card. The only resolutions that are offered to me through the nvidia driver program is up to 640x480. My native resolution is 1440x900.

Is there anyway to fix this low resolution problem? I tried editing the nvidia configuration file through gedit, but that only disabled me from logging on, so I had to reinstall ubuntu. Is it that my video card is unsupported?

P.S, I am trying to get Ubuntu 9.10 x64 running.

---

### Post by sandyd on 2009-12-27
i assure you its supported, i have one and its running a dual screen config w/ no problems.

i downloaded the 177.82 drivers and it worked like a charm.

for more info, look here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

and scroll down..... lower.... lower.... and youll see it

---

### Post by Beastlicker on 2009-12-27
Thanks. Did you have any problems with low resolution when you first started using it?

---

### Post by sandyd on 2009-12-27
nope.
once i installed the drivers, it lept instantly to the maximum resolution.
before, it was a 600*800 resolution (w/ vesa), which makes me wonder if youve installed the drivers properly.

---

### Post by Beastlicker on 2009-12-27
When I installed it, I went to the restricted drivers and enabled it from there only to leave me with the same low resolution. I may try again sometime tonight. Should I be following the [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to activate it?

---

### Post by Beastlicker on 2009-12-27
And is there any reason as to why I am only able to do safe graphics mode with the live disc?

---

### Post by deathbyswiftwind on 2009-12-27
why dont you try using envy to install your nvidia drivers. I did on my sisters laptop and it worked like a charm

---

### Post by Beastlicker on 2009-12-27
I am currently on safe graphics mode on the live disc. I am planning to install sometime soon.While it's installing can you tell me exactly how to use envy? Should I enable the restricted driver then use this envy?

Also, something is going wrong. When I open up terminal on live disk, I get the error bash: /etc/bash_completion: Input/output error

Should that be happening?

---

### Post by gradinaruvasile on 2009-12-27
Or just use the latest driver from Nvidias site. I use it on all my computers, its really easy to install. But you have to reinstall it on every kernel update...

---

### Post by Beastlicker on 2009-12-27
I just figured out how to use envy. I will try that. If that doesn't work, then I will use the nvidia one from the website. That is a .run file right? I tried doing that once before and it would not work with unicode...

---

### Post by sandyd on 2009-12-27
> **Beastlicker said:**
> I am currently on safe graphics mode on the live disc. I am planning to install sometime soon.While it's installing can you tell me exactly how to use envy? Should I enable the restricted driver then use this envy?

Also, something is going wrong. When I open up terminal on live disk, I get the error bash: /etc/bash_completion: Input/output error

Should that be happening?
run memtest and some other hard disk checking tools.

you **can** possibly have a bad ram chip, or problems with your hard drive
the former can likely cause the problems the video card is having

---

### Post by Beastlicker on 2009-12-27
The thing is, I have windows 7 installed on my main hard drive and that has ran fine for a good amount of time. I've had my ram chips for about two years now and they have stayed in good condition. I think it's just my video card may be having problems. I will try to install ubuntu once again and use some other methods. It worked with my old video card, but with my new one, it seems to be buggy.

---

### Post by sandyd on 2009-12-27
check gpu temp.
and 
[http://www.techenclave.com/graphic-cards/gpu-memory-tester-135350.html](http://www.techenclave.com/graphic-cards/gpu-memory-tester-135350.html)

---

### Post by Beastlicker on 2009-12-27
I just finished installing ubuntu, so let me restart and try to install driver via envy.

---

### Post by 3rdalbum on 2009-12-27
Run the "nvidia-settings" program as root (gksudo nvidia-settings)

Select the resolution you want and tell it to write the change to the Xorg.conf file.

---

### Post by Beastlicker on 2009-12-27
Okay, it seems that my monitor is stuck on 640x480 resolution. I did the root nvidia settings and all it did was expand the screen, but my monitor is stuck at that resoution. And also, I have no xorg file for some reason.

Yeah. I went into the x server settings and for some reason, it says that my monitors native resolution is 640x480. It should say 1440x900. Is there any way to fix this?

---

