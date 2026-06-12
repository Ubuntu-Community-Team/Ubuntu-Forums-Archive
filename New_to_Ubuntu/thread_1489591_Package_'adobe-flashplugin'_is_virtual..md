---
title: "Package 'adobe-flashplugin' is virtual."
date: 2010-05-21
forum: New to Ubuntu
---

### Post by shmy on 2010-05-21
Hi all

I'am new ubuntu user and my colleague which helps me in problems is in holiday. -> I have really no idea! :-)

I Updated from 9.04 to 10.04 and now the Flash player works no more. I tried to install it like described on this page: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)
After this installation appears this error message: Package 'adobe-flashplugin' is virtual.

What do I have to do now?

Thanks and Greets, shmy

---

### Post by chiefster on 2010-05-21
I am an utter beginner at all this but if you can remove the flash plugin that isn't working you can install "ubuntu restricted extras" from synaptic which contains a working flash plugin and lots of other useful goodies for media playback

---

### Post by shmy on 2010-05-21
Thanks for your help chiefster. I removed now Adobe Flash Player and Ubuntu restricted extras (It was already installed) and installed Ubuntu restricted extras again. After that I restarted the Laptop but it's still not working (tried with YouTube). It this is for relevant information, I use Firefox...

---

### Post by chiefster on 2010-05-21
are you using a 64bit edition of ubuntu?
This bug is listed with links to a few solutions
[https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/554449](https://bugs.launchpad.net/ubuntu/+source/apturl/+bug/554449)

Bear in mind I am a n00b as well so it might be a good idea to wait for someone else to help you before you do anything drastic.  It seems the solutions work for 32bit editions (the normal one) and not for the 64bit edition.

---

### Post by shmy on 2010-05-21
How can I find out whether I use 32 or 64 bit?

Thank you anyway! I'll wait :-)

---

### Post by lovinglinux on 2010-05-21
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by shmy on 2010-05-21
Okay thanks lovinglinux, I should understand this :-) But I still need to know how I can find out whether I use 32 or 64....

---

### Post by philinux on 2010-05-21
Open a terminal , Apps>Access>

```
uname -a
```

Post back what it says.

---

### Post by shmy on 2010-05-21
Nice, thank you!

Linux mariuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_**[COLOR=black]6[/COLOR]4** GNU/Linux

So I think 64bit....

---

### Post by lovinglinux on 2010-05-21
> **shmy said:**
> Nice, thank you!

Linux mariuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_**[COLOR=black]6[/COLOR]4** GNU/Linux

So I think 64bit....

Yes.

---

### Post by 52177 on 2010-12-01
I managed to get flash player working using firefox 3.6 on Ubuntu 10.04 i went to a site and it said install missing plug ins so i did then refreshed and it worked.

---

### Post by Lord Funzo on 2011-02-07
Hey mate, I had the same problem lasting the last two releases, I have just this minute found my solution.

taken from:
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

fire:
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

I really hope that helps, I hate flash but the internet is boring without it, now to listen to my computer basically melt down whilst I watch some pixelated video :D.

---

### Post by A9010 on 2011-07-15
Muchas GRACIAS  Lord Funzo.      con tan solo copiar y pegar en la terminal:


sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get  update && sudo apt-get install flashplugin64-installer

---

