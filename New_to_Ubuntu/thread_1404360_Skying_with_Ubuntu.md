---
title: "Skying with Ubuntu"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-02-11
A short time ago I installed Ubuntu and I use it for a good 98% of what I do. The only real things I still use windows for is iPod managment and Skyping my parents (I'm a college student) Anyway, I've started using Songbird and GTK pod so skype is the whole reason for me having windows now. I know skype can be installed in Ubuntu, but I can't do video chat. Thats the big thing for me. Is there anyway to enable video chat with skype in ubuntu or another program that would let me do the same thing?

---

### Post by chaanakya_chiraag on 2010-02-11
Do you know if your webcam is supported in Ubuntu?  Most times, that's the reason why video chat won't work...what make/model is the webcam?  Is it integrated into the laptop?

---

### Post by Dougie187 on 2010-02-11
I can skype perfectly in ubuntu. I have a logitech Webcam. We also have some other no-name one that works fine too.

It was even easier to set up skype in ubuntu than it was in windows. I had to set it up for my wife in windows and the webcams wouldn't work without drivers, and those took a while to find.

---

### Post by Captainflowers91 on 2010-02-11
Well when I try to video chat all I can do is audio, but in skype I did a webcam test and the webcam worked fine, maybe even had better tracking than in windows. I read on other forums that you couldn't do actual video chat. But I'm hoping that their wrong

---

### Post by Merk42 on 2010-02-11
> **Captainflowers91 said:**
> Well when I try to video chat all I can do is audio, but in skype I did a webcam test and the webcam worked fine, maybe even had better tracking than in windows. I read on other forums that you couldn't do actual video chat. But I'm hoping that their wrong

They are wrong, you can do video chat in Linux.

As it appears your webcam works fine in Skype, are you sure you're hitting the button for video chat and not just audio chat in Skype?

---

### Post by Captainflowers91 on 2010-02-11
yea, I have it set to always do that. IDK, I've tried it, but when my roommate gets back I'll try it with him and see if we can do it that way. Maybe something changed and I just didn't realize it.

---

### Post by chaanakya_chiraag on 2010-02-11
Also, which version of Skype are you using?

---

### Post by Captainflowers91 on 2010-02-11
Well I'm using the newest version. I had to fiddle with some settings, but I finally got the video chat working. The only new problem is I keep getting an error message when I try to sign in because when I click on skype is tries to start skype again instead of opening the skype already running. The message says "Another Skype instance may exist". Anyway, I want to find a way that I can minimize is without this happening, but it won't place an icon on the gnome panel like in windows (I know, I hate having to say it, but it DOES work)

---

### Post by 2hot6ft2 on 2010-02-11
Glad you got it working. Just thought I would throw in kopete which does most IM's (and skype, see pic) and has video too.
You did try going to it in the menu and right clicking on it and selecting "Add this launcher to panel" right?

---

### Post by Captainflowers91 on 2010-02-11
Thanks, I installed that, but I'm still having that Skype issue. Any ideas?

---

### Post by 2hot6ft2 on 2010-02-11
I don't use skype but do you mean when you minimize it that it doesn't minimize to the bottom panel like in windows?
It's probably an icon on the top panel up in the top right.

2 instances of it running hit ALT+F2 and use
```
sudo killall skype
```

then start a new session and there will only be the new one you start.

---

### Post by Captainflowers91 on 2010-02-13
The video now works fine, but my microphone won't work right. It makes my voice go off and on throughout the call

---

### Post by chaanakya_chiraag on 2010-02-14
Are you using pulseaudio or are you accessing the sound card directly?  Check in the Skype audio options

---

