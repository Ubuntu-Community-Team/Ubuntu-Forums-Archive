---
title: "Need help installing flash"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by RingWraith007 on 2010-12-05
[FONT=Times New Roman]I need help with installing macromedia flash  [/FONT]
I can't play videos on youtube, facebook, etc.
I downloaded flash from adobe and installed it yet nothing happened... :?:

---

### Post by khelben1979 on 2010-12-05
How did you install it? Also, you need to restart the web browser after it has been installed for the new changes to take effect.

In Ubuntu Software Center you haveto make sure that you don't have other flash players installed in the system like [libflash]("http://packages.ubuntu.com/search?keywords=libflash&searchon=all&suite=all&section=all"), [gnash]("http://packages.ubuntu.com/search?suite=all&section=all&arch=any&searchon=all&keywords=gnash") or Ubuntus own install package of Adobe flash. Uninstall them if they are there, because otherwise, your install of Adobe flash player will not take effect.

---

### Post by sikander3786 on 2010-12-05
Or give flash-aid a try.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by garvinrick4 on 2010-12-05
If it is easier for you and you have not installed ubuntu-restricted-extras which give you quite a few codecs, flash, to play media with:
```
sudo apt-get install ubuntu-restricted-extras
```
It is nice to start any ubuntu install with this.

---

