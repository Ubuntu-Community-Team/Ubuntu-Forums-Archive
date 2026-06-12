---
title: "how to install adobe flash player"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by fireunbuntu on 2010-12-09
hi i know it might  be a silly question but how do i install flash player to Ubuntu ?;)

---

### Post by coffeecat on 2010-12-09
Easiest way is to install ubuntu-restricted-extras from the Ubuntu Software Centre because that gives you java (not Sun Java), MS corefonts and a multitude of media codecs as well.

---

### Post by BugBuster on 2010-12-09
I have always done it this way..and has always worked ok..

Download the appropriate package from adobe site, and then extract the libflashplayer.so to your home folder.

Then do this :
```

sudo mv ~/libflashplayer.so /usr/lib/mozilla/plugins/
sudo chown root:root /usr/lib/mozilla/plugins/libflashplayer.so 
sudo chmod 755 /usr/lib/mozilla/plugins/libflashplayer.so

```

The procedure is same for 32/64 bit architectures.This way your flash plugin will work for all users.

---

### Post by kaldor on 2010-12-09
> **BugBuster said:**
> I have always done it this way..and has always worked ok..

Download the appropriate package from adobe site, and then extract the libflashplayer.so to your home folder.

Then do this :
```

sudo mv ~/libflashplayer.so /usr/lib/mozilla/plugins/
sudo chown root:root /usr/lib/mozilla/plugins/libflashplayer.so 
sudo chmod 755 /usr/lib/mozilla/plugins/libflashplayer.so

```

The procedure is same for 32/64 bit architectures.This way your flash plugin will work for all users.

No real use. Work with the repositories to keep things better in sync.

As the previous posts instruct, get the Restricted Extras package in the Software Centre. It's easier this way and is officially supported, too.

---

### Post by oldos2er on 2010-12-09
> **fireunbuntu said:**
> hi i know it might  be a silly question but how do i install flash player to Ubuntu ?;)

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

This gets you flash with the proper architecture (32- or 64-bit) for your system.

---

