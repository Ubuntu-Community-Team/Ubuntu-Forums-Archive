---
title: "Upgrade to VirtualBox 3.0"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by jeffbilling on 2009-07-14
I am running VirtualBox 2.1.4 and I wish to upgrade to latest version.

 I read somewhere in the Forum that I have to first uninstall v2.1.4

I am currently running Windows XP inside the VirtualBox.

My question is:

If I uninstall V2.1.4 and then install VirtualBox 3.0.2 will I then have to re-install Windows XP (and then have to download all those patches!!) or will the Windows XP be picked up by new version.

If you could also point me back to how I uninstall v2.1.4 I would be greatful.

---

### Post by philinux on 2009-07-14
If it aint broke why fix it. What is to be gained in version 3.0?

I'm testing win 7 in VB.

---

### Post by jeffbilling on 2009-07-14
O.K I may not fix it immediately but I would still like to know the answer to my question regarding whether or not I would lose the current Windows XP

---

### Post by philinux on 2009-07-14
> **jeffbilling said:**
> O.K I may not fix it immediately but I would still like to know the answer to my question regarding whether or not I would lose the current Windows XP

I dont think you would as all your settings and virtual hard drives etc are stored in /home in the folder ~/.VirtualBox

---

### Post by jeffbilling on 2009-07-14
Thanks for that philinux.

---

### Post by mike555 on 2009-07-14
I just installed the new version of vb over the older version and everthing works ok ......... I'm running Hardy if that matters ..

---

### Post by philinux on 2009-07-14
Whats the newer version got that's better?

---

### Post by Cheesemill on 2009-07-14
> **philinux said:**
> Whats the newer version got that's better?

3D Graphics Support

---

### Post by lkraemer on 2009-07-14
jeffbillings,
One big difference is where the newer version stores the vdi file.
Newer versions have the GUEST.vdi file stored at:
home/USER/.VirtualBox/HardDrives

Under the .VirtualBox folder you should have two folders.
HardDisks & Machines

The VDI folder should contain your Windows.vdi file

OR for previous versions the folders will be:
Machines & VDI

Your .VirtualBox folder will remain after the removal of VirtualBox,
and the new HardDrives folder should be created, so just copy your
GUEST.VDI from the old storage folder to the HardDrives folder if
the install doesn't do it automatically.  (I haven't tried that sort
of upgrade yet.)

You shouldn't have any trouble with VirtualBox 3.0.2.

lkraemer

---

### Post by sqyntz on 2009-07-24
> **philinux said:**
> Whats the newer version got that's better?

 from [http://www.virtualbox.org/wiki/Changelog:](http://www.virtualbox.org/wiki/Changelog:) 
 
[LIST]
[*]Guest SMP with up to 32 virtual CPUs (VT-x and AMD-V only; see [chapter 3.7.2.2]("http://www.virtualbox.org/manual/UserManual.html#settings-processor") of the [user manual]("http://download.virtualbox.org/virtualbox/3.0.0/UserManual.pdf"))
[*]Windows guests: ability to use Direct3D 8/9 applications / games (experimental; see [chapter 4.8]("http://www.virtualbox.org/manual/UserManual.html#guestadd-3d") of the [user manual]("http://download.virtualbox.org/virtualbox/3.0.0/UserManual.pdf"))
[*]Support for OpenGL 2.0 for Windows, Linux and Solaris guests
[/LIST]

thank you mike555 & lkraemer for answering the OP question

---

