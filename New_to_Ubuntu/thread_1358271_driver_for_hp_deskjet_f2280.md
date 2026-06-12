---
title: "driver for hp deskjet f2280"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Adele74 on 2009-12-18
I have ubuntu. And I need driver for my hp deskjet f2280.
can anybody help me. very urgent. It for x-mas presents :)
And I know nothing about this. I didnt install ubuntu on my machine

PLEASE HELP.

---

### Post by hansdown on 2009-12-18
Hi Adele74.

The default ubuntu install should include the HPLIP package, which means, that installing the printer is as simple as plugging it in, and turning on the power.

---

### Post by Adele74 on 2009-12-18
No tried that..... doesnt work,still :(

---

### Post by ajgreeny on 2009-12-18
It should work without a problem; I have the similar F2180, and with hplip and the hplip-gui it works as good as it would on windows.

What version of ubuntu are you running, and are you sure that the printer usb cable is OK?

The next thing to do is run ```
lsusb
``` in terminal and see if the printer is even seen by the system, and report back here the output, which should show something like this:-
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:7d04 Hewlett-Packard Deskjet F2100 Printer series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Adele74 on 2009-12-18
> **ajgreeny said:**
> It should work without a problem; I have the similar F2180, and with hplip and the hplip-gui it works as good as it would on windows.

What version of ubuntu are you running, and are you sure that the printer usb cable is OK?

The next thing to do is run ```
lsusb
``` in terminal and see if the printer is even seen by the system, and report back here the output, which should show something like this:-

The cable is just fine. Used just e feew weeks ago.
I have the unbuntu 9.10
Dont under stand the rest you wrote. Have to explain as if to a kid.know nothing about this

---

### Post by Adele74 on 2009-12-18
I know how to get in to the terminal thing but what was that sign that you wrote before susb?

---

### Post by philinux on 2009-12-18
> **Adele74 said:**
> I know how to get in to the terminal thing but what was that sign that you wrote before susb?

Apps>accessories>Terminal

A little L

```
lsusb
```

---

### Post by kansasnoob on 2009-12-18
I have an F2210 which is same series:

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html)

All I had to do was install hplip-gui (I also use flegita which is the gnome scan frontend):

```
sudo apt-get install hplip-gui flegita
```

Then I just turn on the printer and it's found, I then go to System > Preferences > HPLIP Toolbox and there it is:

[ATTACH]140425[/ATTACH]

As I said I prefer using the Flegita Scan Utility, you'll find it in Applications > Graphics.

---

### Post by Adele74 on 2009-12-18
ha ha ha ha ohhh yes....... it WORKED.
Thank you guys :)
You saved my x-mas......
THANK YOU, THANK YOU, THANK YOU

---

### Post by lavinog on 2009-12-18
> **Adele74 said:**
> ha ha ha ha ohhh yes....... it WORKED.
Thank you guys :)
You saved my x-mas......
THANK YOU, THANK YOU, THANK YOU

What did you do to get it to work?

---

### Post by Adele74 on 2009-12-18
I installed hplip gui and than just put the cable from the printer to the comp. and it worked...
At least I think thats what I did he he he.....
joking thats what I did..And I couldn't have done it without the help from you guys

_**[COLOR=Red]Have a very merry x-mas[/COLOR]**_

---

### Post by ajgreeny on 2009-12-18
Interesting!  It should still have worked without the hplip-gui, but would have been much more difficult to monitor what was going on, and how much ink was left etc etc.

hplip on its own provides all that is needed for it to print.

---

### Post by Adele74 on 2009-12-18
I have to say : I realy dont know. 
But It works and Im[COLOR=Blue]_ happy happy happ__y_[/COLOR].

---

