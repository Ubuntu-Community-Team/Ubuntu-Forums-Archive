---
title: "Plugins not working!"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by beano0528 on 2009-10-18
I updated Ubuntu to 9.04 and now then my plugins don't work for Firefox!  I have tried installing them, but it says I already have them installed.  I am new to all this linux stuff (as suggested by beginner talk).  Any help you can give would be greatly appreciated.

---

### Post by beastrace91 on 2009-10-18
What Ubuntu version did you upgrade from and what plugins are no longer working?

Help us help you,
~Jeff

---

### Post by beano0528 on 2009-10-18
8.04 and not sure.  Youtube doesn't work, stlouisblues.com, (I site I often go to), as well as several other sites.  I tried about:plugins and it said that all were enabled except the default plugin filename:  libnullplugin.so  Could this be the problem?

---

### Post by beastrace91 on 2009-10-18
Open up your synaptic packet manager (System->Administration->Synaptic) and search for "flashplugin-nonfree"

If it is already checked right click on it and select "mark for re-installation" and then hit apply.

If it is not checked - then check it and hit apply.

~Jeff

---

### Post by beano0528 on 2009-10-18
It wasn't checked, so I installed it, restarted Firefox, and it is still not working.

---

### Post by beastrace91 on 2009-10-18
In firefox select Tools->Addons->Plugins 

What is listed there?

~Jeff

---

### Post by beano0528 on 2009-10-18
default plugin
demo print plugin for unix/linux
divx web player
quicktime plug-in 7.2.0
shockwave flash
VLC multimedia plugin (compatible totem 2.26.1
window media player plug-in 10 (compatible;totem)

---

### Post by beastrace91 on 2009-10-18
Huh, it appears to be installed - what version does shockwave flash read?

~Jeff

---

### Post by beano0528 on 2009-10-18
9

---

### Post by sandyd on 2009-10-18
> **beano0528 said:**
> 9
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
download version 10 to desktop, then
```

sudo apt-get remove flashplugin-nonfree
sudo dpkg -i ~/Desktop/flash*deb
sudo apt-get -f install
```

---

### Post by beano0528 on 2009-10-18
I thought I tried version 10 too, but I'll try again.

---

### Post by beano0528 on 2009-10-18
> **carlee said:**
> [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
download version 10 to desktop, then
```

sudo apt-get remove flashplugin-nonfree
**sudo dpkg -i ~/Desktop/flash*deb**
sudo apt-get -f install
```
After doing this step I got: dpkg: error processing /home/beano/Desktop/flash*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/beano/Desktop/flash*deb

---

### Post by beano0528 on 2009-10-18
So after extensive research on how to fix this problem I'm assuming it has something to do with flash player or java?

---

### Post by beastrace91 on 2009-10-18
When you downloaded the file from that adobe link, did you select the .deb installer? If so just find where you downloaded it to and then double click the file to install it - no terminal required ;)

~Jeff

---

### Post by sandyd on 2009-10-18
> **beano0528 said:**
> After doing this step I got: dpkg: error processing /home/beano/Desktop/flash*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/beano/Desktop/flash*deb
EDIT:

should be ```
sudo dpkg -i ~/Desktop/install*.deb

```

---

### Post by beano0528 on 2009-10-18
> **beastrace91 said:**
> When you downloaded the file from that adobe link, did you select the .deb installer? If so just find where you downloaded it to and then double click the file to install it - no terminal required ;)

~Jeff
I tried it that way too.  It said it was already installed.  Would running the terminal the way carlee said this time matter, since it says it's already installed?

---

