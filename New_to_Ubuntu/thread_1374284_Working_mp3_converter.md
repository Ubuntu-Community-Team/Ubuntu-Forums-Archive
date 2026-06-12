---
title: "Working mp3 converter?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-01-06
So, I have a few files in ogg format. I want to put these on my phone, but it doesn't work. 

So I downloaded SoundConverter. Didn't come with mp3 plugin, so I go to find that. Click the page and get that the browser does not know how to handle apt. 

Can happen. So I move on to SoundKonverter. That one does have mp3 support, but it gets stuck, and never finishes converting. 

Then I go to scripts. My last turn. 
Does. Not. Work. Either. 

So whose laptop do I have to clean around here to find out how to get an mp3? :)

---

### Post by blazemore on 2010-01-06
Try this one
[http://www.jochem.name/Projekte/ogg2mp3](http://www.jochem.name/Projekte/ogg2mp3)

Bear in mind you lose a lot of quality converting one lossy format to another.
Kind of like taking a photo of a printed photograph.

---

### Post by Falc7 on 2010-01-06
Handbrake seems quite good

---

### Post by netol on 2010-01-06
To use the mp3 export feature in SoundConverter:
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

Also, you can use ffmpeg.

---

### Post by Alex De Duck on 2010-01-06
Thank you all brave knights! Problem solved.

---

