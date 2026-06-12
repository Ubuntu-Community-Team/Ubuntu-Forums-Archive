---
title: "install subsonic"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by trucker33377 on 2009-01-04
what would be the easiest way for a noob like myself to play my mp3 files?
I need them to play on their own from an Http. In the past i have used mediamaster to do this but now it seems there servers are full.
Ive come across this Subsonic player and it looks like it needs to have Tomcat 5.5 with some mods installed.
I also found a tutorial but ran into problems right off.
Now the Goal here is to play these files, so if theres a better way to do this I am open to it.

---

### Post by kgas on 2009-01-04
you can try xmms2 simple command line player. A good article is also there in wiki.

---

### Post by Michael.Godawski on 2009-01-04
hi

I would install the package 

ubuntu-restricted-extras

to enable mp3 support and download many other codecs as well.
```

sudo apt-get install ubuntu-restricted-extras
```

I guess you need these packages to hear mp3:

 [B][B]gstreamer0.10-plugins-ugly
[/B]w32codecs [/B]

---

### Post by trucker33377 on 2009-01-04
maybe im not clear here. what I want to do is make it so i can give you a url to hear my music. Not me playing it on my PC i can do that ok

---

### Post by twent4 on 2009-03-19
Did you get this figured out yet? (posts about 2.5 months old).

Just got this working a couple of days ago, hope this helps, actually conjured this up for various forums here. Get the vanilla subsonic setup running on your laptop, then register for a free DNS service, something like dynDns.com does the trick (dynamic dns is what i used). Create usernames for your friends. Then, point them towards the address created with the DNS service, port 8080 was the default subsonic share i believe.

Also, for dynDNS to work properly, you need your computer/router to send it your ip. Most modern routers can do that for you (look for DDNS in settings), but if its just your computer, their website can point you towards linux clients for achieving the same goal. I would also recommend that you forward any incoming port 80 traffic to port 8080 on your server, that way you don't need to give your friends the port number when handing them the URL. Let me know if this helps at all.

---

### Post by trucker33377 on 2009-04-23
ya i got it figured out i got a stream from another server and use icecast

---

