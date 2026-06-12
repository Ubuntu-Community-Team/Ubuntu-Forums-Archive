---
title: "Problem with PS/2 Mouse"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by Aamir Aziz on 2009-03-09
i have PS/2 Mouse connected with my computer. whenever i run any Linux, it does not work. I have tested "OpenSuse", "Ubuntu 8.04", "Mepis" & "Debian 4". Now i am using "Debian 4" but don' t know that how do i run my PS/2 mouse on it.

---

### Post by PukingPenguin on 2009-03-09
Likely a hardware issue. I have several ps2 mice connected to several Linuces from Ubu, Debian 3/4/5, Mepis, etc., all the way back to redHat 7.2. Never had a detection issue.

---

### Post by bailbath on 2009-03-09
Can you tell us which mouse you have?
Ian

---

### Post by LowSky on 2009-03-09
We really need t know more about your PC and the mouse in question, please as much detail as possible

---

### Post by Aamir Aziz on 2009-03-09
> **LowSky said:**
> We really need t know more about your PC and the mouse in question, please as much detail as possible

Mouse

Compaq
Model Number: M.S69


PC

IBM 
Intel Pentium 4
main Board Model: MT-M 8315-42U

---

### Post by Aamir Aziz on 2009-03-09
> **bailbath said:**
> Can you tell us which mouse you have?
Ian

Mouse

Compaq
wheel Mouse
Model Number: M.S69


PC

IBM NetVista
Intel Pentium 4
main Board Model: MT-M 8315-42U

---

### Post by LowSky on 2009-03-09
[http://ubuntuforums.org/showthread.php?t=186689](http://ubuntuforums.org/showthread.php?t=186689)

OK during boot, go into the BIOS settings, look for USB legacy support, or see if PS/2 is enabled, sometimes it is not

otherwise did you know a USB mouse can be purchased for under $10USD
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010290065+4024+1083407048&Configurator=&Subcategory=65&description=&Ntk=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010290065+4024+1083407048&Configurator=&Subcategory=65&description=&Ntk=&SpeTabStoreType=&srchInDesc=)

---

### Post by amor0fati on 2009-05-06
After upgrading from jaunty 11 to 12, I lost the use of my mouse in ps/2 but not in usb on my main drive.  Going from Intrepid  to Jaunty on my backup drive, I lost ps/2 but had usb until a reboot.  My keyboard is ps/2 and works fine on both.  In my situation, it is preferrable to be able to use ps/2, rather than usb; I am short on usb ports and my mouse seems to jump a lot in usb.  My mouse is a logitech mx laser.

---

### Post by amor0fati on 2009-05-07
I mostly sorted it out with
```
sudo gedit /etc/rc.local
```
then typed in
```
modprobe -r psmouse
modprobe psmouse proto=imps
```
before the exit 0 line.

However, this did not work on my backup harddrive, and now my pointer moves all the way to the left of my main screen when I move it to the second screen to the right.  What's going on here?

---

### Post by SunnyRabbiera on 2009-05-07
Unknown, is this one of those crazy multi button (as in more then 4) mice?
If its a standard PS/2 2/3 button mouse this is very unusual, Linux can handle any brand of that kind of mouse.
Is it a laser mouse or an older trackball?

---

### Post by amor0fati on 2009-05-07
It is a multi-button laser mouse.  It's a USB mouse by default but has always worked fine with a ps/2 adapter until a partial upgrade was performed in jaunty.

I can't get it to do what it was doing before when it kept jumping across the screen.  Now it just sticks in place where it crosses the barrier between screens (I can see it on the other screen as well when this happens) like it's done ever since I upgraded to jaunty.  This is very annoying in itself.

---

