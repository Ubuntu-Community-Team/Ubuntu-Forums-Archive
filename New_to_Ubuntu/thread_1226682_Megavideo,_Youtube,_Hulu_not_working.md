---
title: "Megavideo, Youtube, Hulu not working"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2009-07-29
I was bored and decided to watch mythbusters online, but all the megavideo links are broken, for some reason it goes to the website and shows the player, but the player is blank, theres no ad and no loading bar, it is just black. At first I just thought Megavideo was down, but it is the same with Hulu, Youtube, 56 and everyother online media player I've looked at. it worked yesterday, and my internet conection is finedoes anyone know what might be wrong?

---

### Post by Linux_Man on 2009-07-29
Sounds like a problem with Flash (if you are watching these in your browser) what version of Flash do you have?

---

### Post by Commisar Jimp on 2009-07-29
I just downloaded flash two or three days ago so I'm pretty sure I've got the most recent one, is there a way to check?

---

### Post by earthpigg on 2009-07-29
> **Commisar Jimp said:**
> I just downloaded flash two or three days ago so I'm pretty sure I've got the most recent one, is there a way to check?

lets start from scratch and keep it simple, just for kicks.

close firefox.

system -> administration -> synaptic -> search for 'flash'

mark to '*completely* remove' any flash plugin you see.

hit 'apply'.

once it is done, search for the 'ubuntu-restricted-extras' package. install it.

start firefox.

work?


edit - ubuntu-restricted-extras is the standard metapackage that includes flash, mp3, wmv, etc support. installing ubuntu-restricted-extras is the 'standard' way to get all this stuff. lots of websites out there give crappy how-to guides or are for older versions of ubuntu. another alternative is that, instead of *_sticking to the repositories whenever possible_*, a user may have gone to youtube and clicked the 'click here to install flash!' link like he or she is still using microsoft windows or apple os x. :D a third alternative is that ubuntu is imperfect and screwed up.

---

### Post by Commisar Jimp on 2009-07-29
> **earthpigg said:**
> lets start from scratch and keep it simple, just for kicks.

close firefox.

system -> administration -> synaptic -> search for 'flash'

mark to '*completely* remove' any flash plugin you see.

hit 'apply'.

once it is done, search for the 'ubuntu-restricted-extras' package. install it.

start firefox.

work?


edit - ubuntu-restricted-extras is the standard metapackage that includes flash, mp3, wmv, etc support. installing ubuntu-restricted-extras is the 'standard' way to get all this stuff. lots of websites out there give crappy how-to guides or are for older versions of ubuntu. another alternative is that, instead of *_sticking to the repositories whenever possible_*, a user may have gone to youtube and clicked the 'click here to install flash!' link like he or she is still using microsoft windows or apple os x. :D a third alternative is that ubuntu is imperfect and screwed up.
Yeah that was it, I downloaded flash about two days before they upgraded, and now I had to do it again, but I got it working now. Thanks guys.

---

### Post by lovinglinux on 2009-07-30
For future reference...

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by Ubun2 Us3r on 2009-08-04
check to see if you are also using GNASH, because that can conflict with other flash plugins

---

