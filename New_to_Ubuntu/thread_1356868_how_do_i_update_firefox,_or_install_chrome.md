---
title: "how do i update firefox, or install chrome??"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by pous on 2009-12-16
is there a way to do so easyly :confused:
i cant find them in the add/remove app, and if i d/l from the web i get this bunch of files and folders that i don't know what to do with or where to put them...

---

### Post by viljun on 2009-12-16
As far as I know you should install chrome going here:
[http://www.google.com/chrome/?hl=fi](http://www.google.com/chrome/?hl=fi)

I suppose it's not yet in repositories.

Firefox will be updated automatically if you installed it through repositories. If not, I recommend You to uninstall it and reinstall using synaptic - ie using repository.

---

### Post by sandyd on 2009-12-16
add this to your sources.list
```

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main                                                         
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

```then
```

sudo apt-get install ubuntuzilla chromium-browser
ubuntuzilla.py

```

that will get you the latest version of chrome (its still beta for linux)

---

### Post by pous on 2009-12-16
thanks for the link, i'm now installing chrome, the firefox i got is from the repositories, but i havent seen any updates and i found while adding some extensions that 3.5 is out for linux already... but then didnt know what to do when i tried to d/l from their website...

by the way, i cant seem to be able to install the extension for thinderbird to open my hotmail & gmail...

---

### Post by ricardo.gloe on 2009-12-16
You can get Chrome from here 
[http://www.google.com/chrome?platform=linux](http://www.google.com/chrome?platform=linux)

Just download the file and then double click, then click install.

---

### Post by kukibird1 on 2009-12-16
I have used this in the past for the latest official build of firefox or thunderbird . 
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

or 

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa")

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

---

### Post by nanotube on 2009-12-16
> **carlee said:**
> add this to your sources.list
```

deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main                                                         
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

```then
```

sudo apt-get install ubuntuzilla chromium-browser
ubuntuzilla.py

```

that will get you the latest version of chrome (its still beta for linux)

just a note: ubuntuzilla doesn't exist in the official repositories... nor does it have anything to do with chrome. :)

---

### Post by pous on 2009-12-16
thanks for your help!!

---

