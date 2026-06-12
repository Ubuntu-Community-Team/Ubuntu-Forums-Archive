---
title: "[SOLVED] Synaptic error message"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Scunnered on 2009-01-02
I was checking if Scribus was available for download via Synaptic only to have the following error message displayed :

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 E: _cache->open() failed, please report."

Can you please offer guidance on how I may once again access Synaptic?

Many thanks for your assistance

EDIT: tried the manual run code and found that when I accessed the terminal as sudo it came up with a further error.  I have attached a screenshot of this.  Looks like when I was thinking about removing needless language files that I have messed up somewhere.

---

### Post by the yawner on 2009-01-02
Just open up a terminal and type:
```
sudo dpkg --configure -a
```
That should do it.

---

### Post by Scunnered on 2009-01-02
Looks like edit does not permit screenshot to be added,

Hopi that I can do it from here.

---

### Post by the yawner on 2009-01-02
It's not an error. I believe you were trying to install the package localpurge and Synaptic has now installed the package and trying to configure it to remove language files. Were you trying to achieve this?

---

### Post by Scunnered on 2009-01-02
Yes, I was looking at removing surplus language files. 

When I saw all the varying options I closed the file but from what you say it seems still to be open.

What I was aiming for was to work only with English - UK.

Can you offer an easier way to achieve that?

Thanks for your guidance

EDIT : following the yawners post and my reply I attempted again to use Synaptic.  This time I was asked for my password and on entering it was confronted by :-

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first."

How may I close the application down ?

---

### Post by the yawner on 2009-01-02
Okay. Sorry it took me a while to check your reply. Anyway, you're supposed to select the which language/s you'd like to keep on that dialog by pressing che spacebar then continuing the process. Although I'm not sure which options selects UK english.

---

### Post by Elfy on 2009-01-02
Try the sudo dpkg --configure -a command again - tab should move you about the screen - up/down arrows I believe will allow yout to move up and down the language choices.

When you've made them tab to the ok button and enter

If you have no luck with that command 

```
sudo apt-get install -f
```

---

### Post by Scunnered on 2009-01-02
forestpixie

I went back and forward using tab and keys and eventually got out of the problem.

I can now properly access Synaptic.

My sincere thanks

---

