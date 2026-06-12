---
title: "no full screen with youtube?"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by kekearif on 2010-10-20
hey, does anyone else have a problem watching videos on youtube in full screen with ubuntu 10? mine will not work. I click full screen and the screen enlarges but the video freezes (the sound still plays). any idea why?

---

### Post by uRock on 2010-10-20
64bit or 32bit?
Which ubuntu 10? 10.04 or 10.10?

---

### Post by kekearif on 2010-10-20
32bit 10.10

---

### Post by ivarn on 2010-10-20
ok, close the browser, go to synaptic and see if gnash is installed.
If it's not install, keep it that way.
Run this command in the terminal:[FONT=monospace]
[/FONT]sudo apt-get install ubuntu-restricted-extras
This is obviously a flash problem, and this command will install the flash plugin you need.
See if this helps.

---

### Post by kekearif on 2010-10-20
> **ivarn said:**
> ok, close the browser, go to synaptic and see if gnash is installed.
If it's not install, keep it that way.
Run this command in the terminal:[FONT=monospace]
[/FONT]sudo apt-get install ubuntu-restricted-extras
This is obviously a flash problem, and this command will install the flash plugin you need.
See if this helps.

thanks, fixed :)

---

### Post by kekearif on 2010-10-20
actually my mistake. still not working. worked once now it's doing the same. still image with audio arghh

---

### Post by kekearif on 2010-10-20
any ideas?

---

### Post by ibizatunes on 2010-10-20
If you have remove gnash and install ubuntu-restricted-extras
That should work but maybe we need to do some more digging
A few ideas to get you started 

[http://www.google.com/chrome?platform=linux](http://www.google.com/chrome?platform=linux)

Install chrome brower and see if your gettting the same issue

reboot if you havent already - dont thin that will work
if it works in chrome try giving yourself a new firefox profile
in nautilus >  view >show hidden files > then in home > rename the .mozzila  to .mozzila.old

---

### Post by uRock on 2010-10-20
What method did you use to install Flash?

---

### Post by kekearif on 2010-10-20
dont remember think it was just there

---

### Post by qsx on 2010-10-20
When it is something easy to install and remove like Flash, I always try uninstalling it and reinstalling it before moving on to other possible fixes. I recommend trying that. Even before trying that you could check to see if it is updated to the current version at:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by sydbat on 2010-10-20
For Firefox, install [Flash-Aid]("https://addons.mozilla.org/af/firefox/addon/161939/"). Should clear things up.

Also, what is your graphics card/RAM/CPU/other important hardware? Might be a hardware issue.

---

### Post by kekearif on 2010-10-20
> **sydbat said:**
> For Firefox, install [Flash-Aid]("https://addons.mozilla.org/af/firefox/addon/161939/"). Should clear things up.

Also, what is your graphics card/RAM/CPU/other important hardware? Might be a hardware issue.


nice it worked thx :)

---

### Post by gandaran on 2010-10-20
try disabling hardware acceleration in flash, right click in the flash video window and go to the adobe flash settings
this worked for me and many users too.

---

