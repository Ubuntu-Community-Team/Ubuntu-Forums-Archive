---
title: "Installing Flash for Ubuntu 64"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by daniell59 on 2011-08-26
I seem to remember that there was a program that made installing flash very easy. Does anyone have a link?

Thanks

---

### Post by BlinkinCat on 2011-08-26
Is this it?
[http://ubuntuforums.org/showthread.php?p=11053538](http://ubuntuforums.org/showthread.php?p=11053538)

Note #3 if you don't have Natty

---

### Post by haqking on 2011-08-26
> **daniell59 said:**
> I seem to remember that there was a program that made installing flash very easy. Does anyone have a link?

Thanks

use Flash-Aid it works great.

I use the beta flash 11 for x64 and works fine though.

---

### Post by bodhi.zazen on 2011-08-26
Define easy ...

The tar ball from adobe is as easy as 3 commands in a terminal

[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

1. Get the tar ball :

```
wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_64_080811.tar.gz
```

2. extract 
```
tar -xvf flashplayer11_b2_install_lin_64_080811.tar.gz
```

3. copy the lib
```
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins
```

About as easy as any other method

---

### Post by haqking on 2011-08-26
> **bodhi.zazen said:**
> Define easy ...

The tar ball from adobe is as easy as 3 commands in a terminal

[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

1. Get the tar ball :

```
wget http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11/flashplayer11_b2_install_lin_64_080811.tar.gz
```2. extract 
```
tar -xvf flashplayer11_b2_install_lin_64_080811.tar.gz
```3. copy the lib
```
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins
```About as easy as any other method


Well you could ease it a little with GUI ;-)

Download, right click and choose extract.  Then copy the libflashplayer.so to the directory.

depends on how comfortable you are in terminal

---

