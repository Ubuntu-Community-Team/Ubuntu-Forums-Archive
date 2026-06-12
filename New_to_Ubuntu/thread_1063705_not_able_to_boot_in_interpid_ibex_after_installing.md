---
title: "not able to boot in interpid ibex after installing nvidia 6200 graphic card"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by imlinux on 2009-02-08
as i installed nvidia 6200 graphic card in my pc i am not able to boot in ubuntu,but as i remove the card from the hardware everything goes fine.my pc specifications are:-  

RAM=512mb,processor=3Ghzt with HT,
motherboard=82865 one thats intel geniune not the chipset,
graphic card is nvidia 6200,256 MB,
kernel version for ubuntu 8.10=Linux 2.6.27-11-generic,

i had successfully installed hardy heron without trouble with boot with my graphic card in my hardware.i guess its something to do with kernel it returns with the error while booting.is there anyway to disable ubuntu to detect my hardware while booting so that i am able to boot first then install its driver for graphic card.

i am using my pc without card even though i have one.

---

### Post by carml on 2009-02-08
I think two ways could resolve: 1. boot Intrepid choosing recovery mode(it may help,but I'm ensure);2. try with a previous kernel.
All the two require that the card should be installed on the PC,of course.
To install a previous kernel(even if possible in Intrepid) go to System->Administration->Synaptic Package Manager and look fr a previous kernel in the system section.

---

### Post by imlinux on 2009-02-08
> **carml said:**
> I think two ways could resolve: 1. boot Intrepid choosing recovery mode(it may help,but I'm ensure);2. try with a previous kernel.
All the two require that the card should be installed on the PC,of course.
To install a previous kernel(even if possible in Intrepid) go to System->Administration->Synaptic Package Manager and look fr a previous kernel in the system section.
 none of the kernel versions that come with interpid ibex are able to support my graphic card although it was ok with hardy heron.what you suggested i have tried it already.

---

### Post by carml on 2009-02-08
So it looks like a problem related to the kernel,if you need to use that VGA I suggest (IMHO) so to use Hardy instead of Intrepid.:confused:

---

### Post by imlinux on 2009-02-08
> **carml said:**
> So it looks like a problem related to the kernel,if you need to use that VGA I suggest (IMHO) so to use Hardy instead of Intrepid.:confused:
 i am thinking about compiling custom kernel but haven't done it before so hesitating to venture in that direction.is there any detailed guide for it.

---

### Post by carml on 2009-02-08
Yes if I'm not wrong there's a site called linuxkernel,you can find by google the right one.You can also look into the main sections of the forum and see if there's some suggestions.

---

### Post by felix.rommel on 2009-02-08
What is the error message on your screen when booting your Intrepid with your NVIDIA 6200 graphic card?

[LIST]
[*]Do you have an onboard graphic card?
[*]Did you try to disable the onboard graphic card in your BIOS when using the NVidia card?
[/LIST]

---

### Post by imlinux on 2009-02-08
> **felix.rommel said:**
> What is the error message on your screen when booting your Intrepid with your NVIDIA 6200 graphic card?

[LIST]
[*]Do you have an onboard graphic card?
[*]Did you try to disable the onboard graphic card in your BIOS when using the NVidia card?
[/LIST]
 yes i guess there is on board graphic card how do i disable it ?i have phoenix BIOS i dont know the version, i dont have camera working so to click it what comes in console,but your suggestion with disabling onboard graphic seem to be way out.

---

