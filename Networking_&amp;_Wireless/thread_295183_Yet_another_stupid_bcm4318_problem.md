---
title: "Yet another stupid bcm4318 problem"
date: 2006-11-07
forum: Networking &amp; Wireless
---

### Post by RevRogue on 2006-11-07
Well I have searched and searched but I still cannot find any solutions to my wireless problems, let me tell you what I got and what I have done and maybe someone can smack me around a bit and show the proper way to fix it. I have a HP z6209 AMD 64, Ubuntu 6.10 / Broadcom bcm 4318 airforce card. That pretty much sums it up. I have tried every tutorial I can get my hands on involving these such things and still no luck, ndiswrapper hasn't worked. Using 43xx wont work. I have attempted using kubuntu in hopes it was an OS issue and no such luck. I even tried putting in the disc and seeing if it would work using the disc b4 install. :( no luck on all accounts. The only other thing I can think of is finding a tutorial on writing my own drivers and trying to fix it that way but that is about as likely of happening as it is for me to fly. So please help anyone

---

### Post by K.Mandla on 2006-11-07
I used a zv6000 for a little while with a Broadcom chipset in it; I think it was a 4318, but I'm not 100 percent sure. 

The fwcutter method worked for me. I still have the wl_apsta.o file that did the trick. PM me if you want me to send it to you. It might be worth a shot.

---

