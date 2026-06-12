---
title: "loading nvidia drivers reboots to black screen."
date: 2009-05-31
forum: New to Ubuntu
---

### Post by tactx on 2009-05-31
I could really use some help with this if anyone knows how to. I've been bashing my head against a wall for two days now.

My computer: Nvidia nForce 780i mainboard
             Intel Core2Duo processor
             2x Nvidia Geforce 8800 GTS graphics cards
             3x Optiquest monitors

Problem: I have had this rig functioning without issue in 8.04,but since
         I just installed 9.04 no matter what method I use to intall the nvidia drivers, when I reboot after the logo loads commands scroll down the page and after it says "checking batteries i get a blinking cursor and the a black screen.
         If I reboot is says "shutting down gnome display manager."

it doesn't this weather I use 32bit or 64 bit Ubuntu 9.04, or if I load the drivers using the restricted hardware drivers app or the envyng script the result is the same.

Again, any help on this will be much appreciated

---

### Post by Steelmourne on 2009-05-31
You might need drivers for your motherboard. Otherwise try manually install the newest drivers by logging out of gnome and bringing using a virtual console to install.

---

### Post by tactx on 2009-06-01
I've tried that...
I ran envyng from the from the prompt..dropping to bash at the login screen and I followed the method I found in a post using the driver from Nvida..stoping x server/gdm first..and Ive used the Jockey app..

every time the driver installs, but after reboot commands scroll across the screen until it says "checking batteries"...then noting but a blinking cursor..

Appearantly Gnome Display Manager(GDM) is running but not working.

---

### Post by tactx on 2009-06-01
Day three, no luck. If you know how to fix this please help. If it is a known issue...please let me know that as well.

---

### Post by tactx on 2009-06-01
I did a parallel install got things working and copied over the working xorg.config file.

now there still a small mouse issue to adress...but its working well so far.

---

### Post by mochiko on 2009-06-16
hi, i'm having this problem right now and i'm not sure how to fix it. I've been searching for a solution for about 4 days now and still can't get past this black screen with a cursor.

how would i find out which kind of driver i need to install?
or.. like how do i fix this problem ?!

---

