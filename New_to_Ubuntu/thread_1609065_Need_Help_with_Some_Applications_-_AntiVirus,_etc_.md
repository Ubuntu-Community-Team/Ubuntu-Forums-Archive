---
title: "Need Help with Some Applications - AntiVirus, etc And youTube Help"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by D3SI on 2010-10-29
i just installed Ubuntu and i am completely new to it.

what are the best software for following?

Anti-Virus?
Firewall?
Video Player?


any other software you would recommend?

also videos on youtube are working for some reason and its giving me no error whatsoever

---

### Post by NickJones on 2010-10-29
Welcome to Ubuntu!
Installing software on Ubuntu is different to Windows, you don't normaly downlaod a program and install it through a web browser. Pretty much all of the software you will ever need comes through what's known as the Ubuntu Software Centre, you can find it under Applications, Ubuntu Software Centre, just type in what software you want and it will find it.

The great thing about the Ubuntu Software Centre is you aren't going to find any viruses in there, as it's all maintained by nice people. So AntiVirus isn't essential unless you start downloading heaps of unknown software, and even then, it's unlikely. In terms of firewall software, it's pretty much the same situation, Ubuntu is awesomely secure. 

In terms of video Players, I use VLC (Which you can find in Ubuntu Software Centre)

---

### Post by NickJones on 2010-10-29
Oh, and to fix your YouTube problem, install Adobe Flash Plugin from the software centre.

---

### Post by D3SI on 2010-10-29
the reason i need Firewall and Anti-Virus is because i am in Torrenting.

so if you have any recommendations please let me know

Thank You

also anything on youtube problem?

i was using Chrome

---

### Post by jroa on 2010-10-29
Anti-virus and Firewall--no need with Linux unless you plan to do some dangerous things.

I can't comment on the best Video Player.  There are many to choose from, though.

---

### Post by lightningfox on 2010-10-29
A good GUI firewall for Ubuntu is Gufw.

Here is a webpage about it: [http://dedoimedo.com/computers/gufw.html](http://dedoimedo.com/computers/gufw.html)

---

### Post by armageddon08 on 2010-10-30
Although you would not require any antivirus on Linux; if you want Avast, AVG and Avira provide Linux versions of their softwares. 
For Firewall I'd recommend GUFW or Firestarter(for advanced users). 
IMHO, VLC Media Player is the best video player you could ever find on the planet.

---

### Post by P4man on 2010-10-30
As others suggested, you dont need a firewall. In windows a firewall closes ports because there is by default software listening to a gazillion ports. On ubuntu by default there is absolutely nothing listening and closing those ports is therefore pointless. If you run "server" software that listens to a port, like a webserver or in your case, a torrent client, you will have the torrent client listening to those ports, but once again you dont want to close those ports or your torrent client will not work.

The only reason for a software firewall on ubuntu is if you want to create specific rules like allowing some traffic locally (lan) and disallowing it over the internet; say you have a webserver that you only want to be accessible from your local machine or lan.  Then a firewall could do that for you. Doesnt sound like you need one though, but I could be wrong.

As for antivirus; the threat of a virus for ubuntu is theoretical at best. No need if that is what you are worried about. But if you want to detect windows virusses (which are harmless on ubuntu), go ahead and install any of the apps suggested above.

As for a videoplayer, I cant recommend SMPlayer enough. Its in the repositories (software center).

Last question about youtube; afaik chrome comes with flash preinstalled nowadays. Which version of ubuntu and chrome (or chromium?) are you using?

---

### Post by AngusH on 2010-10-30
> **armageddon08 said:**
> For Firewall I'd recommend GUFW or **Firestarter(for advanced users)**. 


I would not recommend firestarter to anyone. From my understanding the project is virtually dead in terms of development, besides GUFW will do most stuff you need, and if you need more UFW (from the command line) is a bit more configurable.
Angus

---

### Post by walt.smith1960 on 2010-10-30
If you're familiar with synaptic (system->administration->synaptic package manager) and search for "restricted extras".  That will install flash, java and codecs for video. I find movie player works okay with the restricted extras enabled. I'm using Lucid but I don't know that it matters. VLC is also an excellent video player and has its own codecs.

---

### Post by D3SI on 2010-11-01
whats the Best Music Player?

i noticed that Rhythmbox  adds my music twice, so i have every song x2 in the playlist :|

---

### Post by weasel fierce on 2010-11-01
> **D3SI said:**
> whats the Best Music Player?

i noticed that Rhythmbox  adds my music twice, so i have every song x2 in the playlist :|

Best depends on what you want :)

I use Rhythmbox as its simple to use, and its quick to look just for certain albums or artists.
I used XMMS quite a bit which is basically winamp in feel.
Also used Amarok for a while, which was very nice and very polished.

A lot of people seem to enjoy Banshee but I haven't used it.

---

### Post by D3SI on 2010-11-01
i like Rhythmbox is well but is there any way i can fix that problem?

---

### Post by P4man on 2010-11-01
> **D3SI said:**
> i like Rhythmbox is well but is there any way i can fix that problem?

Perhaps you are having the same issue as the last poster here:
[http://ubuntuforums.org/showthread.php?t=1508157](http://ubuntuforums.org/showthread.php?t=1508157)

---

