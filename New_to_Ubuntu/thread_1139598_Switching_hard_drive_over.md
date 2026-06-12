---
title: "Switching hard drive over"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by brewerdave on 2009-04-27
Have a strange problem with Ubuntu 8.10 on one PC - Can't seem to read/manipulate MP3 player thru USB ports(despite trying to follow advice in various posts-it won't mount).On another(older) pc I haven't got the problem.It automounts. As a consequence I want to switch hard drives over so that I keep all the music on the first system.Is Ubuntu installation tied to a motherboard/cpu combination(as per Windose) or can I swop drives like this without problems??

---

### Post by cariboo on 2009-04-27
Moving a hard drive from computer to computer is possible, the only thing you might have to do is change restricted drivers if the  video cards are different.

---

### Post by brewerdave on 2009-04-28
Thanks - I'll try swapping them over today!!Wish me luck.

---

### Post by ndefontenay on 2009-04-28
If you switch from linux to windows it won't read the linux partition...

If you switch a data only hard disk supported by your OS it will be seemless.

If you switch an OS from one PC to another, it could be trouble.

---

### Post by brewerdave on 2009-04-28
Switched hard drives over - both Ubuntu 8.10 - machine A now automounts the mp3 player - machine B won't; this suggests something to do with the USB controller on the m/board I'm presuming?
On the PC which won't mount MP3 player this is output of lsusb

Bus 002 Device 003: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I get exactly the same on the PC which does allow me to see/play the MP3 player.Starting to get frustrated!

---

### Post by card_ace on 2009-04-28
have you tried putting the MP3 in different USB ports?  kinda a dumb question but figured i'd ask anyway

---

### Post by brewerdave on 2009-04-28
Not dumb at all! But yes, I've tried all available USB 1.0 ports - I've come to the conclusion that the problem is to do with "modern" MP3 players (USB 2.0) NOT being truly backwards compatible with 1.0 standard motherboards. I can get 1 MP3 player to mount occasionally on one pc(but not every time!) ; the other one never automounts on either pc - last resort is to buy a PCI USB 2.0 CARD - Altho' I can't get any definite answers as to whether that'll work !!

---

### Post by brewerdave on 2009-04-28
PCI card worked - I can see and play the contents of both MP3 players using USB2.0 ports - obviously an issue with old(er) motherboards and USB1.0 ports.

---

