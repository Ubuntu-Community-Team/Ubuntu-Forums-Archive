---
title: "Audio Output not Working - Help!"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Roboman1273 on 2011-05-11
I just freshly installed Kubuntu 11.04 and my audio jacks are not producing any sound from any device I plug into them yet my laptop speakers still work correctly. I have tried messing with kmix and alsamixer and nothing works yet. Maybe it's a driver issue? Help appreciated.
 
I have a Dell Studio 17
i7 720Qm
RV 710/730 audio card.

---

### Post by Roboman1273 on 2011-05-11
Bump, any replies c'mon

---

### Post by rockstarrem on 2011-05-11
Have you tried the solution found on this page? : [http://www.linlap.com/wiki/dell+studio+15#comment_2c909f4a23fdd4ba80b5ca69f29f4525](http://www.linlap.com/wiki/dell+studio+15#comment_2c909f4a23fdd4ba80b5ca69f29f4525)

---

### Post by el_koraco on 2011-05-11
> **Roboman1273 said:**
> I just freshly installed Kubuntu 11.04 and my audio jacks are not producing any sound from any device I plug into them yet my laptop speakers still work correctly. I have tried messing with kmix and alsamixer and nothing works yet. Maybe it's a driver issue? Help appreciated.
 
I have a Dell Studio 17
i7 720Qm
RV 710/730 audio card.

You might wanna mess with Phonon. System settings, Multimedia, Phonon, and try to move the cards around a tad.

---

### Post by lidex on 2011-05-12
No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

