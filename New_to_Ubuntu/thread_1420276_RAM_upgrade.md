---
title: "RAM upgrade"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by saintnefarious on 2010-03-02
I am thinking of upgrading th RAM on my Advent 4211 (msi u100) which is running jaunty. will it make any difference that im running linux? do i have to do anything different? or is it just as simple to do as for windows?

---

### Post by nerdy_kid on 2010-03-02
just as simple as it is for windows :)

---

### Post by delectate on 2010-03-02
take it easy,nothing different

---

### Post by abdullahajj on 2010-03-02
Simple is a relative term...  You try upgrading the RAM on a Dell Mini 10v without frying the motherboard...  jk, but yeah as stated above.  Same procedure.  Software has nothing to do with hardware, other than making sure they're compatible.

---

### Post by saintnefarious on 2010-03-02
thanks everyone just making sure!!:D

---

### Post by CBR_Rob on 2010-03-02
I've got a quick ram question. In Vista my laptop sees all 4 gigs of ram. With the 64 bit 9.10 my laptop only sees 3.5 gigs of ram. Is there anyway to make Ubuntu see all my ram?

---

### Post by delectate on 2010-03-02
it seems you have to use 64-bits kernel

or compile kernel yourself?

---

### Post by CBR_Rob on 2010-03-02
Please bear with me on this question I've only got ~10 hours playing with Ubuntu coming from Windows but how would I find out if I've got the 64 bit kernel? I did download the AMD64 install dvd image.

---

### Post by Robster2 on 2010-03-02
> **CBR_Rob said:**
> Please bear with me on this question I've only got ~10 hours playing with Ubuntu coming from Windows but how would I find out if I've got the 64 bit kernel? I did download the AMD64 install dvd image.

In the terminal

```
uname -m
```

If it says "x86_64", then you're using 64-bit Ubuntu.  That includes the Kernel.

```
sudo apt-get install sysinfo
```

```
sysinfo
```  Will give you more information in a GUI.

---

