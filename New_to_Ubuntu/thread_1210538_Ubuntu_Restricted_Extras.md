---
title: "Ubuntu Restricted Extras"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by Rabz on 2009-07-11
i have enabled "ubuntu restricted extras" but still cant play any mp3's.
 
its still giving me an error mesage saying i need a "MPEG-1 Layer 3 (MP3) decoder plugin. 
 
i have searched my "Add/Remove" but cant find such a thing..
 
Any ideas?

---

### Post by oldos2er on 2009-07-11
What program are you using that's giving you the error msg?

---

### Post by Joeb454 on 2009-07-11
When you say enabled - do you mean you actually installed it, or just enabled the repository with the application in?

---

### Post by Rabz on 2009-07-11
"Movie Player".. It opened it when i double clicked my song and i figured thats the default program for playing mp3's..

---

### Post by Rabz on 2009-07-11
its installed..

---

### Post by credobyte on 2009-07-11
Open Add/Remove and search for gstreamer - how many ( approximately ) installed "results" are there ( various gstreamer packages ) ?

---

### Post by servicetech on 2009-07-11
Try it in VLC player.

---

### Post by CaptainMark on 2009-07-11
try purging the extras package and reinstall it using the terminal.

---

### Post by hyperdude111 on 2009-07-11
Have you 

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by vinutux on 2009-07-11
install these plugins fix your problem


gstreamer-plugings-bad

gstreamer-plugings-bad-multivers

gstreamer-plugings-ugly

gstreamer-plugings-ugly-multivers

---

### Post by Rabz on 2009-07-11
GREAT SUCCESS!! thank you.. i got it to "play" with the gstream thing..
 
and im saying "play" because i can see its playing.. but theres no sound..

---

### Post by Rabz on 2009-07-11
I used the command "alsamixer" and set everything to max.. still no sound..

---

### Post by credobyte on 2009-07-12
> **Rabz said:**
> I used the command "alsamixer" and set everything to max.. still no sound..

What music/video player you are using ( for mp3 playback ) ?

---

### Post by Rabz on 2009-07-12
I've tried Movie player, vlc and Rhythmbox.. other program that i should use??

---

