---
title: "[SOLVED] trouble installing rt73 driver for linksys WUSB54GC"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by Pardalnicu on 2008-10-09
Hello Everybody,
I'm pretty new in the Ubuntu-Linux world and I need you help. 
I got a new wireless Linksys wusb54gc wireless card I downloaded the drivers from [http://www.ralinktech.com/](http://www.ralinktech.com/). (This is the driver RT2501USB(RT73:RT2571W/RT2573/RT2671))

I followed up all the steps in the documentations that came with the driver, I compiled it and I got to the point to load it.

This is the loading part in the documentation: 

7> $load                

    #[kernel 2.6]

    #    $/sbin/insmod rt73.ko

    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

And this is the error that I got:
insmod: error inserting 'rt73.ko': -1 File exists

What shall I do?
I really much appreciate any help!

---

### Post by jmbargar on 2008-10-09
Always use "modprobe" instead of "insmod". Modprobe loads the modules that
a module depends on, "insmod" does not. So, try with this line instead of your insmod line:

> modprobe rt73.ko

Good luck!

---

### Post by Pardalnicu on 2008-10-11
hi jmbargar,
Thank you for reply.
I tried : modprobe rt73.ko and I got: 
FATAL: Module rt73.ko not found.

I do have the file rt73.ko in the directory and I didn't got any errors at compilation.
Do you have any further idea?

Thank you!

---

### Post by Pardalnicu on 2008-10-11
For whatever reason after I restart the computer and I unplugged and then plugged again the WUSB54GC, it seams to work now.
I see in the Network Settings all the wireless networks around me.
But all of them has 0% signal.

Any idea?

---

