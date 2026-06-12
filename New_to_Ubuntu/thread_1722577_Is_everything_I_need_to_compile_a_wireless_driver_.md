---
title: "Is everything I need to compile a wireless driver on the install cd?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by itguy1985 on 2011-04-05
I installed Ubuntu successfully. I need to compile a driver but things are missing. From what I can see I at least need to install the build-essential package. Will I need anything else? Is this stuff on the install cd. I have no hardwired network card.

---

### Post by josephmills on 2011-04-05
> **itguy1985 said:**
> I installed Ubuntu successfully. I need to compile a driver but things are missing. From what I can see I at least need to install the build-essential package. Will I need anything else? Is this stuff on the install cd. I have no hardwired network card.

the cd uses the internet to "help" the os install. If you have no eth0 then it will not be able to get some things. All thing that are proprietary will not install by there self. Do you know what kind of wireless card you have?

---

### Post by itguy1985 on 2011-04-06
> **josephmills said:**
> the cd uses the internet to "help" the os install. If you have no eth0 then it will not be able to get some things. All thing that are proprietary will not install by there self. Do you know what kind of wireless card you have?

it's the ralink 3062 chip set I have the driver but need to compile

---

### Post by wep940 on 2011-04-06
If you have the Ubuntu LiveCD that you installed from, the build-essential package is in the /pool/main/b/build-essential folder.  I know that if you install it via the package manager you get the compilers, etc., but I don't know about the package from the CD - I would assume the same.  If you need gcc-4.4 look in the /pool/main/g folder.

---

### Post by itguy1985 on 2011-04-06
> **wep940 said:**
> If you have the Ubuntu LiveCD that you installed from, the build-essential package is in the /pool/main/b/build-essential folder.  I know that if you install it via the package manager you get the compilers, etc., but I don't know about the package from the CD - I would assume the same.  If you need gcc-4.4 look in the /pool/main/g folder.

I'm in my windows install. All i see in that folder is a package called grub-efi.deb

---

