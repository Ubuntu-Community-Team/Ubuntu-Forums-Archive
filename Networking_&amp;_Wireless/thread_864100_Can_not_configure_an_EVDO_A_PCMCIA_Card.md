---
title: "Can not configure an EVDO A PCMCIA Card"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by ahsaeed on 2008-07-19
Hi every one ..
mmm .. ok . i have a little problem .. i have a Pantech PX-100 EVDO A PCMCIA Card.. i can't configure it in my computer.. i'm using ubuntu 7.10
i tried :
*$ modprobe usbserial vendor=0x---- product=0x-----*
and i put the right numbers in the spaces above.. but noting changed
pleaaaaaaaaaaaaaaaaaaase help.

---

### Post by Mach1US on 2008-07-22
Just updated my how-to so this should be an easy setup .

[http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://ubuntuforums.org/showthread.php?t=343989&highlight=evdo)

---

### Post by ahsaeed on 2008-08-01
Hey thank you for help! 
yeah I noticed that it is the same problem just in different words heheheh...!
mmm .. and another thing I have solved it in another way it is easier..
just write in terminal 


~$lsusb
~$ modprobe usbserial vendor=xxxx product=xxxx


then in Kppp configure your connection password and user name  and let the device to be /dev/ttyusb(x) /* the number x is from 0 to 3 I think it's differ from computer to another

then.... enjoy 
thanks again :lolflag::guitar::)

---

