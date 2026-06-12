---
title: "How to execute a .run file"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by fiddler63 on 2009-12-26
I have a something.run file.
When I double click on it, its opens up in gedit.
Right clicking gives me some options, but I cannot get this file to run.

File Location
[http://www.cadsoft.de/download.htm](http://www.cadsoft.de/download.htm)

Also when trying from the terminal with the suggested command, the file will not run.

What do I need to do ?

Kim

---

### Post by leef on 2009-12-26
Maybe you have to be root to run the file since it's installing software;

```
sudo sh eagle-lin-5.6.0.run
```

Let us know how this goes, Thanks.

---

### Post by fiddler63 on 2009-12-26
Maybe the file is corrupt
I get the following.

kim@kim-desktop:~$ sudo sh eagle-lin-5.6.0.run
[sudo] password for kim: 
sh: Can't open eagle-lin-5.6.0.run
kim@kim-desktop:~$ ^C
kim@kim-desktop:~$

---

### Post by fiddler63 on 2009-12-26
Doo

All I needed was to tick the box under file properties, permissions to allow the file to run as an executable

Kim

---

### Post by leef on 2009-12-26
Could be try using wget to download the file

```
wget ftp://ftp.cadsoft.de/eagle/program/5.6/eagle-lin-5.6.0.run
sh eagle-lin-5.6.0.run
```

I just ran the file without root and it seems to have installed fine but it did take a while before the installer showed up. I'm using 64 bit ubuntu 9.10.

---

