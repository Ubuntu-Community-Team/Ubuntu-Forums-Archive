---
title: "just installed jaunty - how to install Kate text editor"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by sthapit on 2009-05-11
I just installed Jaunty and added the Kate text editor using Add/Remove Applications but it installed version 3.2.2.  

I need the "Filesystem Browser" which is only included in version 4.2 and above - how can I install the newer version? I went to [http://kate-editor.org/faq](http://kate-editor.org/faq) but couldn't figure out how.

---

### Post by ashmew2 on 2009-05-11
Hi , 

To get the .deb for kate , just go here : (It says version 4.2.2 )

[http://packages.ubuntu.com/jaunty/i386/kate/download](http://packages.ubuntu.com/jaunty/i386/kate/download)


Click your architecture and you can download the installation file.
Just tell me if you run into any more trouble ;)

---

### Post by sthapit on 2009-05-11
i went to the URL posted above and like it suggested I added a line to my /etc/apt/sources.list like this:

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jaunty main

I then did "sudo apt-get install kate" and when I check the version on my computer, I get this:

kate --v
Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
Kate: 3.2.2

Any other ideas?

---

### Post by ashmew2 on 2009-05-13
no no no..

You didnt have to add that to your sources.list

Scroll down a little below , youll see lots of Mirrors under different headings like Europe etc..Simply click one of them and you will download a .deb file ...Save it to desktop..Double click it..Install Package

---

