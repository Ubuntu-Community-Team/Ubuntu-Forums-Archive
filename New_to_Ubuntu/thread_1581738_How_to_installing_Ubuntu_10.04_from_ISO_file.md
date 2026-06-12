---
title: "How to installing Ubuntu 10.04 from ISO file"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-09-25
Hi ALL,

I 'm try to install ubuntu 10.04 from an iso file facing a serious problem Please anyone help me.

To Install from iso I set up /etc/grub.d folder created a new script with below code in it and made the script file executable and executed the command sudo update-grub in terminal. New entry is added to grub2 but when I select the new entry it shows the ubuntu brown screen after that it throw me an error give below please anyone help me please.....

Please check the screenshot to see the error message

```


cat << EOF
menuentry "Install Ubuntu" {
EOF
cat << EOF
set root=(hd0,1)
loopback loop (hd0,1)/boot/iso/ubuntu-10.04-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.04-desktop-i386.iso noprompt quiet splash 
initrd (loop)/casper/initrd.lz
}
EOF


```

---

### Post by theozzlives on 2010-09-25
Um, why don't you just burn the file to CD and boot off the CD? Just be sure to burn the IMAGE not the file.

---

### Post by elliotn on 2010-09-25
yes burn that image into a CD and install via live cd

---

### Post by vipin.balakrishnan on 2010-09-25
Hi theozzlives

 I just want to try this. Everytime I need to write a cd for to try different version. Can you or anyone help me why this error is..

---

### Post by azertyh on 2010-09-25
hi,
if you have a problem with burning cd, try unetbootin. you can install ubuntu from iso with it. and it's very easy.

---

### Post by vipin.balakrishnan on 2010-09-25
Hi all,

 I know to install from cd. Can anyone help me on this issue..

---

### Post by theozzlives on 2010-09-25
If you mount an ISO on your hard drive, then try to install from it, when it gets to formatting the ISO would be gone. I think DOS use to call it a cyclonic redundancy. You can't install by mounting an ISO, if you don't want to waste CDs, go USB or CD-RW. I know, with all the Alphas, Betas, and RCs, I wasted about 6 CDs/version.

---

### Post by vipin.balakrishnan on 2010-09-25
Hi theozzlives,

It is possible !!!! .I found a solution...  I'm just sharing with you all

I have done a small change in grub script

```


cat << EOF
menuentry "Ubuntu Install" {
EOF
cat << EOF
set root=(hd0,1)
loopback loop (hd0,1)/boot/iso/ubuntu-10.04-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper file=/cdrom/preseed/ubuntu.seed quiet splash 
initrd (loop)/casper/initrd.lz
}
EOF

```

Copied casper and .disk to (hd0,1) 

Thats it It will boot with the iso image... No need of usb drive..

---

### Post by vipin.balakrishnan on 2010-09-26
Hi theozzlives,

 I can able to do that in VirtualBox. In created an NTFS partition there I kept my iso image. So that image will not get formated while installing

Thank you all..

---

