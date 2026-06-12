---
title: "How di I see  installed RAM in computer?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by sillyboy on 2009-09-09
I'm using 8.04.  Just added 1GB RAM to the 512 MB already installed.  How do I bring up what the computer is reading as what's installed?

Thanks

---

### Post by halitech on 2009-09-09
you can check when the computer turns on by looking in the BIOS or during memtest during POST and compare that to what shows up to the command in the terminal of
```
free -m
```

---

### Post by swoody on 2009-09-09
You can also go to System>Administration>System Monitor, and under the 'System' tab there is an entry there for your Memory :)

---

### Post by sillyboy on 2009-09-09
> **swoody said:**
> You can also go to System>Administration>System Monitor, and under the 'System' tab there is an entry there for your Memory :)

Thank You swoody and halitech! You are the best!

---

### Post by nandemonai on 2009-09-09
As a side note to this, you can see how much memory your system picks up on boot within BIOS.

---

### Post by relay_man on 2009-09-09
I like the command "top"  (don't enter the quotes)  :P

---

### Post by BobJam on 2009-09-10
There is also a nice GUI program called "Hardware Info" that will give you system information on just about everything . . . there is a memory section in it.

You can download it at [http://packages.ubuntu.com/hardy/i386/hardinfo/download](http://packages.ubuntu.com/hardy/i386/hardinfo/download)

or

[http://packages.ubuntu.com/hardy/hardinfo](http://packages.ubuntu.com/hardy/hardinfo)

---

### Post by expatCM on 2009-09-10
At some stage you may want to look at not only memory but also the rest of your hardware as well ...

The command 

sudo lshw

will generate a report on screen.

If you want to keep a file then simply expand the command to 

sudo lshw >hw.txt 

and a text file called hw.txt will be saved.

---

