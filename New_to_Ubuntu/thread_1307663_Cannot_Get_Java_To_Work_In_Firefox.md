---
title: "Cannot Get Java To Work In Firefox"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by AlistairH on 2009-10-31
I've just replaced an old Ubuntu 7.10 partition with a clean install of Xubuntu. I have another partition to which I dual boot into Ubuntu 9.04.

I'm having trouble getting the Java browser plugin to work on Firefox under Xbuntu. I've tried both the open source version and the Sun version from the repositories, neither of which are listed in the Firefox Add-ons dialog.

Any ideas would be appreciated.

---

### Post by NCLI on 2009-10-31
Try installing xubuntu-restricted-extras, just to make sure EVERYTHING is there.

---

### Post by liquidbee on 2009-10-31
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Version might differ ( I don't know what's inside 7.10 repositories ) but the base name should be the same.

---

### Post by winotree on 2009-10-31
I had previously installed Java in my clean install of Koala 9.10  -- the information from **liquidbee** should give you what you need.  ;)

---

### Post by AlistairH on 2009-10-31
I'd already done both of those before posting. I'll uninstall them and try again.

---

### Post by AlistairH on 2009-11-03
I had to completely remove all traces of java then re-install them. Not sure what happened but all is well now thanks.

---

