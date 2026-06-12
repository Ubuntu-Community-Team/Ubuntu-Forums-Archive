---
title: "formating a hfs plus using gparted for ubuntu install"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by daveb272 on 2009-02-08
A friend of mine gave me his broken macbook for parts.  I just bought a lenovo s10 netbook and i am currently using a live usb as i type. 
I have tried to format the used mac hd so i could install it on the 120gig hd.  However i cant format or create partition for the install.  Any ideas?  I have been using ubuntu since 6.10, but i am still consittered a newbie.

---

### Post by handydan918 on 2009-02-08
Why can't you? You don't give any error messages. 
I don't know if gparted handles that filesystem, but you might try using fdisk or cfdisk from the terminal.

---

### Post by daveb272 on 2009-02-08
Neither fdisk or cfdisk are able to open the hd.  it is mounted and i am able to navigate thru the folders, just unable to format.

ubuntu@ubuntu:~$ fdisk /dev/sda

Unable to open /dev/sda

---

### Post by houstonbofh on 2009-02-08
Unmount it.  You can not format a mounted partition.

---

### Post by daveb272 on 2009-02-08
Thank you, I told you i was a newbie,  Thats all it was.  Now I am getting a error of a faulty cd/dvd drive,  Install can not continue, even though I am running it off of a usb live drive. I am in the process of downloading another iso of 8.10, It might have been corrupted?

---

### Post by carml on 2009-02-08
Gparted cannot fully handle that filesystem,as you can see on the official website.

---

### Post by daveb272 on 2009-02-08
I downloaded two different iso's of 8.10 and durring install i get a Errno 5 input/output error.
Any ideas?
Just tried another 8.10 and a 8.04, both with fail out come!!!!!

---

### Post by carml on 2009-02-08
All the two passed the checksum control?Generally it is advisable to choose a low writing velocity in the burning software to avoid burning errors.

---

### Post by daveb272 on 2009-02-08
i did the checksum, i file with errors.  this is a usb install, so i cant control the write speed

---

