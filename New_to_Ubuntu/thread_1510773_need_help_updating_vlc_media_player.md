---
title: "need help updating vlc media player"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-06-16
i have just recently installed vlc player and so far cant get it to play anything  like my big bang theory disk  how would i go about updating it?

---

### Post by Linuxforall on 2010-06-16
> **pyrofreak99 said:**
> i have just recently installed vlc player and so far cant get it to play anything  like my big bang theory disk  how would i go about updating it?

in terminal sudo apt-get install libdvdcss2

---

### Post by pyrofreak99 on 2010-06-16
it says that libdvd could not be found

---

### Post by mc4man on 2010-06-16
In a terminal run 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Or install directly from here
[http://packages.medibuntu.org/lucid/libdvdcss2.html](http://packages.medibuntu.org/lucid/libdvdcss2.html)

---

