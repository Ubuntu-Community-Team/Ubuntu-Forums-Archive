---
title: "Big ! in the toolbar???"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by Smaug95swe on 2011-07-28
I dont know where it came from or what it is... (think it came after i updated)

[IMG]http://i.imgur.com/NyQQu.jpg[/IMG]

I tried pressing update and all but it dosent say there is any... and if i do sudo apt-get update the last packages cant be downloaded...

anyone know how to fix? plz tell me :P

---

### Post by wildmanne39 on 2011-07-28
Hi run this in a terminal and post the results here
```
sudo apt-get update && sudo apt-get upgrade
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Smaug95swe on 2011-07-28
W: failed to get [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: failed to get [http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/simple-ccsm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

(Was in swedish so i translated)

---

### Post by redbikemaster on 2011-07-28
Nevermind.

---

### Post by Smaug95swe on 2011-07-28
Ah thanks lol im not really even new to ubuntu... but rightclickign at the icon and take up the update manager didnt work cuz it didnt find any updates but now it did... hope it removes the "!" Thanks :)

---

### Post by wildmanne39 on 2011-07-28
Hi, open synaptic and click on settings then repositories,other software and uncheck those to ppa's because they are no longer on the server or the server is down.

---

