---
title: "DVD stoped working - This is how I fixed it!"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by say.hello.to.anna on 2011-01-22
Hi, just a summary to be of any use to anyone else stuck. My DVD stopped working, though was fine for music and files. Symptom was that if you press play it just switched back to stopped/paused again straight away. There were occasional notices about /dev or something not working, but nothing much in the logs that I could understand. I found some advice about an issue online, they didn't get it fixed, but it fixed my problem straight away. A good first try if yours is broken I think.

Go to applications, accessories, terminal (in 10.10 this is the location of the terminal)

copy and paste in the following line

sudo /usr/share/doc/libdvdread4/install-css.sh

you need to use control-c to copy it, and shift control c to paste it.  this instruction will "Re-install decss"

you might need to enter your password, this is your normal password. Wait for the text to stop. Close the terminal and try your DVD again.

I found the info here > [http://www.pubbs.net/201012/ubuntu/3874-ubuntu-1010-dvd-playback-stopped-working-after-the-upgrade.html](http://www.pubbs.net/201012/ubuntu/3874-ubuntu-1010-dvd-playback-stopped-working-after-the-upgrade.html)

there are some additional steps that did not work on my computer, but it was ok cause the first was fine. 

Best

Anna

---

### Post by ubudog on 2011-01-23
Thanks for sharing!  Also, another command that may help with MP3 issues, YouTube issues, and DVD issues.

```
sudo apt-get install ubuntu-restricted-extras
```

Installs a bunch of codecs, etc.  Very useful.

---

### Post by Verbeck on 2011-01-23
> **say.hello.to.anna said:**
> 
I found the info here > [http://www.pubbs.net/201012/ubuntu/3874-ubuntu-1010-dvd-playback-stopped-working-after-the-upgrade.html](http://www.pubbs.net/201012/ubuntu/3874-ubuntu-1010-dvd-playback-stopped-working-after-the-upgrade.html)

a little closer to home : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by wep940 on 2011-01-23
While this is the solution for copy protected DVDs and is well known in the forum, it never hurts to have a fresh approach to using it.  Thank you for your simple guide.

---

### Post by say.hello.to.anna on 2011-01-23
what is really odd is that the DVD worked for months with 10.10 - no issues, all the correct region for the player etc - then one day it just stoped. I don't get why...

anna

---

### Post by wep940 on 2011-01-23
Probably got an update that included a package that reset some of the dvd settings.

---

### Post by say.hello.to.anna on 2011-01-23
> **wep940 said:**
> Probably got an update that included a package that reset some of the dvd settings.

Does this constitute a bug? I am lucky that I know how to go about fixing stuff even though I don't usually understand what the fix is. Its not userfirendly though, to lose the use of your DVD cause of an upgrade.

Whats to be done?

---

