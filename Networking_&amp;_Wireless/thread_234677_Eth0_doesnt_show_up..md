---
title: "Eth0 doesnt show up."
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by offramp13 on 2006-08-11
I have an ASUS M2V motherboard. When i go to networking there is no eth0 option, there is just modem and wireless. I have come to assume that it is because i dont have the drivers installed for my motherboard. If anyone can help i would be very greatful.

---

### Post by drtvasudevan on 2006-08-11
there is a LAN card or not?
how do you connect to internet?

---

### Post by offramp13 on 2006-08-11
I guess i neglected to mention that there is integrated gigabit LAN on the motherboard. I have a PCI wireless card i can use to get online, but i'd like to get the ethernet working.

---

### Post by drtvasudevan on 2006-08-12
then there must be an eth0.
i guess your hardware did not get properly configured.
did you face any problem in installation.
teh solution is beyond me as i am a newbie as well.

---

### Post by avanderbergh on 2006-08-15
Hi.

I also had the same problem. The On-Board Gigabit LAN is not yet supported in the kernal. but you can download the driver source from Asus website.

The driver module compiled without any problem and the module works fine.

I did however notice that my upload speeds are really slow, this might be an issue with the driver module

The driver is not yet production ready so I guess errors can be expected. Anyone know how long before the next kernal upgrade so this card can be supported?

---

### Post by offramp13 on 2006-08-20
I tried to install this but it didnt work, i downloaded the linux-lan drivers for my motherboard, and everything went fine, then i ran
```
cd /home/charlie/Desktop/Linux_Lan/src
sudo make install
```
and then it gave me the following error.
```
Makefile:65: *** Linux kernel source not found.  Stop.
```
I don't know if i did something wrong or what. but i followed the instructions. Thanks if anyone can help.

---

### Post by Fass on 2006-08-21
```
sudo aptitude install linux-headers-`uname -r`
```

That should be what you need to fix the compile error.

---

### Post by tuxcantfly on 2006-08-21
did you try doing sudo ifup eth0?

---

### Post by offramp13 on 2006-08-21
I did this:

> **Fass said:**
> ```
sudo aptitude install linux-headers-`uname -r`
```

That should be what you need to fix the compile error.

and then ran sudo make install and it did its stuff. but its still not recognized

---

### Post by Fass on 2006-08-21
> **offramp13 said:**
> and then ran sudo make install and it did its stuff. but its still not recognized

Did you modprobe the module? What did dmesg say afterwards? Sometimes, and I don't know why, you have to add the module to /etc/modules and reboot for these things to work their magic.

---

### Post by avanderbergh on 2006-08-24
Hi,

After compiling the module you should run the following command:
```
sudo modprobe atl1
```

This should load the module.

---

### Post by offramp13 on 2006-08-26
Thank you very much both avanderbergh and Fass. It is working now and i am happy,

---

