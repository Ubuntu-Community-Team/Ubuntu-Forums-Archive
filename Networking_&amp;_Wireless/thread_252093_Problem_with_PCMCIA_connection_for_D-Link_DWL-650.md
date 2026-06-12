---
title: "Problem with PCMCIA connection for D-Link DWL-650"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Tritan on 2006-09-06
Hello,

first off - I am new to Linux in general so I am somewhat of a noob ;)

I`ve recently been looking for alternatives for my slow XP-laptop, so I have tried some distro live cd`s. Ubuntu seems to be best for now, so I am trying to install all the systems components. All works perfectly, except for my WiFi-card. I`ve messed around a bit with ndiswrapper, but didn`t get me any further. I`ve did a fresh install of Ubuntu just to make sure I get no conflicts when installing the Linux Driverloader. I can load drivers here, but the app says there is a problem with the connection to my PCMCIA-card. 

I haven`t found alot of usefull info on google about people using my card, except for statements that others deny (like for instance faulty D-Link drivers which .inf is incorrect?) or different statements on it`s chipset.

Driverloader now suggest looking into the kernelmessages, but I don`t really see any problems in there, I see a message saying a PCMCIA device is being registered as "pcmcia0.0", and that it`s availible in slot1 (which seems correct). PCMCIA doesn`t get mentioned any further, neither does wlan0.

_Where do I have to look to solve my problem?_

My specs:

HP Pavillion ze4610us
D-Link DWL-650 rev P.
Ubuntu 6.06 LTS

Thanks in advance!! :D

---

### Post by tturrisi on 2006-09-06
Your card has a prism 3 chipset and the drivers for it come w/ Ubuntu already.  The problem w/ that card is that it is basically a serial flash device that does not have any onboard firmware. afaik the card is not supported.  You would have to install firmware for the card.

---

### Post by Tritan on 2006-09-07
I see. Where can I find more information about this, and are you confident I do have a prism3?

Is it worth looking into such a solution, or does it only work partially or so?

Thanks again :KS

---

### Post by tturrisi on 2006-09-07
[http://www.google.com/search?hl=en&lr=&q=ubuntu+prism3&btnG=Search](http://www.google.com/search?hl=en&lr=&q=ubuntu+prism3&btnG=Search)

---

### Post by Tritan on 2006-09-08
Does anyone know how to enable the loading of the driver when Ubuntu starts? It seems I have to run `sudo modprobe ndiswrapper` everytime I boot now :-| 

Thanks.

---

### Post by BenTyreman on 2006-09-08
Add "ndiswrapper" to /etc/modules:
```
sudo -s
echo "ndiswrapper" >> /etc/modules
exit
```

Alternatively, running ```
sudo ndiswrapper -m
``` should cause ndiswrapper to be loaded when your network card is loaded. Have you blacklisted the prism driver? If you using ndiswrapper, this might be beneficial.

---

### Post by ymeng on 2006-10-19
I wonder if Tritan ever got the card work? Did you install firmware for your card as tturrisi suggested? How???

I tried to google on "ubuntu prism3", then followed some links, but nothing panned out. You can see the detail of my endever from my post [http://ubuntuforums.org/showthread.php?t=280590&highlight=dwl+650](http://ubuntuforums.org/showthread.php?t=280590&highlight=dwl+650)

---

