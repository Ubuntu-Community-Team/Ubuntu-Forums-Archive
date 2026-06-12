---
title: "[SOLVED] How to install Java in Ubuntu 8.10?"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by retskrad on 2009-01-01
I'm new to ubuntu and I already love it.
I have tried to goole, but people doesnt have any anonymous answears, eevryone has their own steps.

I have tried JRE in synaptic, nothing comes. up.
Please, help. Thanks.

---

### Post by adobrakic on 2009-01-01
Make sure you have the multiverse repo. added, and run

```

sudo aptitude install sun-java6-jre

```

in terminal

---

### Post by retskrad on 2009-01-01
How do I get thee multiverse repo in synaptic?

---

### Post by Gwasanaethau on 2009-01-01
Howya! Welcome to the community!

If you're looking for just the JRE, the synaptic package you're looking for is 'sun-java6-jre'. The JDK can be installed with 'sun-java6-jdk' and the mozilla-based browser plugin with 'sun-java6-plugin'. There are loads of other packages that you can install that begin with 'sun-java6-&#8230;' depending on what extra features you need/want.

I hope that's what you're looking for. If not, just let me know. Best of luck, now!

EDIT: Oh man, I'm so slow!

---

### Post by joukez on 2009-01-01
Have you already installed ubuntu restricted extras? Maybe that will solve the problem!

                       gr. Jouke

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) on that page you will also see the name Medibuntu when you klick on that you will go to the page that will provide the video playback and w32 codec

---

### Post by adobrakic on 2009-01-01
[http://www.howtodothings.com/computers-internet/how-to-enable-universe-and-multiverse-repositories-on-ubuntu](http://www.howtodothings.com/computers-internet/how-to-enable-universe-and-multiverse-repositories-on-ubuntu)

Nice instructions & easy to follow.
Hope this helps!

---

### Post by retskrad on 2009-01-01
I just want to view internet based java stuff, like games based on java....

---

### Post by Gwasanaethau on 2009-01-01
The 'sun-java6-plugin' package is the one you need, so. To enable the multiverse repositories, open up Synaptic and go to 'Settings', then 'Repositories'. Then tick the box that says, "Software restricted by copyright or legal issues (multiverse)" and click 'close'.

---

### Post by retskrad on 2009-01-01
It was already ticked. Then what?

---

### Post by oldos2er on 2009-01-01
Run "sudo aptitude update && sudo aptitude install ubuntu-restricted-extras" in a terminal.

---

### Post by joukez on 2009-01-01
I added something to my above post, just try, it will work

---

### Post by retskrad on 2009-01-01
Thanks, I wrote in "sudo aptitude update && sudo aptitude install ubuntu-restricted-extras", but it downlaoded a huge lsit of stuff... what does it do?

---

### Post by Gwasanaethau on 2009-01-01
Sorry it's taken me so long to reply. Once you've ticked the box, all you need to do is click 'reload' and wait for Synaptic to get the latest package updates from the server. You should be able to search for and install the Java packages you need then.

joukez and oldos2er: doesn't 'ubuntu-restricted-extras' install everything from LAME codecs to the Flash player, Adobe Reader and Microsoft's core TTF fonts *as well as* the JRE plugins?

---

### Post by oldos2er on 2009-01-02
> **retskrad said:**
> Thanks, I wrote in "sudo aptitude update && sudo aptitude install ubuntu-restricted-extras", but it downlaoded a huge lsit of stuff... what does it do?

 "Installing this package [ubuntu-restricted-extras] will pull in support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback."

---

### Post by wboyd53tx on 2009-06-21
Tis a sad day that I had to remove Ubuntu from my wife's computer and put the dreaded Windows back on it. To her, the ability to play Runescape was the selling feature for Ubuntu. But when she clicked "upgrade" to the newest greatest Ubuntu, she could not run Runescape anymore. Three Linux people working all day around the clock could not fix it. We tried putting the old Ubuntu back. We tried installing Java according to all of the instructions both in this forum and on the Runescape forums, but we could not get Runescape to play in HD mode anymore on her computer. Finally, after my wife was totally frustrated, I had my friend put Vista on her machine, and of course, it works perfectly.

I am still running Linux Mint on my machine, but I also upgraded to the latest version "Gloria" and lo and behold, it will not play runescape either, but I don't care as much about runescape as I do about Linux, so I'm sticking with Linux.

-Wayne  :(

---

