---
title: "tor for karmic, file permission issues"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Timi47 on 2009-11-19
im having trouble installing tor for ubuntu 9.10 karmic
i followed the [guide]("http://www.torproject.org/docs/debian.html.en") on the tor website and then moved on to the second [guide]("http://www.torproject.org/docs/tor-doc-unix.html.en#polipo") it sent me too. this is where i encountered my issues.

on step 2 i installed [SIZE=1]Polipo but when i tryed to change the config file i was denied access because it said i dont have permission to modify the file. 

my main issue is that i cant modify anything in the file system. is there anyway to gain access?
[/SIZE]

---

### Post by shadowlands on 2009-11-23
I am also having trouble and mine was working just fine but I had to reinstall it and it is not working.  Can some one please assist us?:popcorn:

---

### Post by camaron1 on 2009-11-23
> **Timi47 said:**
> im having trouble installing tor for ubuntu 9.10 karmic
i followed the [guide]("http://www.torproject.org/docs/debian.html.en") on the tor website and then moved on to the second [guide]("http://www.torproject.org/docs/tor-doc-unix.html.en#polipo") it sent me too. this is where i encountered my issues.

on step 2 i installed [SIZE=1]Polipo but when i tryed to change the config file i was denied access because it said i dont have permission to modify the file. 

my main issue is that i cant modify anything in the file system. is there anyway to gain access?
[/SIZE]
Don't know what the guide says but if you are trying to change a config. file for which you need root permission (seems to be the case here) you need to open a terminal and write 
> gksu gedit /(here the full name of the file or just drag and drop it)
Once you've given your password you have write permission over the file

---

### Post by camaron1 on 2009-11-23
> [SIZE=1]
my main issue is that i cant modify anything in the file system[/SIZE]

Just to further clarify: the whole file system is own by root so every time you want to change a file (any file) from the file system you have to open it as root (by doing what I have just told you for example)

---

