---
title: "wine for a usb camera"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Garthhh on 2010-07-11
I have an attachment for a microscope that drops in the eye piece
the cable plugs into usb port [USB PC Camera 301pc]
I installed wine from synaptic
I have the installation disc, 
have saved a copy, 
changed the exe permission, 
right clicked, opened with wine installation loader
let the wizard run
Unplugged & replugged as directed
no joy
have a printer & mouse, running through usb
where do I find the list of all hardware devices connected?

---

### Post by gandaran on 2010-07-11
drivers installed in wine don't work, in fact only some windows application can work in wine without problems, so if you cannot get your hardware to work in linux forget it it won't work in wine.

---

### Post by techunit on 2010-07-11
Why are you trying to use WINE again?

If you are trying to connect a USB microscope then you should see if it will start using an application called "Cheese"

```
sudo apt-get install cheese
```

if it works then you should see if anyone knows about a Microscope based application? I am sure one exists because of the open nature of linux and the fact that linux is quite common among Universities around the world.

---

### Post by Garthhh on 2010-07-11
> **techunit said:**
> Why are you trying to use WINE again?

If you are trying to connect a USB microscope then you should see if it will start using an application called "Cheese"

```
sudo apt-get install cheese
```if it works then you should see if anyone knows about a Microscope based application? I am sure one exists because of the open nature of linux and the fact that linux is quite common among Universities around the world.

Thanks, just the advice I needed
I wasn't asking the right question;)
I was having trouble classifying the device
Cheese [loaded it up from synaptic] worked fine, might as well be a web cam

This would have been the 1st application I would needed wine for dodged that bullet [whew]

---

### Post by Allu2 on 2010-07-11
You also might be interested in program called "motion". Which is a software motion detector, useful if you want to take photos on something that doesn't move all the time but some times. It hits the capture at right time and not after for example some water bug swim away from the sight of ocular, also if i remember right it can be monitored true web-browser :)

---

