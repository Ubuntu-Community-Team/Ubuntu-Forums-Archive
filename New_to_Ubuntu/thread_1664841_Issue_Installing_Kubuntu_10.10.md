---
title: "Issue Installing Kubuntu 10.10"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by mastergunner on 2011-01-11
When I boot up my computer with the Kubuntu CD in the disk drive the install screen pops up. Once I select Install Kubuntu I get a blank scree and nothing happens. I have a NVIDIA 8500GT Video Card. What do I do not? Thanks for the help.

---

### Post by Linyx on 2011-01-11
> **mastergunner said:**
> When I boot up my computer with the Kubuntu CD in the disk drive the install screen pops up. Once I select Install Kubuntu I get a blank scree and nothing happens. I have a NVIDIA 8500GT Video Card. What do I do not? Thanks for the help.

Have you Checked whether the CD is Correct > [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mastergunner on 2011-01-11
> **Linyx said:**
> Have you Checked whether the CD is Correct > [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It is good. I saw somewhere people with NVIDIA cards were having issues installing but I lost the webpage.

---

### Post by Linyx on 2011-01-11
> **mastergunner said:**
> It is good. I saw somewhere people with NVIDIA cards were having issues installing but I lost the webpage.

see post #6 here...> [http://forums.hexus.net/operating-systems-applications/111344-nvidia-causing-problems-ubuntu-kubuntu.html](http://forums.hexus.net/operating-systems-applications/111344-nvidia-causing-problems-ubuntu-kubuntu.html)

Edit:- I think their is** f4** Option While installing Kubuntu , From their Select **Safe-mode**, and then try to install......

---

### Post by mastergunner on 2011-01-11
I read that as you already have 10.10 installed. I cant even install it because the screen is blank.

---

### Post by Linyx on 2011-01-11
> **mastergunner said:**
> I read that as you already have 10.10 installed. I cant even install it because the screen is blank.

Have you tried that **safe-mode** while installing ,as i mentioned in above post....?

---

### Post by mastergunner on 2011-01-11
Yes I have.

---

### Post by Linyx on 2011-01-12
> **mastergunner said:**
> Yes I have.

Did you still getting that blank screen...?

Try to install from flash, i think you had burned your image wrong or the image you are using is bad.....

---

### Post by pissedoffdude on 2011-01-12
I had a similar issue with a 9600GT.  When you get to the purple screen just after grub, hit f6, and use the nomodeset paramater.  Then install.  Reboot, type e at the grub menu, and add nomodeset after quite splash and you should be able to boot and install the appropriate video drivers.

---

