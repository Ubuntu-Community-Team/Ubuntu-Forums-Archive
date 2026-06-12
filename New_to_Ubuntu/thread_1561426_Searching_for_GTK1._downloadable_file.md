---
title: "Searching for GTK1.* downloadable file"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by alfa_80 on 2010-08-26
Hi,

I am searching for a GTK1.* downloadable file to run under my 64-bit machine since imlib-1.9.15 is only working with GTK1, not GTK2. I have tried with several files provided which can be found here: [http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/](http://ftp.gnome.org/pub/gnome/sources/gtk+/1.2/) Unfortunately, none of them worked, and it always complains about my 64-bit machine. I have been spending all day fixing this :(

Any help is highly appeciated.  

-alfa-

---

### Post by mcduck on 2010-08-26
Just install the packages from Ubuntu's repositories, GTK1 should be there. :)

---

### Post by mc4man on 2010-08-26
if referring to libgtk1.2 then it was removed from the repos after 9.04, but can still be gathered and installed.
You'd need 3 - 5 packages depending on whether you needed the -dev package.

Easiest is to dl the 3 or 5 packages, place in a folder, cd to it and run 
sudo dpkg -i *.deb, though you could do individually in this order  - with links - if needing the -dev's maybe do individually to avoid a possible broken packages situation (though easily fixed in synaptic


 
[libglib1.2ldbl]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl")
[libgtk1.2-common]("http://packages.ubuntu.com/jaunty/libgtk1.2-common")
 [libgtk1.2]("http://packages.ubuntu.com/jaunty/libgtk1.2")
[libglib1.2-dev]("http://packages.ubuntu.com/jaunty/libglib1.2-dev")
[libgtk1.2-dev]("http://packages.ubuntu.com/jaunty/libgtk1.2-dev")

---

### Post by alfa_80 on 2010-08-26
> **mc4man said:**
> if referring to libgtk1.2 then it was removed from the repos after 9.04, but can still be gathered and installed.
You'd need 3 - 5 packages depending on whether you needed the -dev package.

Easiest is to dl the 3 or 5 packages, place in a folder, cd to it and run 
sudo dpkg -i *.deb, though you could do individually in this order  - with links - if needing the -dev's maybe do individually to avoid a possible broken packages situation (though easily fixed in synaptic


 
[libglib1.2ldbl]("http://packages.ubuntu.com/jaunty/libglib1.2ldbl")
[libgtk1.2-common]("http://packages.ubuntu.com/jaunty/libgtk1.2-common")
 [libgtk1.2]("http://packages.ubuntu.com/jaunty/libgtk1.2")
[libglib1.2-dev]("http://packages.ubuntu.com/jaunty/libglib1.2-dev")
[libgtk1.2-dev]("http://packages.ubuntu.com/jaunty/libgtk1.2-dev")

Thanks  for the reply. It is actually not the one I am searching for because I am looking for the one related to gtk-config. As for gtk1.2, it is in favor of pkg-config. Is there any you found?

---

### Post by Bachstelze on 2010-08-26
> **alfa_80 said:**
> Thanks  for the reply. It is actually not the one I am searching for because I am looking for the one related to gtk-config. As for gtk1.2, it is in favor of pkg-config. Is there any you found?

gtk-config is in libgtk1.2-dev.

---

### Post by mc4man on 2010-08-26
Not sure then  what you're looking for, at least here the only gtk-config would be in the libgtk-1.2-dev package. (/usr/bin/gtk-config

---

### Post by alfa_80 on 2010-08-26
[U]
[/U]Thanks a lot everyone and especially mc4man. You all are right :-)

I got it.

---

### Post by Ibidem on 2010-09-24
If you'd rather not install the jaunty packages, there is a PPA:
[https://launchpad.net/~adamkoczur/+archive/gtk1.2]("https://launchpad.net/%7Eadamkoczur/+archive/gtk1.2")

Besides that, I have some old GTK1.2 software in my own PPA:
[https://launchpad.net/~ibid-ag/+archive/oldgtk1]("https://launchpad.net/%7Eibid-ag/+archive/oldgtk1")--it includes XMMS and a lot of GTK1.2 themes, plus several other tools of varying usefulness

---

