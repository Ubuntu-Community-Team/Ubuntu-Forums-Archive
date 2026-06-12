---
title: "Nvidia pci geforce fx 5500 128mb hides root folder?"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by xanxor on 2010-04-05
Hi i just got a really cheap (free) GPU a pny nvidia geforce fx 5500 128mb. i installed it and then booted up. but all that happened after grub loaded was the screen flashed twice and then said something along the lines of canout find root folder cannot mount root drive and then type help for commands... 
so i got on and got the 173' driver (which is the correct one) and alas it did the same thing again... does anybody know how to solve this problem? id really like to play my games.... 

specs 
2 gig memory 
pentium d processor
200 gig hd 
linux box. no windows

---

### Post by undecim on 2010-04-05
> **xanxor said:**
> i got on and got the 173' driver

How did you get on without a root folder? Did you reboot and it worked?

Sounds to me like you broke or disconnected something while installing the card. A video card can't hide a hard drive. Double check all connections to the hard drive and motherboard.

Although the fact that grub loaded at all indicates that your drive can still be accessed. Perhaps it's the power connector, or just a drive starting to die?

Either way, I don't believe this could possibly be related to the video card.

---

### Post by xanxor on 2010-04-05
drives fine after removing the card... i tried installing it many times. card works fine in my other machine too.

---

### Post by 3rdalbum on 2010-04-06
That's really odd, the graphics card shouldn't be causing this to happen.

When you have the card in, and you get dumped at the Busybox prompt (which is the thing you describe), wait about 30 seconds and type 'exit'. Your system might boot up now.

---

### Post by xanxor on 2010-04-10
that put busy box into panic mode or something

---

### Post by mgranet on 2010-04-11
How many watts is your power supply rated for?

---

