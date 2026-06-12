---
title: "OK, I found drivers. What do I do with them now?"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by Beretta_NZ on 2008-05-30
I have an internet PCI dsl modem. It's a Dynalink ALH110.

I managed to find Linux drivers for it (alh110_linux221214-generic.zip), for Linux kernels 1.12 - 2.14. I have insufficient technical knowledge to know if that means I can use them with Ubuntu Hardy Heron.

If I can use them what would I do with them? The zip file contains three files:

itex1483-2.2.16.o
itex1483-2.2.14.o
ifconfig

Any suggestions are welcome.

---

### Post by hal10000 on 2008-05-30
> **Beretta_NZ said:**
> I have an internet PCI dsl modem. It's a Dynalink ALH110.

I managed to find Linux drivers for it (alh110_linux221214-generic.zip), for Linux kernels 1.12 - 2.14. I have insufficient technical knowledge to know if that means I can use them with Ubuntu Hardy Heron.

If I can use them what would I do with them? The zip file contains three files:

itex1483-2.2.16.o
itex1483-2.2.14.o
ifconfig

Any suggestions are welcome.

Don't use these drivers, because they are made for use with (very) old kernel. (kernel versions 2.2.12 anh 2.2.14.

If you are using hardy heron i suppose your kernel version is 2.6.16 or 2.6.17. you can find out the number of your kernel-version by using the command [COLOR="Red"]uname -r[/COLOR] in a terminal window.
I don't know anything about your dsl-modem, but usually most needed hardware-drivers are already installed on your system.
 To find out something about your modem use the command lspci -v and search for the lines relevant for your modem. You may also post the output of this command here, so we can help you further in case your modem is not recognized by the system.

I guess the best way to get your moden working is to start the network-manager (I don' use gnome, but i think it can be found under [COLOR="Red"]System --->Network settings[/COLOR] or something similar) and configure the device with your provider's data).

---

### Post by Beretta_NZ on 2008-05-30
Well, I installed ubuntu (dual boot with XP), got stuck with the famous "Busybox" issue, then got past that, logged in, and had a couple of fatal errors, and nautilus could not be displayed. So the question of modem drivers is a bit moot, lol. Ubuntu won't be going on this machine.

Thanks

---

### Post by mbogo.kariuki on 2009-08-25
Where can I get Huawei EG162G modem drivers for Ubuntu OS. The modem came with Windows drivers only.

---

