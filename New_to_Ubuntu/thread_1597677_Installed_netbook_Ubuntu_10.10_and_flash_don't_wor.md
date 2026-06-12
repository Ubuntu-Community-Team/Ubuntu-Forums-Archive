---
title: "Installed netbook Ubuntu 10.10 and flash don't work"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Mobjerkn on 2010-10-15
Hi,
I though Flash should work in Firefox after installing 10.10 (clean install) but when going to youtube it asks me to install or upgrade my flash. When I try to install Flash it says it's all ready installed on my system. Any ideas?
Regards

---

### Post by cariboo on 2010-10-15
How did you install flash?

---

### Post by AndyM3 on 2010-10-15
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by cariboo on 2010-10-15
That's the way I install it, what version do you get when you type:

```
about:plugins
```

In Firefox's address bar? I have:

```
File: npwrapper.libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r85
```

---

### Post by keylimekai on 2010-10-18
I am having this problem too. about: plugins yields this:

**Shockwave Flash**

 File:  libgnashplugin.soVersion:   Shockwave Flash 10.1 r999.
Gnash 0.8.8, the GNU SWF Player.   Copyright (C) 2006, 2007, 2008, 2009, 2010   [Free   Software Foundation]("http://www.fsf.org/"), Inc. 
   Gnash comes with NO WARRANTY, to the extent permitted by law.   You  may redistribute copies of Gnash under the terms of the   [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   
  Compatible Shockwave Flash 10.1 r999.MIME Type Description Suffixes Enabled    application/x-shockwave-flash Shockwave Flash swf Yes

---

