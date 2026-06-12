---
title: "Ubuntu 10.10 freezes after some 2-3 mins ..."
date: 2010-12-01
forum: New to Ubuntu
---

### Post by vizkid2005 on 2010-12-01
Hi everyone ... 
I am very new to using ubuntu ... 
I downloaded ubuntu 10.10 64 bit ...

My problem is that when I boot up ubuntu , After 2 -3 mins(regularly) the system freezes ... It happens irrespective of what task I am doing ... It happens after every boot up ... Neither the mouse nor the keyboard works ... I can`t even toggle Num lock on\off ... Then I have to reboot to again encounter the same problem ....

I had encountered the same problem when I booted using Live CD also ... In that case also the system froze ...  

I have an i5 760 based system ... Graphic card is XFX HD 4350 ... I couldn`t install the drivers because the freeze up doesn`t give me time to do it ...  

Please help me ... 
Thank You ...

---

### Post by cariboo on 2010-12-01
Have you tried installing the graphics driver form the command line? Boot into recovery mode and once at the menu, select netroot using the arrow keys. Once at the prompt, type:

```
jockey-text -l
```

The above command will list the recommended driver for your graphics card. To install it type:

```
sudo jockey-text -e <driver>
```

Where <driver> = the driver suggested by the first command.

---

