---
title: "Checkinstall Help?"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-06-25
Before we start, checkinstall is for packaging/compiling .deb files for linux correct? I was wondering how you get it and how to use it. If someone has a good webpage that would point me in the right direction that would be great. Post anything else you think I should know too.

---

### Post by Bachstelze on 2010-06-25
```
sudo apt-get install checkinstall
```

then when you're compiling something, instread of [font=monospace]sudo make install[/font], run [font=monospace]sudo checkinstall[/font].

---

### Post by mikewhatever on 2010-06-25
Here you go.
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
Here's a rather detailed example:
[http://kmandla.wordpress.com/2008/09/16/howto-build-software-updates-in-ubuntu/](http://kmandla.wordpress.com/2008/09/16/howto-build-software-updates-in-ubuntu/)

---

