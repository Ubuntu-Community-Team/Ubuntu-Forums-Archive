---
title: "download.virtualbox.org down?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-04-28
Does anyone have a copy of the latest Virtualbox for karmic?

Can't seem to get hold of a copy from there website *Sigh*

---

### Post by sadaruwan12 on 2010-04-28
Try this [Click Me]("http://dlc-cdn-rd.sun.com/c1/virtualbox/3.1.6/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb?e=1272477047&h=ebe1af7d54305b10290fdcf7aec70994")

---

### Post by tom.swartz07 on 2010-04-28
> **kamitsukai said:**
> Does anyone have a copy of the latest Virtualbox for karmic?

Can't seem to get hold of a copy from there website *Sigh*

386 or x64 version? I got em

PS- Totoro is so cool. I always wanted a cat-bus.

---

### Post by kamitsukai on 2010-04-28
> **tom.swartz07 said:**
> 386 or x64 version? I got em

PS- Totoro is so cool. I always wanted a cat-bus.

yer I love Studio Ghibli films:lolflag:

if I could have the i386 deb please:popcorn:

---

### Post by aysiu on 2010-04-28
VirtualBox is in the (Universe) repositories. You don't need to download it separately.

Use Applications > Ubuntu Software Center or System > Administration > Synaptic Package Manager to install it.

---

### Post by tom.swartz07 on 2010-04-28
> **aysiu said:**
> VirtualBox is in the (Universe) repositories. You don't need to download it separately.

Use Applications > Ubuntu Software Center or System > Administration > Synaptic Package Manager to install it.

I believe that the OP is looking for the non-free version. This one has USB support that is not available in the OSE version from the software center.

I sent a link in PM to you, you should have it as soon as the file is uploaded! I have it hosted on my site. 


Also, Ponyo is a work of art! :D
Glad to help!

---

### Post by kamitsukai on 2010-04-28
> **aysiu said:**
> VirtualBox is in the (Universe) repositories. You don't need to download it separately.

Use Applications > Ubuntu Software Center or System > Administration > Synaptic Package Manager to install it.

I want the latest release with usb support =]

---

### Post by kamitsukai on 2010-04-28
> **tom.swartz07 said:**
> I believe that the OP is looking for the non-free version. This one has USB support that is not available in the OSE version from the software center.

I sent a link in PM to you, you should have it as soon as the file is uploaded! I have it hosted on my site. 


Also, Ponyo is a work of art! :D
Glad to help!

Thanks very much:guitar:

I haven't seen Ponyo yet:KS I will have to check it out!

---

### Post by aysiu on 2010-04-28
> **kamitsukai said:**
> I want the latest release with usb support =]
Hm. It's working for me.

Can you try using *wget* instead of a web browser? ```
wget -c http://download.virtualbox.org/virtualbox/3.1.6/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb
sudo dpkg -i virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb
```

---

### Post by kamitsukai on 2010-04-28
> **aysiu said:**
> Hm. It's working for me.

Can you try using *wget* instead of a web browser? ```
wget -c http://download.virtualbox.org/virtualbox/3.1.6/virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb
sudo dpkg -i virtualbox-3.1_3.1.6-59338_Ubuntu_karmic_i386.deb
```

yes it appears to back up now...sods law really isn't it:lolflag:

---

