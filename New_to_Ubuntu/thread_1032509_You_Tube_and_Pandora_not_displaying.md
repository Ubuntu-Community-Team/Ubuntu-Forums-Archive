---
title: "You Tube and Pandora not displaying"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-06
So I just recently formatted to 64bit Ubuntu, but now when ever I try to load [www.pandora.com](www.pandora.com) or anything off of you tube all I see is a blue box where the movie/music is suppose to display... but firefox is not saying that it is missing anything or giving any reason why it wouldn't display what it is suppose to... suggestions anyone?

~Jeff

---

### Post by kestrel1 on 2009-01-06
I would get the latest flash player installed.

---

### Post by ibizatunes on 2009-01-06
have you install ubuntu restricted
```
sudo apt-get install ubuntu-restricted-extras
```

Also you may want mediabuntu install to
[www.medibuntu.org/](www.medibuntu.org/)

---

### Post by donkyhotay on 2009-01-06
> **ibizatunes said:**
> have you install ubuntu restricted
```
sudo apt-get install ubuntu-restricted-extras
```

Also you may want mediabuntu install to

It's medibuntu and here's a link too adding their repositories, they have a lot of very useful stuff that a regular desktop user will want.
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by Therion on 2009-01-06
Open Synaptic, search for and install, the **ubuntu-restricted-extras** package and see if that doesn't set things right.




Edit: Wow... Beaten to the punch not once, but twice even.  Must be getting old(er)...

---

### Post by fooman on 2009-01-06
adobe now has a 64 bit flash plugin that works really well (for me anyways)...here the link:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

scroll down and download the "64bit plugin for linux (tar.gz)".  after it downloads, right click on it and extract the file.  that will leave you a "libflashplayer.so" file.   copy that file to /home/<user name>/.mozilla/plugins

restart firefox and you should be good.

EDIT:  you should uninstall any other flash/gnash packages that you have previously installed before installing this plugin.

---

### Post by beastrace91 on 2009-01-06
Restricted extras and Mediabuntu have both already been installed... going to try that download for the 64bit flash player now.

~Jeff

---

### Post by beastrace91 on 2009-01-06
Thanks fooman that worked like a charm!

~Jeff

---

### Post by beastrace91 on 2009-01-06
Ok so that flash driver made pandora work but Youtube is still displaying as blue box... any ideas?

~Jeff

---

