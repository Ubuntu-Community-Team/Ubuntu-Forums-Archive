---
title: "Getting Opera Browser to auto-update"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-07-02
Hello,

I would like my Opera browser to automatically update to the latest version on my ubuntu computer.


I found [http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/](http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/) .


It leads me to [http://deb.opera.com/](http://deb.opera.com/).

Which of the following should I use:
potato, woody, sarge, etch, lenny, sid
?

---

### Post by LookTJ on 2009-07-02
On [http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/](http://kyleabaker.com/2009/04/04/how-to-opera-repository-for-debian-based-linux/)

it says that sid non-free works fine.

---

### Post by hanzj on 2009-07-02
Taylor,
Thanks for the reply. So sid works fine, but is that the best? And is the best good enough? Thanks.

---

### Post by LookTJ on 2009-07-02
Also you will have to do this

```
[COLOR=#800000]sudo wget -O – http://deb.opera.com/archive.key | sudo apt-key add -
```[/COLOR]

---

### Post by LookTJ on 2009-07-02
> **hanzj said:**
> Taylor,
Thanks for the reply. So sid works fine, but is that the best? And is the best good enough? Thanks.
Well sid is the testing release of Debian so it shouldn't be too much trouble.

---

### Post by hanzj on 2009-07-02
Thank you! I now have 

Version: 10.00 Beta 2
Build: 4458

installed.

---

