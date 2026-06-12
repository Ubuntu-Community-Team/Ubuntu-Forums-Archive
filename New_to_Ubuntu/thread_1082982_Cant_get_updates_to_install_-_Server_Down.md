---
title: "Cant get updates to install - Server Down?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by gwurzel on 2009-02-28
Hi All, New User here, I've installed ubuntu 6.10 (was the only 1 I could get to install on an old laptop I had spare. I'm used to working with Unix etc, so thought it would be interesting - and I was right. 

I'm having a problem updating this tho, or installing any extra programs as it wont seem to recognise that i'm connected to the internet. 

Any advice welcome,


Wurzel

Edit *forgot to add, I'm using the laptop to browse around ho hum - so it has to be connected*

---

### Post by taurus on 2009-02-28
Edgy has been expired so the repos have been move to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).  Therefore, you need to edit your /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and replace the 

```
deb http://gb.archive.ubuntu.com/ubuntu/
```

to 
```
deb http://old-releases.ubuntu.com/ubuntu/
```
Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by howefield on 2009-02-28
6.10 has passed it's end of life date, I guess the repositorys are no longer available for it.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by gwurzel on 2009-02-28
ah ah, theres a surprise, its me being dimmer than usual. Thanks for the  quick replies.


Wurzel

---

