---
title: "Orinoco Silver not working or loading wrong drivers"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Neo_Reloaded2 on 2007-05-04
Hello.

I am running Ubuntu 7.04 and I have an Orinoco Silver PCMCIA 11b Wireless card (Lucent Technologies PC24E-H-FC) and I was trying to change drivers and I think I have a big mess now, because when I plugin into the PCMCIA it does not lit any led and checking configuration I have found it:

Doing a "sudo lshw -C network" I obtain it:
```
  *-network
       description: WaveLAN/IEEE
       product: Version 01.01
       vendor: Lucent Technologies
       physical id: 0
       slot: Socket 0

```
And checking "lspcmcia" I obtain an strange thing
```
Socket 0 Device 0:      [-- no driver --]       (bus ID: 0.0)
```

It appears as WaveLAN/IEEE and I am not sure if it is correct. Doing a "lsmod | grep orinoco" or "lsmod | grep hostap" I obtain nothing so no Orinoco nor hostap modules are loaded.

Does anybody knows how to fix it and reinstall the needed drivers to be able to work with that card?

Thanks in advance.

---

### Post by chili555 on 2007-05-04
I believe orinoco and its cousin hostap are correct. If you do:```
sudo modprobe orinoco_cs
```followed by:```
iwconfig
```Does your interface appear? Sometimes these cards will also mistakenly load *prism2_cs* which is incorrect. You might check for that with lsmod and blacklist if necessary.

---

### Post by Neo_Reloaded2 on 2007-05-04
Hello.

I have tried and shows orinoco_cs module not found, or something like that, it states that there is no orinoco_cs module. I have been reading and it seems that with latest kernel 2.6.20-15 of Ubuntu 7.04 Orinoco chipset cards are having a lot of troubles, I have tried to bootup with an old kernel (2.6.17-10) and it loads OK the orinoco_cs modules and it wokrs.

 I hope that a new driver version will appear soon.

If anyone knows how to get working an Orinoco with the new kernel version 2.6.20-15 please let me know because I'm going mad!

Thanks.

> **chili555 said:**
> I believe orinoco and its cousin hostap are correct. If you do:```
sudo modprobe orinoco_cs
```followed by:```
iwconfig
```Does your interface appear? Sometimes these cards will also mistakenly load *prism2_cs* which is incorrect. You might check for that with lsmod and blacklist if necessary.

---

### Post by chili555 on 2007-05-04
Well, it works fine for me. When you boot up the newer kernel, does *lsmod | grep prism2* tell us the outlaw module loaded? If so please *sudo gedit /etc/modprobe.d/blacklist* to add:```
blacklist prism2_cs
```. Reboot andd see if orinoco_cs loads and your card works.

---

### Post by Neo_Reloaded2 on 2007-05-06
Hello.

I tried to blacklist drivers but still nothing, I tried to "sudo modprobe orinoco_cs" and it says "FATAL: module orinoco_cs not found", the same with "sudo modprobe orinoco".

I guess the problem is that I don't have the specified module, so if anyone knows how to compile or install it under Ubuntu 7.04 please let me know, because I don't know how to do it.

Thanks in advance.

Regards.

---

