---
title: "NIC not getting detected"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by heartshaped on 2009-09-25
hey guys, Im using Ubuntu Server 8.04 and i cant seem to install a second NIC in order to run the box as a proxy :(
 
Ive used the lspci command to view my hardware and its not coming up at all, i know i installed it correctly :S i mean plug the damn thing into a PCI slot, (the other NIC is coming up, ie my realtech ethernet adapter)
 
Im trying to install a DGE 530T which says that there is linux support but for some reason it wont even get detected? any ideas, 
 
Do i have to install the drivers first? because i have a copy of the on a CD given with the NIC, if that the case how on earth do i do that using the basic command line prompt in Linux, (i think its called the bash shell or something like that)
 
Btw Modconf wont work either, whenever i find the driver i think is right (dl2k) it gives me an error message 
"FATAL: Error inserting dl2k (/lib/modules/2.6.24-24-server/kernel/drivers/net/dl2k.ko): Operation not permitted
Installation failed.
 
the update-modules command is deprecated and should not be used!"
 
Then press enter to continue

---

### Post by Bachstelze on 2009-09-25
Please paste the output of

```
lspci -k
```

---

### Post by heartshaped on 2009-09-25
lspci -k isnt an recognisable argument :S

---

### Post by Bachstelze on 2009-09-25
> **heartshaped said:**
> lspci -k isnt an recognisable argument :S

I'm pretty sure it is.

---

### Post by heartshaped on 2009-09-25
Just tried it its not an arg, what output did you want ill look through the help with it

---

### Post by philinux on 2009-09-25
From man lspci
```
-k     Show kernel drivers handling each device and also kernel modules
              capable of handling it.  Turned on by default when -v  is  given
              in  the  normal  mode of output.  ([B]Currently works only on Linux
              with kernel 2.6 or newer.)
[/B]

```

Works here. Maybe you are on an older kernel.

---

### Post by heartshaped on 2009-09-25
okay how do i update my kernel then? presumably some ATP command?

---

### Post by philinux on 2009-09-25
You could enable the backports repo. It may have a later kernel for the LTS. Click the backports link below. 

I've never installed a new kernel so cant help you there. Maybe a separate thread could get you help or a bit of searching.

Or upgrade to a later release.

---

### Post by philinux on 2009-09-25
Hang on 8.04 LTS desktop uses a 2.6 kernel. Check your kernel with system monitor.

[http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-32aaa603103e2cc37066332131dcef4f1c021d66](http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-32aaa603103e2cc37066332131dcef4f1c021d66)

---

### Post by tenmoi on 2009-09-25
> **heartshaped said:**
> lspci -k isnt an recognisable argument :S

You can do this: (go to applications -> accessories -> terminal)

sudo lshw

Scroll and look for all instances of *-network. Look at the product field and your card name and model will be listed there (at least on my system)

If you have an instance like this: -*network DISABLED, then you know that you have to activate it. YOu read on and find "logical name ethx". Ok now do:

sudo nano /etc/network/interfaces

append these lines:

     auto ethx
     iface ethx inet dhcp ( from the command line you can do a "man interfaces" to know how to configure this file)

then CTRL + X  and press "y" to accept and "enter" to save the file

then you do:

sudo /etc/init.d/networking restart

Now you can do this:
ifconfig

and see if your NIC (ethx) is listed with IP address and if you can go through it to the INternet.

---

### Post by heartshaped on 2009-09-25
AHA Eureka, thankyou got it running now and its displaying as eth1 in ifconfig
 
cheers fellas

---

