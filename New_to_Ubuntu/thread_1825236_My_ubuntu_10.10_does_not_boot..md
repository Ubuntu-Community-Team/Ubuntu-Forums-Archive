---
title: "My ubuntu 10.10 does not boot."
date: 2011-08-15
forum: New to Ubuntu
---

### Post by amityadav9314 on 2011-08-15
Hello!
 I ran this command "sudo apt-get remove python" by mistake, not knowing  the consequences, and it removed it everything 
Then I used the following command to install it back.


```
sudo fdisk -l
sudo mount /dev/sda5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
sudo umount
```After this I sucessfully installled back my python.
I ran "sudo apt-get -f install" also
But when I rebooted the system I am getting these errors and can not at all boot in the system.

It says:-


1:- [12.092021] /*build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c*:  *usb_submit_urb*(crtl) *failed*
(That is the error which comes at the very starting of booting screen.

2:-Then a window appears which says:---UBUNTU IS RUNNING IN LOW GRAPHICS  MODE
YOUR SCREEN, GRAPHICS CARD, AND INPUT DEVICE SETTINGS COULD NOT BE  DETECTED CORRECTLY, YOU WILL NEED TO CONFIGURE THIS YOURSELF.


3:-after that another windows pop up saying, "stand by one minute while  the display starts.


But it never starts, The boot screen exists  forever...:sad:

Please help me.

---

### Post by jtarin on 2011-08-15
Have you tried booting with safe mode from Grub screen, or booting with an alternate kernel?
Is this an old install or recent? When did you download?

---

### Post by amityadav9314 on 2011-08-15
I do not know,  I do not see any safe mode option. Please Tell me where I will find it

---

### Post by jtarin on 2011-08-15
> **amityadav9314 said:**
> I do not know,  I do not see any safe mode option. Please Tell me where I will find itIf you will read my post thoroughly it will tell you to Find it at the Grub Boot Screen.

---

### Post by amityadav9314 on 2011-08-15
> **jtarin said:**
> booting with an alternate kernel?
Is this an old install or recent?
There on the booting options it shows two kernel, but i can choose only the first one, the other does not work.
This is a very old install, about 1.5 years

---

### Post by amityadav9314 on 2011-08-15
Is there any possibility that it removed my "ubuntu-desktop" when i removed python because it removed almost everything.
I tried this command "sudo apt-get install ubuntu-desktop" by entering into the chroot of /sda6(my linux partiton ) and it installed it, this means this was not insatlled or was removed.
By the way please tell me what this command do...sudo apt-get install ubuntu-desktop

---

### Post by jtarin on 2011-08-15
You should have something like a kernel with "recovery mode", in the Grub menu.
Have you kept your system updated?

---

### Post by amityadav9314 on 2011-08-15
Yes there is a option of recovery mode, when i choose that, it shows option like:-
1:- Enter to the regular boot menu
2:- upgrade grub
3:- Enter prompt with networking\g.
4::- Enter command shell

I can successfully enter into command shell, it prompt for the user name and password 
Ager that when I try to open anything like synaptic or Firefox, it throws some error like ....display not mentioned.
Is there any problem with the DISPLAY, might be that is not installed

---

### Post by amityadav9314 on 2011-08-15
> **jtarin said:**
> 
Have you kept your system updated?
Yeah i have updated my system when i entered into chroot of /sda6 vai the live CD

---

### Post by jtarin on 2011-08-15
> **amityadav9314 said:**
> Yes there is a option of recovery mode, when i choose that, it shows option like:-
1:- Enter to the regular boot menu
2:- upgrade grub
3:- Enter prompt with networking\g.
4::- Enter command shell

I can successfully enter into command shell, it prompt for the user name and password 
Ager that when I try to open anything like synaptic or Firefox, it throws some error like ....display not mentioned.
Is there any problem with the DISPLAY, might be that is not installedWhat graphics card are you using?

---

### Post by amityadav9314 on 2011-08-15
Yippee......
Hey man thanks for all your help.
I rebooted successfully.
I think this command has helped me....
sudo apt-get install ubuntu-desktop

---

### Post by jtarin on 2011-08-15
Excellent! Mark the thread as solved using thread tools at the top of the page.

---

### Post by amityadav9314 on 2011-08-15
Okay, the thread is marked as a SOLVED.
Thanks!

---

### Post by jtarin on 2011-08-15
Your more than welcome! Good Luck!

---

