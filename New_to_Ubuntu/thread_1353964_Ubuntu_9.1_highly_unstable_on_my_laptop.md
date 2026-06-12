---
title: "Ubuntu 9.1 highly unstable on my laptop"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by brett01 on 2009-12-13
Hi,

    I am having lots of problems with ubuntu 9.1. Its higly unstable on my laptop.Only once in 3  booting itempts it works. The problem is it gives me currupted screen and system gets struck. Can someone solve my problem pls. I am using intel core 2 duo proc, Nvidia 9500M Gs graphics card, Realtek HD audio drivers. I never got these kinds of problems before.

Thanks & Regards,
brett.

---

### Post by gs777 on 2009-12-13
have u installed nvidia proprietory driver? if no then installing it may solve your problem

---

### Post by brett01 on 2009-12-13
> **gs777 said:**
> have u installed nvidia proprietory driver? if no then installing it may solve your problem
No I didnt do it. Can you help me how to do it please

---

### Post by talsemgeest on 2009-12-13
> **brett01 said:**
> No I didnt do it. Can you help me how to do it please
Go to System>Administration>Hardware Drivers. Select the driver you want to install, then click "activate".

---

### Post by brett01 on 2009-12-14
> **talsemgeest said:**
> Go to System>Administration>Hardware Drivers. Select the driver you want to install, then click "activate".
No I opened the hardware drivers menu. Its showing only modem drivers thats it.  There is nothing more in it.

---

### Post by The_Pirate_King on 2009-12-14
You may consider an older distribution of Ubuntu, since 9.1 is the latest disto it's likely to be less stable.

---

### Post by chessnerd on 2009-12-14
If you are running 32 bit Linux, this driver might work:

[http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

For 64 bit try this one:

[http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)

Found them by inputing GeForce 9M Series (which I believe is your card) on this page and picking either 32 or 64 bit:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Hope this helps


EDIT: Also from nVidia for the 32-bit one (64 bit would be a different driver name) -

> Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-190.42-pkg1.run

---

### Post by IBadget on 2009-12-14
Another solution might be to boot with the noapic parameter.

---

### Post by brett01 on 2009-12-14
Hi,

     I tried to install the drivers before It asks me to disable x windows framwork . When i press the ctrl+alt+F1 I am getting the old curopted screen!

---

### Post by gs777 on 2009-12-14
> **brett01 said:**
> No I didnt do it. Can you help me how to do it please
you can install nvidia drivers by this method also
1..open synaptic package manager
2..search for nvidia , there you will see the drivers. install them in usual way. also remember to install nvidia - xorg settings program

---

### Post by Marvin666 on 2009-12-14
If you can't get it running try the version I run. It runs fast and hasn't given me hardware trouble except for hot swapping an external monitor that needs a very weird graphics mode to drive properly (monitor has ceased to work,  so this is no longer an issue).

---

