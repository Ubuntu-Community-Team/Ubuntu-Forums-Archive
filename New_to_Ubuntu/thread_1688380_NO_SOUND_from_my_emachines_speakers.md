---
title: "NO SOUND from my emachines speakers"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by BoMonGhanni on 2011-02-15
I am starting to lose hope in ever getting this ubuntu OS  fully functioning on my Emachines M5414.  After a little research, i have found no other examples of installations on this model. What I have noticed was that the graphics and video play are not as smooth as on Windows XP.  But most importantly...I HAVE NO SOUND IN MY SPEAKERS!!!!  Fortunately, I can get sound through the headphone jack.  But, I would really like sound without external devices.  Anyone have any ideas.  I have tried much of what is on the threads I looked through to no avail. Please help!!?

---

### Post by scouser27 on 2011-02-15
If the soundcard works (and it must do for sound to come out of the headphones) then it's possibly that the speaker volume is turned down. 

Have you tried alsamixer or one of the other sound-mixer applications?

If it's not installed, try getting it using either synaptic or 
```
sudo apt-get install alsa-utils
```

---

### Post by cariboo on 2011-02-15
What have you got the output connector set to in System->Preferences->Sound, on my netbook I have it set to Analog Speakers

---

### Post by BoMonGhanni on 2011-02-15
I have tried that, and get this....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-utils is already the newest version.
alsa-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And....still no sound.  Thanks for the input.  The more the merrier. lol

---

### Post by BoMonGhanni on 2011-02-15
cariboo907....I initially blew your suggestion off, since I had checked that area over and over again.  However, I owe you an apology.  For, you sent me BACK to that very area where I went through, partially out of desperation, and checked the list of options in System->Preferences->Sound->Output.  It turns out that I cannot use any amplifier selections nor the mono selection.  But, I am happy to say that[COLOR=Lime] **I HAVE SOUND!!!! **[/COLOR]Thank you for your time and nudge BACK in the right direction.

---

