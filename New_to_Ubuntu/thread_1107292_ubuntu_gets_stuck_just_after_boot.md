---
title: "ubuntu gets stuck just after boot"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by marco v. on 2009-03-26
Hi there!
I've just installed ubuntu 8.10 in safe graphic mode.I first tried to install in normal mode but it failed.
The installation went through but when I restarted the system the desktop just faded in weird colours and the computer just stopped working. I switched the power off manually and then rebooted the system: ubuntu was loaded but no log in window, just  a blurry motionless screen.
I've been browsing around your and other forums and it could be a crash with the graphic card(VIA S3).
Thanx for grea:confusedt support,
marco

---

### Post by jerrrys on 2009-03-26
how bout some more info...
whats your system specs?
how fail? what error msg?
are you using live cd?

lets start there...and hay...welcome to ubuntu

---

### Post by marco v. on 2009-03-27
Thank for this reply
 I bought a dvd of ubuntu 8.10 from a cd burner supplier.I have a sansui laptop with 1.8 Gb Amd cpu and 512 Mb ram
GRUB did not show any error msg. when I installed ubuntu for the first time in normal mode it got stuck at the first installation window, it was just blank and I could take no action. Then I redid the boot in safe graphic mode and the insalllation went through but at the restart my screen just screwed up.Just tell me if you need more info!

---

### Post by jerrrys on 2009-03-27
first off, i use intel, amd has different things happening on install..but even at that, sounds like your not using the live cd...on the live cd all you got to do is answer a few questions and your up and running, no safe boot required..please to check this out..i dont download OS cd/dvd because its easer to just spend 2usd and be done with it [http://www.osdisc.com/cgi-bin/view.cgi/products/linux](http://www.osdisc.com/cgi-bin/view.cgi/products/linux) ...

second im not a fan of 8.10...its just easy to start with 8.04, its proven long term support

i do have 810/kde on mine, but it just seems to be a work in progress and not something i want to trust, at least not yet...

im just throwing this at ya....let me know your thoughts...

---

### Post by stderr on 2009-03-27
Please verify that you can, once Ubuntu's loaded, do Ctrl+Alt+F1 to switch to a terminal. From there you should be able to log in with your username and password. 

Then, please attempt to start an x session by typing:

```
startx
``` 

and hit enter. If you get any error messages, please post them here. They may help us debug.

---

### Post by marco v. on 2009-03-28
Thanx for your help!
I ran the live cd mode(in safe graphic mode) and this warning message popped up: Ubuntu is running in low graphic mode and csnnot recognise the graphic card. My graphic card support a Via S3 chipset
when I ran ubuntu live cd this msg appears:error 8254 timer not connected to I/O aptec.
Hope this info are useful!

---

