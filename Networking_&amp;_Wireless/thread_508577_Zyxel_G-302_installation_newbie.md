---
title: "Zyxel G-302 installation newbie"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Eto Samoe on 2007-07-24
Hey Everyone! Great Forum. I just switched to linux and so far I am impressed. Just 2 little problems I am having. I would appreciate any help. I followed some directions from earlier posts, but they did not help. Here's my issue. 

I have in my computer a pci zyxel g-302 wireless card. I cannot get the computer to recognize it for the life of me. I want it to work so I can get rid of this darn cable. I have read, and I even tries installing some ndwisripper thing, didn't work. Sorry to sound like such a noob, I am completely new to ubuntu. 

My other problem is my ati x300 graphics card. It works ok, and I installed the drivers along with some patches for it, but I still only get 1024x768 resolution. Is that as good as it gets? My monitor supports 1600x1200 resolution, so I would like to get that if I could . Thanks!

Eto Samoe

---

### Post by jdemarco on 2007-08-11
I have been trouble shooting the same card off and on for a couple days.

Can anyone verify that it is possible to install this card?

Zyxel g-302 v3

I installed ndiswrapper and then got the driver installed. When I run the command

ndiswrapper -l 

I get the output: driver installed device 10EC:8185 present.  (great right?)

The card is recognized in the device manager, but not under  network settings

When I try iwconfig i get:

 lo     no wireless extensions
 eth0 no wireless extensions (ethernet card)

I am not sure where to go from here. What do I do to wake this card up assuming ndiswrapper installed the driver correctly?

My sys is AMD 64

---

### Post by jdemarco on 2007-08-11
On further inspection

dmesg | grep ndiswrapper

...
...
ndiswrapper: kernal is 64-bit, but Windows driver is not 64-bit: bad magic: 10B

Unless I hear otherwise, I will assume there is no way to install this card on x64 at this time.

EDIT:

I wiped x64 and went to x86 and after installing the driver with ndiswrapper, the card is recognized, but every time I try to connect, it drops the connection.
I am ready to throw this card in the trash

---

