---
title: "More Wireless Problems... : ("
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by Pxncture on 2007-01-02
](*,) 

More wireless problems, there seems a lot of them in these forums. So I'd like to say Hi to everybody.

Anyways, I've got an HP dv9100 currently running Kubuntu Edgy. I've had a few problems in the past, but was able to resolve them on my own. Now, I was going to follow the 
Broadcom tutorial here:

[http://www.ubuntuforums.com/showthread.php?t=197102&highlight=.%2Fndiswrapper_setup]("http://www.ubuntuforums.com/showthread.php?t=197102&highlight=.%2Fndiswrapper_setup")

but my adapter isn't even being recognized. 

Yup. The return of lspci is:

Network Controller: Broadcom Corporation Unknown Device 4311 (rev 01)

Now, my the card I do not believe is a 4318, I think its a 4400 something?. It's somewhere about there. Also, I dont know much about wireless cards as the 4400 may just be my driver, but considering how new of a laptop this is (still shiny), it would make sense to me. Any input is appreciated

---

### Post by ingo on 2007-01-03
The command lshw will give you a detailed output of your hardware. Once you have more precise info either get back to us or go for a more accurate search of the forum.

HTH

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

