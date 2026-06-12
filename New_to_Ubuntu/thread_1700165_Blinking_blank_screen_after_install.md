---
title: "Blinking blank screen after install"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by AdrianV on 2011-03-04
I actually have a new problem... i did the install using the whole hard drive... i have a 250 hard drive so i partitioned it into 4 groups..

5g designated /
100 gigs /home
140 gigs /user
5g swap

(im not sure if this is good or bad, but i had no idea so i just did that)

anyways, after installing (asked me for time zone, name, password, and took time til everything was done), it asked me to restart to finalize installation.

when i restarted my laptop... the usual HP screen with the escape F2, F9, F10 etc came up then went blank with a blinking cursor on the top upper left corner.. and nothing else happened... so now my laptop is windows free.. but apparently Ubuntu isn't loading either... 

so i took the USB pendrive again, and looked at it said that dev1 has Ubuntu 10.10 installed in it.. but i dont know why it wouldn't load.

thanks for the help!

---

### Post by davidmohammed on 2011-03-04
press and hold the shift key when your computer starts.  This will display your grub.

Press e to edit the kernel.

Find the line ending with "quiet splash" - add the text "nomodeset" before this i.e. so it reads "... nomodeset quiet splash"

press CTRL +X to boot.

If this doesnt work repeat with the options

i915.modeset=1

or

i915.modeset=0

instead of "nomodeset"

---

### Post by maqtanim on 2011-03-04
Your root partition is really very small! You should use atleast 10 GB. Here is my how to partition the HDD:
20 GB for root (/)
2 GB for swap 
Rest of the space for /home

Well.. now come to the point. When you used CD or USB, you have changed the boot priority to CD/USB. Did you still have the HDD in your priority list? Another thing, Did the live cd works? I mean did you able to run ubuntu from the CD without installation?

---

