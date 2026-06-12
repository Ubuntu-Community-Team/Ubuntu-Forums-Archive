---
title: "tried search, need help....Headless system help"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by JNasci7906 on 2009-05-12
Hello ladies and gents, I've done the searching and I have had no luck. Here is my scenario and what I want to do. I'm moving to a new house and am going to be forced into getting sat. internet (wild blue...ugh). With that comes slow speeds and data caps. However, there is one shining light. My parents live 35 minutes away from home (10 from work) and have Cable. Fast speeds, no caps. 

I would like to be able to set up a headless system, with ubuntu, hardwired to my parents router. I would like to be able for this system to download torrents to a local hard drive. I would like to be able to connect from my home on my macbook to the headless machine and upload the torrent files and have them start downloading. That way I can stop by my parents once a week and take the data off quickly.

I realize that these needs are high (i think, im good but not that good with computers lol) and I am willing to go with a headed system, or any other operating system.

Forgive my noob-ness, the search feature just is not working for me. Thank you all in advance for any help you can give. Walk throughs and step by steps are preferred. thanks so much!!!

---

### Post by Cheesemill on 2009-05-12
The latest versions of Deluge allow you to install different parts of the application on different machines. I used this guide
[http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)
with a couple of changes so I now have the Deluge daemon running on my headless 8.04 server, the WebUI running on my virtual LAMP server, and the Gnome GUI running on my Jaunty desktop and laptop.

This lets me connect to my server via my Jaunty machines if they're close to hand or use the WebUI if I'm on someone else's machine to manage my torrents. This is the best solution I've come across because I only have to fall back to the WebUI when absolutely necessary unlike other headless clients.

Cheesemill


PS - The forum search is broken, for best results just use Google but append *site:ubuntuforums.org* to your search terms.

---

### Post by lovinglinux on 2009-05-12
+1 for Deluge

You can connect to the server using webui, remote gtk and cli. It has everything you need, a nice gtk interface, a nice webui, it is easy to configure and has all important torrent features.

---

### Post by JNasci7906 on 2009-05-12
reading now, thanks guys

---

### Post by 3rdalbum on 2009-05-12
Transmission-daemon (in the "transmission-cli") package is really good. It provides a web gui on port 9091 where you can upload .torrent files and change some settings. Just forward port 9091 to your parents machine, set transmission-daemon to run on login, and you've got yourself a torrent box.

---

