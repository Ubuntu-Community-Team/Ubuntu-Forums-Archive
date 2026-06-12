---
title: "Get volume buttons to control PCM"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by pissedoffdude on 2009-04-24
I recently updated to jaunty and I'm liking it so far, but I've one problem: I can't seem to get my volume buttons to control the PCM (they're controlling master volume).  In previous versions, I was able to do this by going to System>Preferences>Sound and setting PCM as default there.  However, in jaunty, PCM is no longer an option and all that appears is master. Anybody know a solution for this?

---

### Post by inobe on 2009-04-24
i don't know much about System>Preferences>Sound, never went there.

you can control pcm from right clicking volume control and selecting "open volume control"

---

### Post by pissedoffdude on 2009-04-24
> **inobe said:**
> i don't know much about System>Preferences>Sound, never went there.

you can control pcm from right clicking volume control and selecting "open volume control"

Yeah, but I'm trying to get my keyboard buttons to control the pcm instead of the master.  Thanks for the input though.

---

### Post by inobe on 2009-04-24
you can try selecting another device from the drop down menu.

remember the default device encase.


i was able to bring up multiple selections selecting HDA intel (alsa mixer)

---

### Post by pissedoffdude on 2009-04-24
> **inobe said:**
> you can try selecting another device from the drop down menu.

remember the default device encase.


i was able to bring up multiple selections selecting HDA intel (alsa mixer)

Done that, but nothing about the keyboard controlling pcm.  My sound is working perfectly, its just that I'm just trying to modify the channel that my keyboard volume buttons use.

---

### Post by inobe on 2009-04-24
what happens after selecting pcm then going to keyboard shortcuts ?

system> preferences> keyboard shortcuts

---

### Post by pissedoffdude on 2009-04-24
> **inobe said:**
> what happens after selecting pcm then going to keyboard shortcuts ?

system> preferences> keyboard shortcuts

The thing is, going there allows me to change the volume only for the master channel, not pcm.  I used to be able to modify this under system>preferences>sound before.

---

### Post by inobe on 2009-04-24
it's working fine for me, i can successfully lower and raise pcm with my keyboard.

[>>click<<]("http://www.itsyourpc.org/duane/files/Screenshot1111.jpg")

---

### Post by pissedoffdude on 2009-04-24
> **inobe said:**
> it's working fine for me, i can successfully lower and raise pcm with my keyboard.

[>>click<<]("http://www.itsyourpc.org/duane/files/Screenshot1111.jpg")

Problem solved! Thanks for your help.  I must've overlooked the options in system>preferences>sound the first time, as selecting the last option for the device gave me the list of channels to control.

---

### Post by inobe on 2009-04-24
your welcome.




enjoy

[http://ubuntuforums.org/showpost.php?p=7131999&postcount=4](http://ubuntuforums.org/showpost.php?p=7131999&postcount=4)

---

### Post by fabiosl on 2009-08-07
This thread Helped me. :D I'm using Hardy, instead...

---

