---
title: "wireless usb"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by olgeaser on 2010-12-18
newbie with low linux IQ cannot get wireless usb adapter to work in ubuntu 10.10.. The adapter is made by Belkin  ..Surf & Share

thanks..

---

### Post by Old_Grey_Wolf on 2010-12-18
The easiest way I have found to get wireless adapters working is with ndisgtk. It is a graphical front end for setting up ndiswrapper. You can install it by going to the Applications > Ubuntu Software Center and entering 'windows wireless drivers' in the search box. When you start it, it will allow you to install a driver for your wireless adapter and set up the network. If you have the CD that came with the wireless adapter you can search the CD for the .inf files; which are the drivers. There may be more than one .inf file so you may have to try each one until you find the one that works. If you do not have the CD, you can download the drivers from Belkin's website.

---

### Post by matt-fender on 2010-12-18
ndis is the way to go unless wireless works OOTB,

if ndis won't work punch this into a terminal

```
sudo lshw -C network
```

---

### Post by Old_Grey_Wolf on 2010-12-18
> **matt-fender said:**
> ndis is the way to go unless wireless works OOTB,

if ndis won't work punch this into a terminal

```
sudo lshw -C network
```

Then do what with the output of that command? I assume you want the original poster to post it here so that people can help? :)

---

### Post by matt-fender on 2010-12-19
Of course, silly me! 2 days of not sleeping catching up right there ;)

---

