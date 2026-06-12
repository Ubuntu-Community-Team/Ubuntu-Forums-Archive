---
title: "Senao USB Wifi device &amp; Ndiswrapper, newbie has no clue"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by qzonk on 2007-06-30
Hey all, hope someone can help,

i have allready followed several threads to get NDISwrapper to take up my 
.inf windows drivers, but from there i get zero results, and unplugging the device 
aint good for the ndiswrapper process, (how do i stop it?) 

Can anybody give me a little more help on getting my 
Feisty to work with my Wireless adapter?

Thanx
Newbie

---

### Post by kevdog on 2007-06-30
Lets just start at the beginning.  I need to know more about your wireless device.  At command line type the following and cut and paste the output:

lsusb

If you have installed ndiswrapper, lets just check the installation to see if its installed properly:
ndiswrapper -v 
ndiswrapper -l

Thanks

---

### Post by qzonk on 2007-06-30
Its a Senao Sub 362 USB adapter using the Atheros AR5523

As you can see ive loaded the Net5523.inf and athfmwdl.inf files,

but plugging in the device and looking for it via either ifconfig or iwconfig
delivers zero results, so i thought asking someone might help a lot!

thus, thanx for helping

henry@qzonk:~/wireless$ lsusb
Bus 003 Device 003: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  

henry@qzonk:~/wireless$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

henry@qzonk:~/wireless$ ndiswrapper -l
athfmwdl : driver installed
        device (0CF3:0002) present
net5523 : driver installed
        device (0CF3:0002) present
henry@qzonk:~/wireless$

---

### Post by frenkiel on 2007-07-02
I am exactly in the same case as Qzonk:
  - same outputs
  - same problem: device ath0 doesn't show up
I must add that  it worked perfectly before I did the stupid
thing to replace Fedora Core 6 by Ubuntu on my laptop...

Any help would be appreciated.

---

### Post by frenkiel on 2007-07-02
At last, I solved the problem by removing the ndiswrapper debain packages,
and installing version 1.46 from the tar ball.
Can some ubuntu guru explain that ?

---

