---
title: "LMMS Help"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Ziadance on 2011-02-05
Hello
I hope I've posted this in the right place, I checked but could not find threads on a similar problem.

I'm new to LMMS, it seems to be working fine (samples play) but when I hover over controls/buttons, only a white box appears where normally there would be text, informing you what the function is before you click on it.

[ATTACH]182746[/ATTACH]

Please note 'song editor' menu.

Any suggestions?

Thank you Z

---

### Post by marin123 on 2011-02-05
try changing ubuntu theme. i had a few themes that would have the box and text inside the same color.

btw what version are you using? the latest is 0.4.9.

---

### Post by NightwishFan on 2011-02-05
This bug is known, LMMS is QT I believe so changing a theme probably will not help. As far as I know this bug is not there in the PPA version:
[https://launchpad.net/~tobydox/+archive/lmms](https://launchpad.net/~tobydox/+archive/lmms)

To install ppa run:
```
sudo add-apt-repository ppa:tobydox/lmms && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Ziadance on 2011-02-05
Hi 
Thanks for the reply.  
I tried Preferences>Appearance>Theme but none of those got rid of the white box.  
I'm using 0.4.5, I only installed it last week.  I'll try to get the newest version.
Thanks

---

### Post by Ziadance on 2011-02-05
> **NightwishFan said:**
> This bug is known, LMMS is QT I believe so changing a theme probably will not help. As far as I know this bug is not there in the PPA version:
[https://launchpad.net/~tobydox/+archive/lmms]("https://launchpad.net/%7Etobydox/+archive/lmms")

To install ppa run:
```
sudo add-apt-repository ppa:tobydox/lmms && sudo apt-get update && sudo apt-get upgrade
```

Fantastic, thats done the trick ;o)

Now I can spend the weekend making noise!

Thank you Z:guitar:

---

