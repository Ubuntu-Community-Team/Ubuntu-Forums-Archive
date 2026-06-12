---
title: "i need help downgrading..."
date: 2009-05-26
forum: New to Ubuntu
---

### Post by r3l3ntl35 on 2009-05-26
i have ubuntu jaunty installed n i want to downgrade to hardy, ive already downloaded the content and made the cd. where do i go from here? when i try to run the wubi.exe file, it opens up in wine, and i cant go any further from there... what do i do?

---

### Post by Boondoklife on 2009-05-26
> **r3l3ntl35 said:**
> i have ubuntu jaunty installed n i want to downgrade to hardy, ive already downloaded the content and made the cd. where do i go from here? when i try to run the wubi.exe file, it opens up in wine, and i cant go any further from there... what do i do?

I have never come across a way to "downgrade the entire OS" you would really just need to backup your data and reinstall.

---

### Post by WRDN on 2009-05-26
You can't downgrade, only upgrade. The only option you have if you wish to return to Hardy is to wipe the current partition Ubuntu is installed on and install Hardy as a clean install (or put Hardy on a different partition and just ignore Jaunty).

---

### Post by doas777 on 2009-05-26
well, I don;t know of any way to downgrade, beyond just installing over jaunty. this means you will have to backup your user content first though, unless you keep your data on a seperate partition.

if you don't, i really recomend that you create a seperate home partition when you install hardy. that way, switching versions or even distros is smooth and easy.

have fun

---

### Post by r3l3ntl35 on 2009-05-26
thats what i mean by downgrading: completely wiping out jaunty and installing hardy... idk how to get the disk i just created to work

---

### Post by doas777 on 2009-05-26
> **r3l3ntl35 said:**
> thats what i mean by downgrading: completely wiping out jaunty and installing hardy... idk how to get the disk i just created to work
Scratch that. not right for wubi. sorry.

---

### Post by Didius Falco on 2009-05-26
If there are any files in your current Wubi install you want saved, go into it and back them up/copy them to a Windows folder.

Then go to Add/Remove Software and completely uninstall the current Wubi setup. I'd reboot after doing so. Then just install the Hardy version and Bob's your uncle!!

Regards,

Didius

---

### Post by Boondoklife on 2009-05-26
> **r3l3ntl35 said:**
> thats what i mean by downgrading: completely wiping out jaunty and installing hardy... idk how to get the disk i just created to work

It should be as simple as poping the cd in and booting your computer with it. Is this a dual boot system, ie windows and ubuntu or just ubuntu?

---

### Post by doas777 on 2009-05-26
> **maletek said:**
> It should be as simple as poping the cd in and booting your computer with it. Is this a dual boot system, ie windows and ubuntu or just ubuntu?

thats what i thought, but it appears the op is using wubi from within a windows desktop.

---

### Post by oldos2er on 2009-05-26
Wubi is meant to be run under Windows, not Ubuntu.

---

### Post by r3l3ntl35 on 2009-05-26
> **maletek said:**
> It should be as simple as poping the cd in and booting your computer with it. Is this a dual boot system, ie windows and ubuntu or just ubuntu?
im running ubuntu only. no windows.

---

### Post by doas777 on 2009-05-27
> **r3l3ntl35 said:**
> im running ubuntu only. no windows.

  then put your live cd in a boot off it. once the desktop loads, there will be an icon to install to your hdd.

WUBI is only for use within windows.

---

