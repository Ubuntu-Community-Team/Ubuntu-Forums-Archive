---
title: "how do I find out what mother board I have?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by kapi on 2009-07-29
Is there a way for me to locate what type of mother board I possess so as to order the correct type of ram.

I know crucial do an online scan but it appears only to be for windows not linux

any suggestion please


thanks

---

### Post by TeoBigusGeekus on 2009-07-29
```
sudo lshw > /home/username/Desktop/sys.info
```
It will save your system info in a file on your desktop.

---

### Post by philinux on 2009-07-29
If you want a nice gui install lshw-gtk and run it with 

```
gksudo lshw-gtk
```

---

### Post by Copernicus1234 on 2009-07-29
> **philinux said:**
> If you want a nice gui install lshw-gtk and run it with 

```
gksudo lshw-gtk
```

I tried the GUI. God it sucks. :)

Someone should make a better one.

---

### Post by doas777 on 2009-07-29
> **Copernicus1234 said:**
> I tried the GUI. God it sucks. :)

Someone should make a better one.

yes, it was obviously a mac person that wrote it.

---

### Post by jerrrys on 2009-07-29
try this

[http://www.newegg.com/Product/ProductConfigurator.aspx?plf=10&category=17&name=Memory-Configurator](http://www.newegg.com/Product/ProductConfigurator.aspx?plf=10&category=17&name=Memory-Configurator)

---

### Post by credobyte on 2009-07-29
hardinfo - all time fav :p

---

### Post by CaptainMark on 2009-07-29
Just open up your machine and have a gander

---

### Post by irv on 2009-07-29
> **Copernicus1234 said:**
> I tried the GUI. God it sucks. :)

Someone should make a better one.

It sure does!!!!

---

### Post by kapi on 2009-07-29
Thanks guys - In the end I just grabbed the serial number at boot up and did a search online, took me a few minutes, then found the maximum spec on ram for the board.

did that years ago for windows, don't know why I forgot how to do it.

Thanks again

---

### Post by philcamlin on 2009-07-29
good to see you found what you were looking for :popcorn:

---