### Post by chili555 on 2007-05-06
> guess the problem is that I don't have the specified moduleActually, you do. Please do:```
sudo updatedb
locate orinoco
```updatedb will take a minute so let it churn. You should see a /lib/modules/..../orinoco_cs.ko listing.

I think the real problem is it doesn't think it has any device that uses the orinoco module, so it won't load it. I think the symptom is this:> Socket 0 Device 0:      [-- no driver --]       (bus ID: 0.0)As well, *lshw* is severely abbreviated.

> I was trying to change drivers  Can you please tell us more about this?

---

### Post by Neo_Reloaded2 on 2007-05-06
chili555 thank you very much for your time, I tried to updatedb with no luck. I observed that under /lib/modules/2.6.20-15-generic/..../orinoco_cs.ko is not there but it exists under the old kernel 2.6.7.10 that if I try to boot it seems to work.

Let me explain a little more so it will be easier, first I was running Ubuntu 6.10 Edgy and the Orinoco Silver (Lucent Technologies), Hermes I chipset, was working with no problem, after updating I can not remember if it continued working because after it I started to look for "modified drivers" to be able to use monitor mode with Orinoco Silver. Because I am not so good with Ubuntu and all about compiling drivers I tried a few things, like replace drivers with the one of 
```
http://www.nongnu.org/orinoco/
``` and something about pcmcia_cs 3.2.8, after try this it just don't work. So I don't know if it is because of me or because of new kernel of Ubuntu but I can not find how to load the correct module.

If you need more information about the system or configuration, just let me know how to do it and I will try, because I don't want to reinstall all the system, if possible.

Thank you very much!!!

---

### Post by chili555 on 2007-05-06
I took a look at this:[http://www.nongnu.org/orinoco/]("http://www.nongnu.org/orinoco/") It's a bit tricky, but not impossible. I assume you have build-essential and linux-headers installed. If not, you can get them from Synaptic.

Open a terminal and cd to the orinoco-0.15 directory. gedit Kbuild to comment out these lines:```
ifdef CONFIG_HERMES
$(error This driver is already enabled in the kernel)
endif
```In other words, you will insert a **#** in front of each of these three lines. Save and close gedit.

Then do:```
make
sudo make install
```If there are errors, post back and let me help.

PS - This is Plan A; we do have a Plan B if this fails.

---

### Post by Neo_Reloaded2 on 2007-05-07
Hello.

I have tried and when launching "sudo make" it ends without finishing and with error, here I attach the error:
```
user@user:~/Ori/orinoco-0.15$ sudo make
make -C /usr/src/linux-headers-2.6.20-15-generic M=/home/user/Ori/orinoco-0.15 KERNELRELEASE=2.6.20-15-generic modules
make[1]: Entering directory `/usr/src/linux- headers-2.6.20-15-generic'
  CC [M]  /home/user/Ori/orinoco-0.15/orinoco.o
/home/user/Ori/orinoco-0.15/orinoco.c:2466:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Ori/orinoco-0.15/orinoco.c: In function 'alloc_orinocodev':
/home/user/Ori/orinoco-0.15/orinoco.c:2466: error: 'INIT_WORK' undeclared (first use in this function)
/home/user/Ori/orinoco- 0.15/orinoco.c:2466: error: (Each undeclared identifier is reported only once
/home/user/Ori/orinoco-0.15/orinoco.c:2466: error: for each function it appears in.)
/home/user/Ori/orinoco-0.15/orinoco.c:2467:68: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/user/Ori/orinoco-0.15/orinoco.c:2468:75: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
make[2]: *** [/home/user/Ori/orinoco-0.15/orinoco.o] Error 1
make[1]: *** [_module_/home/user/Ori/orinoco- 0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
```Because of this I can not compile the driver, and I have commented the lines indicated.

I tried the information indicated in that page ```
https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200
``` but ends with the same error.

Thanks in advance.

---

### Post by chili555 on 2007-05-07
A Google search for 'INIT_WORK 2.6.20' shows that this was changed in the 2.6.20 kernel and I found no fix, although I only looked at 20 or so posts. 

Plan B that I referred to, involves re-installing your 2.6.20-15 kernel. I am not sure if you can do so in the kernel you are running, so, to be safe, reboot into 2.6.17 and, in Synaptic, mark linux-image, linux-headers and linux-restricted-modules, all of the 2.6.20-5 version, for re-installation.

When you then reboot into 2.6.20, your orinoco modules should be restored.

---

### Post by Neo_Reloaded2 on 2007-05-07
Hello chili555.

That is exactly the problem, the "INIT_WORK" but I can see that it is normal due changes in the new kernel, I will need to wait for a solution.

I have tried to reinstall the kernel but it did not worked, but I found out how to do what I wanted to do with the integrated Intel IPW3945 so I will work with it until a new patch for the new kernel appears, because I do not want to broke my Ubuntu now that it is working great.

Thank you very much for your time.

Regards.

---

