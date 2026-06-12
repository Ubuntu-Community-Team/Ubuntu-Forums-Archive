---
title: "Chainging startup music of Ubuntu"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-08-20
Hi I was wondering if it is possible to change the startup music of Ubuntu 10.04 to a sound clip of my choice....Can any one suggest how to do it? 

If so does the clip have to be of any particular sound format?

---

### Post by Vaphell on 2010-08-20
ubuntu uses .ogg format (compressed audio, just like mp3, except it's better) but i don't know if it has to be ogg. Probably it can open any audio format, though ogg is 'safe', because it is supported out of the box. There are plenty of tools that allow to reencode audio.

/usr/share/sounds/ubuntu is where system sounds are stored
you can create your own theme or simply overwrite files you want.

system_ready or desktop_login are what you want. currently system_ready is just a link to dialog_question

---

