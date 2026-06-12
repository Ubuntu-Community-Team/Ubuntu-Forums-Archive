---
title: "Laptop USB mounting"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by alekz8a on 2010-10-16
The issue is that Ubuntu is not mounting any USB device, no pendrivers no USB HDDs... can somebody help me?

Is this a bug is Ubuntu 10.10, when I try to mount the units it says that thy are already mount, wich is a lie... ¬¬

1)Version Of Ubuntu: 10.10
2)Laptop Maker: Acer
3)Laptop Model: eMachines eM250
4)Known Issue:?

---

### Post by Hippytaff on 2010-10-16
with a usb pendrive (or whatever) plugged in what is the output of 
```

lsusb

```

and

```

df

```

---

### Post by Ctrl-Alt-F1 on 2010-10-16
> **alekz8a said:**
> The issue is that Ubuntu is not mounting any USB device, no pendrivers no USB HDDs... can somebody help me?

Is this a bug is Ubuntu 10.10, when I try to mount the units it says that thy are already mount, wich is a lie... ¬¬

1)Version Of Ubuntu: 10.10
2)Laptop Maker: Acer
3)Laptop Model: eMachines eM250
4)Known Issue:?Can you verify that you cannot find the device if you go to Places > Computer?

If it says that it's already mounted it could be that gconf is just set not to display it on the desktop.

---

### Post by Hippytaff on 2010-10-16
> **Ctrl-Alt-F1 said:**
> Can you verify that you cannot find the device if you go to Places > Computer?

If it says that it's already mounted it could be that gconf is just set not to display it on the desktop.

Good point

---

### Post by acerone on 2010-11-24
I have the same problem. I have a 4gb Imation usb pluged in.
usb dose not show up in places/computer.
but when i boot my computer with the usb in the computer it mounts and shows up on the desktop
neo@neo-AOD255:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0718:044e Imation Corp. 
Bus 001 Device 002: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hippytaff on 2010-11-24
> **acerone said:**
> I have the same problem. I have a 4gb Imation usb pluged in.
usb dose not show up in places/computer.
but when i boot my computer with the usb in the computer it mounts and shows up on the desktop
neo@neo-AOD255:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0718:044e Imation Corp. 
Bus 001 Device 002: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
Did you try CTRL-ALT-F1's suggestion in post #3

---

