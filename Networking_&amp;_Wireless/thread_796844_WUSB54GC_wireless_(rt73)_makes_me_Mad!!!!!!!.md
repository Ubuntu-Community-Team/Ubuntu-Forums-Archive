---
title: "WUSB54GC wireless (rt73) makes me Mad!!!!!!!"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by zouzou0 on 2008-05-16
hi everybody

i tried every post on this web i tried (fedora 6,7;suse 10.3;knoppix 5.0;kubuntu;Ubuntu 7.0.4) to get my rt73 linksys card to work in Monitor mode!!!!!!!!(i just want to test this this i spent over 4 days trying to do it)it's like i am stubborn to get it work just to prove myself.
know i am using Ubuntu 7.0.4 with kernel 2.6.20-15 generic  
i read all threads in the world:confused: not working and btw i am New to linux.

i downloaded the dirver from [http://www.ralinktech.com.tw/data/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0506_RT73_Linux_STA_Drv1.1.0.1.tar.bz2)

i installed it following these instructions
[http://wiki.archlinux.org/index.php/RT73_Wireless](http://wiki.archlinux.org/index.php/RT73_Wireless)

when i write in the terminal:
iwconfig rausb0 mode monitor
it says that : Error in wireless request "Set Mode"
                             invalid arrgument mod
plz i appreciate any help!!!!!

---

### Post by chili555 on 2008-05-16
What about:```
sudo iwconfig rausb0 mode monitor
```

---

### Post by zouzou0 on 2008-05-17
Thanks for the help
but finaly after the 4th day of hard working i found the solution :)!!!!!
it was the rt73 driver which i downloaded it didn't support monitoring mode so i searched for another one and this link worked fine [http://antirez.com/files/rt73-antirez-1.0.3.6-1.tar.gz](http://antirez.com/files/rt73-antirez-1.0.3.6-1.tar.gz) and i followed the instruction on this page  [http://antirez.com/page/rt73.html](http://antirez.com/page/rt73.html)

---

### Post by chili555 on 2008-05-17
Glad it's working. Thank you for posting your solution so the searchers can find it.

---

