---
title: "3com 3C509 ISA ether card working"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by dk1138 on 2007-10-25
I installed Xubuntu 7.10 on my Amd K6-233 pc with 64 megs of ram. I had two issues. First was with serial mouse not working. Fix was "sudo dpkg reconfigure xserver--xorg" Then got to mouse setting and had to select the com port tty0. xubuntu had detected it as a ps2 mouse.

The bigger issue was my 3com ISA 3C509 ether card xubuntu did not find it an there was no way to set it up from the network manager I searched the net  for two days and saw a suggestion from another page on the ubuntu forms to try the following command from the terminal "sudo modprobe 3c509" it thought for a second and then all of a sudden my router port lit up and I had a connection to the net. It was also now active in the network manager.

So if you have this card you just might want to give this a try. It work for me but each pc is different so you millage may very or maybe try the command with you model of eather card and see if it works. Now my next step is to find how to add this to boot so i dont have to type it every time i use xubuntu.

I am very new to Linux I just loaded Puppylinux 3.0 three weeks ago (my first ever Linux)and Xubuntu 2 days ago been doing alot of reading and hair pulling but it is coming along an I will get the hang of this.

Hope this will help somone else out

PS: anyone know where to get EDO memory:)

---

