---
title: "Getting back after dual-booting win 7"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by thelinnoob on 2010-12-02
Hey there, I did a clean install of ubuntu 10.10. I then used gparted to create a separate partition on my HDD. Now Im wondering how i can get back onto my linux partition? There are some files I have to get at.. I tried to lauch from the live CD, I could see the files but it said i did not have permission to access them, and it did not ask me for a password.
What can I do to get at the ubuntu partition. Just to clarify, by default it boots into win 7. I tried setting up EasyBCD, but I probably set it up wrong as when i select the linux option in the boot menu it gives me an error.
THanks for any help!

---

### Post by zipteye on 2010-12-02
It  doesnt offer you a menu when you first boot the computer?

---

### Post by thelinnoob on 2010-12-02
After I installed EasyBCD it offered me a menu once i set up a linux boot. The problem is that i must have set it up incorrectly as it gives me an error message when i try to boot into linux.

---

### Post by wilee-nilee on 2010-12-02
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

I know very little about esybcd2 but we may just have to get things back in order to get things working the script will give us the info needed.

---

### Post by jtarin on 2010-12-02
> **thelinnoob said:**
> After I installed EasyBCD it offered me a menu once i set up a linux boot. The problem is that i must have set it up incorrectly as it gives me an error message when i try to boot into linux.
You must install Grub to the / (root) of the Ubuntu partition and point EasyBCD to that. What is your error message?

---

