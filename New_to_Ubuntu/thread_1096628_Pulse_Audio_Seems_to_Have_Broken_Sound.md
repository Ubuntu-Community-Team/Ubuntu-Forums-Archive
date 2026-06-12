---
title: "Pulse Audio Seems to Have Broken Sound?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Azhtabak on 2009-03-15
My sound isn't  working correctly, and I think it's due to pulse audio? It was working fine last night, then I installed pulse audio (in the form of all the packages marked 'pulse audio whatever' in adept) to see what it was like - I didn't notice much change, though there was a slight buzzing. This morning, however, Amarok doesn't want to play anything for me - it tells me my normal output doesn't work, so falling back on pulse audio, and then I just get the buzzing. I reset the laptop, and the Kubuntu chimes worked normally, though they didn't pick up my headphones, but again Amarok had the same problem.

I haven't had any other sound problems - it's always worked fine until now. I did get some kind of notification when first starting Amarok, but I think I reset it that time and it worked fine.

Does anyone have an idea of how to fix this?

---

### Post by Azhtabak on 2009-03-15
Bump

---

### Post by Azhtabak on 2009-03-15
Minor update: Just tryed reinstalling Amarok 2, but unfortunately no luck that way.

---

### Post by pocketchange on 2009-06-12
I have a very similar issue where I launch amarok, and it says my audio device doesn't work and it's falling back to Pulse Audio.  Then I find that my player works.  If I close the player and open it again, I get no error and nothing's working at all.  Lame.

---

### Post by flyingmayo on 2009-08-03
Please don't do this people.  If you found a solution to the problem, come back and post it!!!

---

### Post by dex008 on 2009-11-03
i just installed kubuntu 9.10 and after installing codec to play mp3 in amarok, i realize that my kubuntu didn't have any sound. my pc used HDA intel ALC883. in system setting->multimedia i see pulse audio, HDA intel (ALC883 analog ), HDA intel (ALC883 digital). and then i test them, and i found that only pulse audio give me output sound.
and i prefer pulse audio in my multimedia setting. when i reopen my amarok, it give me message that pulse audio didn't work, and change to HDA intel but i can hear my music stream on my earphone now. i'm happy that my kubuntu now have a sound :p

---

### Post by pmorton on 2009-11-07
Unreliable sound in Ubuntu is second only to ATI graphics drivers as the biggest source of consistent chronic headache in the distro.

From Teapot post #8 on [http://tremulous.net/forum/index.php?topic=12084.0](http://tremulous.net/forum/index.php?topic=12084.0), worked for me on two clients:

sudo aptitude install libsdl1.2debian-pulseaudio;sudo aptitude remove libsdl1.2debian-alsa

---

