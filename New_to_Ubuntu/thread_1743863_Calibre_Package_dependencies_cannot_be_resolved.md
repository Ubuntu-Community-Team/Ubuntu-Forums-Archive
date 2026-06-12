---
title: "Calibre: Package dependencies cannot be resolved"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by DayLite on 2011-04-29
I just installed Ubuntu 11.04 and most of my programs will not work :(.
I tried to install **calibre**. and this is what came up. 

```
Calibre

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable.
 Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

The following packages have unmet dependencies:

calibre: Depends: python (>= 2.6) but 2.7.1-0ubuntu5 is to be installed
         Depends: python-pypdf (>= 1.10) but 1.12-3 is to be installed
         Depends: python-cssutils (>= 0.9.7~) but 0.9.7~b2-2 is to be installed
         Depends: python-encutils (>= 0.9.5) but 0.9.7~b2-2 is to be installed
         Depends: python-cherrypy3 (>= 3.1.1) but 3.1.2-1 is to be installed
         Depends: python-qt4 (>= 4.7.3) but 4.8.3-2 is to be installed
         Depends: calibre-bin (>= 0.7.44+dfsg-1build1) but 0.7.50+dfsg-0~ppa1 is to be installed
```Please advise, I don't understand :confused:

---

### Post by cariboo on 2011-04-29
There seems to be a problem with calibre on Natty see bug #[lpbug]754886[/lpbug]

---

### Post by oldos2er on 2011-04-30
[http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)

Try the directions under 'Binary install,' they worked for me.

---

### Post by DayLite on 2011-04-30
> **oldos2er said:**
> [http://calibre-ebook.com/download_linux](http://calibre-ebook.com/download_linux)

Try the directions under 'Binary install,' they worked for me.

:-D Thank you. It worked!

I have the folder on my external drive. With Ubuntu 11.04 in order to load the folder in Calibre I have to mount it. Didn't have to do that in Ubuntu 10.04 and Ubuntu 10.10.

Thanks again.  I appreciate you helping me.

---

### Post by oldos2er on 2011-04-30
You're welcome.

---

