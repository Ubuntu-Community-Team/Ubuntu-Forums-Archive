---
title: "Help me"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Linguist99 on 2009-06-19
Hi how can i instal gnome ppp on ubuntu 9.04 which packages do I need to install what I have to do and where can I download gnome ppp?

---

### Post by TJCIB on 2009-06-19
sudo apt-get install gnome-ppp

---

### Post by philinux on 2009-06-19
System>admin>synaptic package manager

Or in firefox web browser address bar.

apt://gnome-ppp

---

### Post by Sealbhach on 2009-06-19
Assuming the guy has an internet connection.

If you need to manually download the debs and install them via a USB stick, you will need these packages:

gnome-ppp 
libuniconf4.4 
libwvstreams4.4-base 
libwvstreams4.4-extras 
libxplc0.3.13 
wvdial

Install them in this order:

libxplc0.3.13 (0.3.13-1build1 Ubuntu:9.04/jaunty)
libwvstreams4.4-base (4.4.1-0.2ubuntu2 Ubuntu:9.04/jaunty)
libwvstreams4.4-extras (4.4.1-0.2ubuntu2 Ubuntu:9.04/jaunty)
libuniconf4.4 (4.4.1-0.2ubuntu2 Ubuntu:9.04/jaunty)
wvdial (1.60.1+nmu2 Ubuntu:9.04/jaunty)
gnome-ppp (0.3.23-1 Ubuntu:9.04/jaunty)

You can get the packages here:

[http://packages.ubuntu.com/jaunty/gnome-ppp](http://packages.ubuntu.com/jaunty/gnome-ppp)

.

---

### Post by NightwishFan on 2009-06-19
You can also use this command:

```
sudo dpkg -i drag and drop the deb files here
```


I also have my main PC without a current connection, I have found the easiest way to get all the stuff you want is to install WUBI on a PC that does, then do a 'download only' on all the packages you want using synaptic, and use Aptoncd to make a DVD with all of them.

If you have a connection, then just use synaptic, or run the command:

```
sudo apt-get update && sudo apt-get install gnome-ppp
```

---

