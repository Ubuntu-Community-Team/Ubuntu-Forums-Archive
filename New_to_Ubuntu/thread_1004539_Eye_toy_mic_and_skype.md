---
title: "Eye toy mic and skype"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Aloush on 2008-12-07
Well when i was using windows i used my eyetoy as my mic and webcam for skype

and now it wont work when i make a test call says problem with audio playback and mirohpone my headsetr works as i listen to youtube videos but it doesnt in skype



Any help?

---

### Post by Aloush on 2008-12-07
Need to talk to somebody on skype so this is kind of urgent

---

### Post by mewithafez on 2008-12-07
[http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page](http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page)

That site has all the info on how to install the driver that most eyetoy webcams use. It worked for me (at least the camera did, I forget about the mic) when I needed to use my eyetoy but good luck. Here's a direct link to the install instructions:

get .tar.gz file from here [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource") and save it to your home directory. Go to the terminal, and then follow these steps: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall")

good luck!

EDIT: if you are on ubuntu 8.10, use this: [http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Installation_on_Ubuntu_8.10_Intrepid_Ibex](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Installation_on_Ubuntu_8.10_Intrepid_Ibex)

---

### Post by andersja on 2009-05-26
Is this still necessary in Janty / Koala?

---

### Post by andersja on 2009-09-28
> **andersja said:**
> Is this still necessary in Janty / Koala?

It would be useful if someone could confirm whether Sony EyeToys now works out of the box in the latest Karmic Koala (Ubuntu 9.10), as the instructions seem a bit out of date?

---

### Post by Jose Catre-Vandis on 2009-09-28
Eyetoy Video and Mic for Skype work more or less out of the box (old black one, not tested the silver one yet). Skype seems to drop the settings you make so you tend to need to revisit settings and reset them to the eyetoy.

You do need to edit the skype config.xml file for the video to work correctly. Work through the dedicated thread on this forum for eyetoy and you should get there.

[http://ubuntuforums.org/showthread.php?p=7846328#post7846328](http://ubuntuforums.org/showthread.php?p=7846328#post7846328)

---

### Post by andersja on 2009-10-06
Thanks, Jose!

---

### Post by Captain_Glen on 2009-11-24
I have both the black and silver eyetoy.  But the black one is at my Grandparents house and they haven't updated to 9.10 yet.  In 9.04 I had to change the resolution to 640x480 otherwise it was all green.  Here is the link: [URL="http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html"]http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html
[/URL]
The silver one initially worked out of the box with skype in 9.10.  But now the microphone has broken.  It makes me sound like a chipmunk.

I get the same problem with sound recorder.  So it is not a skype problem.

I think I have to manually set the sample rate of the microphone to either 44100khz or 48000khz but I don't know what configuration file to modify.  Does anyone know?

---

