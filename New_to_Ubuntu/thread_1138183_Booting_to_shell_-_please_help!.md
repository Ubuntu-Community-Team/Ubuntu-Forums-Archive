---
title: "Booting to shell - please help!"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by lil_pidge on 2009-04-26
I'm a brand new Ubuntu user - and have hit some problems!
I've installed Ubuntu on my old Dell Latitude CPi laptop with the sole use of playing MP3's from my NAS through my stereo.
I'm a Windows man, but thought this would be a good project to learn about Linux.
I battled with mounting my NAS, then playing MP3's and finally then noticed the soundcard wasn't working correctly and was clicking loudly when playing audio.
I was trying to sort this through the forum (NeoMagic NM256AV) and now I've clearly done something to make Ubuntu boot to the shell.
I'm flumoxed!
If I type 'gedit' at the prompt, I get "Gkt-WARNING **: cannot open display:"
What have I done - and how do I solve it!
(Please bear in mind I'm a complete begineer - although I did think I was fairly computer savvy before Linux!!)
Thanks in advance for your help!

---

### Post by spiderbatdad on 2009-04-26
at your shell prompt, try entering: ```
startx
```

---

### Post by sstakes1 on 2009-04-26
I'm sure you should be seeing some messages on the screen as to why you are dropping to the shell. I suspect since you were playing around mounting NAS you may have borked the mounting of the home partition.

Gedit is a graphical editor and requires graphical environment. You can use something like vi or nano to edit files in the shell

---

### Post by lil_pidge on 2009-04-26
Spot on!
 
It's easy when you know how!!
 
Many thanks!

---

### Post by lil_pidge on 2009-04-26
Sound card doesn't work at all now - but that's fine! I can carry on searching the forums for that one! Thanks for your swift replies.
PS: If the shell was giving me messages as to why it was dropping to the shell - I didn't see them - or don't yet know where to look... but I'm learning! Thanks all!

---

### Post by wizard10000 on 2009-04-26
If startx worked then gdm isn't running - which is the way I set my machines up anyway.  If you want the login screen back all you have to do is reenable gdm.

I think bum (Boot Up Manager) is far superior to the services applet in Ubuntu - and sysv-rc-conf is far and away the best of the three but sysv-rc-conf is a runlevel editor and you can *really* break your system with it if you're not careful.

---

