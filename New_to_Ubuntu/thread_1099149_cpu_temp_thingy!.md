---
title: "cpu temp thingy!"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-03-17
i downloaded this [http://www.gnome-look.org/content/show.php/CPU+Temperature+gDesklet?content=65252]("http://www.gnome-look.org/content/show.php/CPU+Temperature+gDesklet?content=65252") and i dont know how to put it to use! can someone help me? code? or instructions? thanx in advance!!!

OR you could give me a better/different program that reads in farenheight

---

### Post by BDNiner on 2009-03-17
The first thing you need to install is lm-sensors. It monitors almost all of the hardware sensors on your computer.

---

### Post by cirabisi2009 on 2009-03-17
mmhmm i did that before thinking it would just pop up ( silly me ). so whats next?

---

### Post by cirabisi2009 on 2009-03-17
??????????????????????????? no one knows what to do from there?

---

### Post by Botbob89 on 2009-03-17
I assume that when you downloaded it, it came with some commands you needed to run in terminal....have you done that? Any errors?

---

### Post by hockeyhead019 on 2009-03-17
have you installed gdeslets? if not then go to the add/remove and find the gdesklets... once you have installed that go to Applications->Accessories->gDesklets and run it... from there you will be able to select which ones you want to put on your desktop and you can just search whatever it is you wanted to install

---

### Post by cirabisi2009 on 2009-03-17
oh never mind. i dont feel like messing with it tonight :(

---

### Post by cirabisi2009 on 2009-03-17
> **hockeyhead019 said:**
> have you installed gdeslets? if not then go to the add/remove and find the gdesklets... once you have installed that go to Applications->Accessories->gDesklets and run it... from there you will be able to select which ones you want to put on your desktop and you can just search whatever it is you wanted to install

yeah i went through and did that but i cant get my HDD temp to work?!

---

### Post by Botbob89 on 2009-03-17
Did it install cleanly? Were there any error messages etc.?

---

### Post by hockeyhead019 on 2009-03-17
are you sure you have an HDD temp monitor? like physically do you know if your computer has a sensor to monitor that?

---

### Post by cirabisi2009 on 2009-03-17
im not sure. i have an acer aspire one. i figured it should be able.. if not then bummer. but everything installed smoothly and there were no errors

---

### Post by Botbob89 on 2009-03-17
Well assuming you DO have a temp monitor (I can't be bothered to find out for myself), the next stage is to check that any commands given with the package have been entered into the terminal successfully, to set up the package as necessary

(If that doesn't make sense I'm sorry, I'm tired :P)

---

### Post by cirabisi2009 on 2009-03-17
is there a cpu temp monitor that doesnt use gDesklet?

---

### Post by Dynaflow on 2009-03-18
> **cirabisi2009 said:**
> yeah i went through and did that but i cant get my HDD temp to work?!

The underlying program may be hddtemp.
```
sudo apt-get install hddtemp
```

---

### Post by Dynaflow on 2009-03-18
> **cirabisi2009 said:**
> is there a cpu temp monitor that doesnt use gDesklet?

I use the sensors-applet Gnome panel applet. You can see it in the upper panel of my posted desktop screenshot.  Install it through ```
sudo apt-get install sensors-applet
```

---

### Post by tjwoosta on 2009-03-18
i think i know why it isn't working

when you first install lm-sensors you will need to configure it

to configure do this from the terminal

```
sensors-detect
```

then answer any questions it asks and when finished reboot


> I use the sensors-applet Gnome panel applet. You can see it in the upper panel of my posted desktop screenshot. Install it through


```
sudo apt-get install sensors-applet
```



i also use sensors-applet

(even with sensors-applet you will still need to configure lm-sensors)

---

