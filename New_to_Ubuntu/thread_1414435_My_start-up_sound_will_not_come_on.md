---
title: "My start-up sound will not come on"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by fightforlife on 2010-02-23
I have Ubuntu 9.10 on my Acer Laptop. I have really enjoyed it, it's a very solid system, however;

I used to have the start up sound come on when Ubuntu started up. It had the drums and the theme sound (default sound). Now it does not come on. I have checked the startup applications and everything looks okay. I have sound from a movie or an MP3 file. All other sounds are fine. I must have fumbled up something.

If someone would have an idea of how I could troubleshoot that, or get my theme sounds back, I would appreciate it.

---

### Post by no2498 on 2010-02-23
right click the sound icon
play around in it a bit put something with sound in cd or on as play a video

till you get sound
hope this helps

---

### Post by 416inversed on 2010-02-23
Does System>Preferences>Startup Applications have check next to 'GNOME Login Sound'?
 
If so, what happens when you paste this into terminal?

```
/usr/bin/canberra-gtk-play --id="desktop-login"

```

---

### Post by fightforlife on 2010-02-25
Okay, I tried the command to the login sound and it said the directory or file was not found.

I have another computer, so I copied the canberra-gtk-play file to a thumb drive from another computer to my laptop and put it on the desktop. Using the command from the terminal off the desktop 

canberra-gtk-play --id="desktop-login" 

the sound played without any problems.

So, it is something set wrong on that file that's in the /usr/bin directory. I tried to copy that file from another computer into that directory and it said I don't have permission to do that.

Should I just put the new file (canberra-gtk-play) into another directory and set the startup to that? Or, can I change that file, or copy the new file in?

---

### Post by Kakers on 2010-02-25
> **fightforlife said:**
> I tried to copy that file from another computer into that directory and it said I don't have permission to do that.


did you put sudo in front of the command ? :D

---

### Post by fightforlife on 2010-02-25
I still can't get the sound to work - only once did I get it to work. And, no I did not put sudo in the command. I just now tried it and still no sounds. I'm ignorant of how the terminal works I think. I'm trying to learn. Thank you so much so far though. I appreciate it.

---

### Post by fightforlife on 2010-02-25
If I go to /usr/share/sounds/ubuntu/stereo and type the following:

play desktop-login.ogg

Then I can hear the sound I want.

But I can't do it with the canberra-gtk-play file for some reason.

Hope that helps some.

---

### Post by fightforlife on 2010-02-25
Solved I think.

I added this to the startup applications list:

play usr/share/sounds/ubuntu/stereo/desktop-login.ogg

And that works when I log on. I guess that's a work-around as I don't get the drums either so. I'm good for a little while. Thanks for everyone's help.

It took forever to learn where the files were. But, it works!

---

