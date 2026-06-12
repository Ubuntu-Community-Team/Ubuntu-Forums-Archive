---
title: "how to install???"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by freezashu on 2009-01-25
i've downloaded a graphics driver for my mother board... plese help me to instal it... please tel me by clickin what i can start installin like setup in windows

---

### Post by taurus on 2009-01-25
What is the name of that file?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

p.s.  Say this three times, "Linux is not windows..."

---

### Post by freezashu on 2009-01-25
i hav download a folder... many files r thr in it...... by clickin which i can instal it???????? help me

---

### Post by taurus on 2009-01-25
What kind of graphic card do you have?  Run this command from a terminal and post the output here.

```
lspci | grep VGA
```

Otherwise, look in System -> Administration -> Hardware Drivers to see if your card is on the list.

---

### Post by llamabr on 2009-01-25
One of the benefits of your new OS is that you no longer usually have to go out into the internet to find drivers, figure out how to install them, etc.  The video on your mother board is very likely already supported.

What problems are you having?

---

### Post by freezashu on 2009-01-25
when i go hardware driver it comes as..."no proprietary drivers are use in this system" wht does it mean??????? i'm wishin to install my globespanvirata usb modem too... how can i do it...

---

### Post by freezashu on 2009-01-25
when that comment is given "00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)" i get this reply

---

### Post by taurus on 2009-01-25
Until you tell people what kind of video card do you have and the names of those files that you've downloaded, I don't think anybody can show you how to install a driver for your graphic card.  People here can help but they are not psychics!

---

### Post by freezashu on 2009-01-25
my graphics is inbuilt... how to c if its driver is installed??????

---

