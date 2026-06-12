---
title: "Installing ubuntu on a external HDD"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by tntxx9 on 2008-12-13
I done a little search at the forum but didn't found anything that could help me out.
Well it is, i have here a external 2.5 HDD with 160 Gb, and i installed on it ubuntu BUT installed it wen i was IN my vista, what i really want to do is install ubuntu on it, to use it on any computer.
I know that on the oders computers i will need to change de boot order but thats no problem.
My question is how can i install ubuntu on the external. Using live cd ?! if yes is there any tutorial or so ?! 
I'm asking this because i couldn't really star the live cd, i started it but wen i go to hit instal it doesn't show up anything (i waited like 20 minutes)

Thanks in advance

---

### Post by cdtech on 2008-12-13
On most computers you can set the BIOS boot order including a USB device as your first boot device. With this said, you can install Ubuntu onto the external drive including the GRUB boot loader to the external drives MBR. You have to be sure that the device is flaged to boot.

As far as the install, you may need to try the Alternate CD for the install as some systems wont install using the Live CD.

---

### Post by adult swim on 2008-12-13
you may also run into a problem with the live cd when you try to install to the external drive.  i think by default ubuntu live will automatically mount an external drive that is attatched.  you run into a problem here because when you try to install, ubuntu cannot edit partitions or install to a drive that it mounted.  you need to right click on your external drive icon and select unmount before you click the install icon.
EDIT: as cdtech already suggested it is very important to install grub to the mbr of the external drive or you will run into problems trying to boot it from any computer.  to do this, i cant remember the exact step but it is the only one with the option advanced, you need to click advanced and then install grub to the mbr of the external disk.  if your disk is labeled as /dev/sdb, that is where you would want to place grub.

---

### Post by tntxx9 on 2008-12-13
Isn't there any tutorial ?! because I'm not an expert xD
I got a error on trying installing yes.

---

### Post by cdtech on 2008-12-13
You could start by reading the howto's
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by tntxx9 on 2008-12-13
thanks for the help, it seems there is an problem with my pc, because, every time i try to teste ubuntu via live cd or installing it, it simply do nothing ! i hit enter to install, de screen desapear and then nothing happens !

---

