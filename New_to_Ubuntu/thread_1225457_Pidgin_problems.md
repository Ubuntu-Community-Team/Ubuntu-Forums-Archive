---
title: "Pidgin problems"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by mrmgh1 on 2009-07-28
Ive been using Pidgin since I first installed UBUNTU, but this week, I constantly get a message saying that  pidgin cant auhenticate my id on MSN. 
Ive not changed my MSN password or any settings that I know of. 
IN desperation I un-installed Pidgin with the intention of re installing it. But now when I try to re add it I get 
W: Failed to fetch "http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.4_i386.deb
  404 Not Found"

So now Ive lost it altogether ! 

Please help, but also please be aware that as soon as you get technical with me IM lost , so keep help in simple terms please ?

---

### Post by LowSky on 2009-07-28
sudo apt-get install ubuntu-desktop

---

### Post by philcamlin on 2009-07-28
[http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)

follow that then try again :)

---

### Post by mrmgh1 on 2009-07-28
Still get 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.4_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.4_i386.deb)
  404 Not Found

Problem is as stated I dont know enough about the workings of linux to be sure I ve done everything I need to in order to follow your suggestions .

---

### Post by nhasian on 2009-07-28
i think you need to change your server source.

go to system->administration->software sources and choose to download from a different server.  then try to install pidgin.

---

