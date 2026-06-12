---
title: "How do I update Firefox?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by psam3 on 2009-10-30
I wanted to update Firefox to the newest version, as I just installed Ubuntu, however the update option is grayed out in the menu. I downloaded a tar.bz2 file from the official website but I don't know what to do with it. Can anyone point me in the right direction? Thanks

---

### Post by JamesParnell on 2009-10-30
when you dont have to download from the atual website, dont.

Best thing to to do is use the terminal:

sudo apt-get remove firefox

then

sudo apt-get install firefox-3.5


bare in mind this is just what i would do, i dont know if deleting the old version is really needed, but i did.

---

### Post by kansasnoob on 2009-10-30
I personally always use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by ghicksrn on 2009-10-30
Another way is to run Firefox as sudo

```
gksu firefox
```

then you will see the update option will not be gray any longer. However, some of your add-ons may not work with the newer version. Also, running a program as sudo makes your system vulnerable. So run at your own risk. I have done it with no problems whatsoever. If you use this option, do nothing other than the update, then close Firefox and restart it as a normal user.

---

### Post by tacantara on 2009-10-30
> **JamesParnell said:**
> when you dont have to download from the atual website, dont.

Best thing to to do is use the terminal:

sudo apt-get remove firefox

then

sudo apt-get install firefox-3.5


bare in mind this is just what i would do, i dont know if deleting the old version is really needed, but i did.

Having just re-installed 9.04 on a separate HDD partition, I found the 3.0 version of FF.  I followed the above installation, only to find that 3.0 still exists, and the 3.5 version carries the Shiretoko name (although it's clearly Firefox - not a deal breaker).  I changed the FF icon on my top panel to re-route to Firefox-3.5.

I also tried the suggestion to run 3.0 in the terminal with gksu.  While it un-grayed the Update item on the help menu, when I clicked it, I received a reply that no updates were available.

---

### Post by wojox on 2009-10-30
If you downloaded it to your home folder open a terminal:

```
tar xjf firefox-*.tar.bz2
```

---

### Post by QIII on 2009-10-30
Shiretoko is the un-branded Firefox available for Jaunty towards the end.

The Firefox branding came back in Karmic.

---

### Post by kansasnoob on 2009-10-30
Ubuntuzilla has me on Firefox 3.5.4 already:)

---

### Post by QIII on 2009-10-30
The Firefox that came with Karmic updated itself to 3.5.4

---

