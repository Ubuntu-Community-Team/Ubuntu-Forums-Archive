---
title: "mounting new cd/dvd"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by dovael on 2010-01-03
Changed today my LG cd/dvd for newer model and Ubuntu does not recognize and mount it. Also I can not enter media/New Volume which is my major partition. Perhaps I twiddled too much with Tweak's Package Cleaner. Help!

---

### Post by warfacegod on 2010-01-03
Check the permissions tab on the drive properties. If the owner is not listed as you but root then do this terminal command:



```
sudo chown -R your username:your username /media/drive name
```



Do not do that, however, if that is the drive that your OS is on. It will create a security black hole.

---

### Post by warfacegod on 2010-01-03
Oh! I forgot your cd/dvd drive. The only advice I have for that is to check the jumper setting in the back of the drive. Make sure it is set to master or possibly cable select if it's the only drive. If you have two, make sure one is master and one is slave as long as they are on the same ribbon cable.

---

### Post by Cheesemill on 2010-01-03
Is the drive IDE or SATA?

If it's IDE then check that the master/slave jumpers on the drive are set correctly. If you have both drives set to master or slave on the same channel it could prevent the computer from seeing either of them.

You can check your BIOS to see if your drives are being recognised correctly.

---

### Post by dovael on 2010-01-04
Tried your suggestion but terminal doesn't recognize drive

---

### Post by sandyd on 2010-01-04
whats the output of lspci

---

### Post by dovael on 2010-01-04
dov@dov-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
dov@dov-desktop:~$

---

### Post by mikewhatever on 2010-01-04
Hi Dov, I think the problem with the cdrom is related to the left over cdrom entry in fstab. Can you post the outputs the following from a Terminal or Console:

cat /etc/fstab

sudo fdisk -l

As for the New Volume partition, if you think you've removed something that caused the problem, make sure the package **kubuntu-desktop** is installed. Kubuntu-desktop is a meta-package, that pulls in all the default Kubuntu packages, including those you may have removed earlier. It might also be useful to look at the output of the following command:

ls -l /media

---

### Post by dovael on 2010-01-04
Actually the problem is the incorrect setting of jumpers. Now everything is working AOK. Thankyou Ubuntu Angels for your help

---

