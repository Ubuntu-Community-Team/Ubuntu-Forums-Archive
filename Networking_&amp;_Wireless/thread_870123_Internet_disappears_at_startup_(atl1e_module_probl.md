---
title: "Internet disappears at startup (atl1e module problem)"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by rehin on 2008-07-25
I downloaded and installed Atheros atl1e driver and it starts running without any problem as soon as I run the command below:

:~> sudo insmod /home/rehin/Drivers/l1e-l2e-linux-v1.0.0.4/src/atl1e.ko


However at each boot internet disappears and I have to rerun the command above. Also when as a root I try to run modprobe atl1e, it says "FATAL ERROR: Module atl1e not found". As a result, I can not put an additional extra line to modules.conf in order to solve this problem.

How can I get rid of entering the above insmod command after each boot? In other words how can atl1e module be loaded at startup automatically?

---

### Post by funkydan2 on 2008-07-27
I think kernel modules are expected to be found under /lib/modules (in a directory for the appropriate kernel), not in your home directory.

Maybe when you compiled the module you forgot a step or didn't run the 'make install' step as root (sudo make install)?

---

### Post by rehin on 2008-07-28
> **funkydan2 said:**
> I think kernel modules are expected to be found under /lib/modules (in a directory for the appropriate kernel), not in your home directory.

Maybe when you compiled the module you forgot a step or didn't run the 'make install' step as root (sudo make install)?

Thanks for the reply.

Yes you are right but atl1e.ko file is already in /lib/modules. When I installed the driver it put atl1e.ko under /lib/modules. So this is not the problem in this case I think.

---

### Post by rehin on 2008-07-28
Is not there anyone to help me on this problem? :confused:

---

### Post by chili555 on 2008-07-29
Please do:```
sudo updatedb
```This will take a few moments, so please be patient. Then post:```
locate atl1e.ko
uname -r
```Thanks.

---

### Post by rehin on 2008-07-29
> **chili555 said:**
> Please do:```
sudo updatedb
```This will take a few moments, so please be patient. Then post:```
locate atl1e.ko
uname -r
```Thanks.

The outputs are as follows:

```
locate atl1e.ko
/home/rehin/Drivers/l1e-l2e-linux-v1.0.0.4/src/atl1e.ko
/home/rehin/Drivers/l1e-l2e-linux-v1.0.0.4/src/.atl1e.ko.cmd
/home/rehin/.local/share/Trash/files/l1e-l2e-linux-v1.0.0.4/src/atl1e.ko
/home/rehin/.local/share/Trash/files/l1e-l2e-linux-v1.0.0.4/src/.atl1e.ko.cmd
/lib/modules/2.6.25.11-0.1-default/kernel/drivers/net/atl1e/atl1e.ko
/lib/modules/2.6.25.11-0.1-default/kernel/drivers/net/atl1e.ko
/lib/modules/2.6.25.11-0.1-default/kernel/net/atl1e/atl1e.ko
/lib/modules/2.6.25.5-1.1-default/atl1e.ko
/lib/modules/2.6.25.5-1.1-default/kernel/atl1e.ko
/lib/modules/2.6.25.5-1.1-default/kernel/drivers/net/atl1e/atl1e.ko

```

```
uname -r
2.6.25.11-0.1-default

```

Thanks for the help.

---

### Post by chili555 on 2008-07-29
It only looks perfect. But, evidently, it's not. I suggest a redo:```
cd Drivers/l1e-l2e-linux-v1.0.0.4/src/
make clean
KBUILD_NOPEDANTIC=1 make
sudo KBUILD_NOPEDANTIC=1 make install
```Now, upon reboot, does it work correctly?

---

### Post by rehin on 2008-07-30
> **chili555 said:**
> It only looks perfect. But, evidently, it's not. I suggest a redo:```
cd Drivers/l1e-l2e-linux-v1.0.0.4/src/
make clean
KBUILD_NOPEDANTIC=1 make
sudo KBUILD_NOPEDANTIC=1 make install
```Now, upon reboot, does it work correctly?

You are right. After I rebuilt and installed, now "modprobe atl1e" works but again it does not startup at the boot automatically. What should I do for this? I tried to remove "install eth0 /bin/true" and add "alias eth0 atl1e" line to /etc/modprobe.conf but it did not work.

---

### Post by chili555 on 2008-07-30
I hope you are really adding your data to */etc/modules.*I suggest adding, on it's own line:```
atl1e
```Does it load on reboot?

---

### Post by rehin on 2008-07-30
It is Ok. To 'module-renames' file under '/etc/modprobe.d' I added lines below:

```

alias eth0 atl1e
atl1e

```

It loaded at boot. Thanks very much. Super Help.\\:D/=D>

---

### Post by jgeissin on 2009-06-21
Using 2.6.28-11 (9.04 Desktop) on a ASUS EEEPC 1000HA.
Installed Ubuntu on the second partition.
I have performed all of the updates/settings that I can think of and still no network at all (wireless or wired).  The wireless light on the laptop is on all the time, but does not show up in Linux or the local access point.
lshw shows both the wireless and wired as unclaimed and network as disabled.
I have to transfer things manually onto the PC in order to try them (no network at all).
Ideas?

---

