---
title: "2 easy fast things , will help me so much !"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Majd04 on 2009-07-27
Hello everybody , 
i am new Ubuntue user , and i don't know much about it .
i have the 9.04 version .

and my friend told me to come her for help and told me to ask he for 2 trminal codes that i only have to copy and paste 

the first one will give me the last compiz pack 
the second one is a code to make me download some codecs and stuff to make youtube and mp3 files and so many media files run on my ubuntue .



sorry for my bad english , hope you guys understand me.

---

### Post by philcamlin on 2009-07-27
sudo apt-get install compizconfig-settings-manager

for compiz 

and 


[LIST=1]
[*]Go to Applications/Add/Remove and choose to show All Available Applications
[*]Next, from left menu choose Sound & Video and on search field enter “gstreamer” without quotes
[*]From the list bellow, choose all Gstreamer plugins:
[LIST]
[*]GStreamer ffmpeg video plugin
[*]GStreamer extra plugins
[*]GStreamer plugins for mms, wavpack, quicktime, musepack
[*]GStreamer plugins for aac, xvid, mpeg2, faad
[/LIST]
[*]Click Apply Changes
[/LIST]
After installing you can open every known audio/video format supported by Gstreamer framework.

---

### Post by terry_gardener on 2009-07-27
for compiz settings manager and most common codecs 

sudo apt-get install compizconfig-settings-manager ubuntu-restricted-extras 
enter password 
and then press y to accept. 

done

---

### Post by Majd04 on 2009-07-27
WoW thx too mcuh ,
i will do that now xD . 
But there is code i put in terminal and it start auto downloading stuff , which allow me to watch videos in youtube and mybe more thing .

---

### Post by philcamlin on 2009-07-27
> **Majd04 said:**
> WoW thx too mcuh ,
i will do that now xD . 
But there is code i put in terminal and it start auto downloading stuff , which allow me to watch videos in youtube and mybe more thing .

look at my bottom part of my postt thats for that :popcorn:

---

### Post by Michael.Godawski on 2009-07-27
> **Majd04 said:**
> WoW thx too mcuh ,
i will do that now xD . 
But there is code i put in terminal and it start auto downloading stuff , which allow me to watch videos in youtube and mybe more thing .

Thats exactly what ubuntu-restricted-extras is for: a package with all the codecs and plugins you need for multimedia heaven. 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by terry_gardener on 2009-07-27
the info given will let you get to the compiz settings manager and install all type of codecs, flash, java and msfonts etc etc. 

it is the package called ubuntu-restricted-extras which i have listed in my command above.

---

### Post by Majd04 on 2009-07-27
Love you all Love Ubuunte (No gay)
it is just cool . how fast stuff can be done .

---

### Post by iNaitvad on 2009-07-27
I think you should give a look to Ubuntu Tweak, its ok to do it from terminal, actually I think is the cleanest way, but some people find that extremly hard, so I recomend trying Ubuntu Tweak:
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)  just download de .deb package, its very easy to install...hope it helps you more

---

