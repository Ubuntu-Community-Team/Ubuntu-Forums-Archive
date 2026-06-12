---
title: "Accessing DVD drive from terminal"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by boldhoof on 2011-04-25
Hi

I need to access a CD through my CDrom drive to install the software for dosbox. Seems it requires you to run the command install from a prompt. If I try doing it via dosbox with the files on the HD it causes an error, but I cannot find the DVD drive via dosbox, nor does the terminal see the dvd drive. The CD is accessible from desktop.

Any easy to follow guides would be excellent, I did try the mount command but not getting very far.

Thanks
Gerry

---

### Post by user1397 on 2011-04-25
> **boldhoof said:**
> Hi

I need to access a CD through my CDrom drive to install the software for dosbox. Seems it requires you to run the command install from a prompt. If I try doing it via dosbox with the files on the HD it causes an error, but I cannot find the DVD drive via dosbox, nor does the terminal see the dvd drive. The CD is accessible from desktop.

Any easy to follow guides would be excellent, I did try the mount command but not getting very far.

Thanks
Gerrytry installing this app: ```
sudo apt-get install nautilus-open-terminal
```I think you have to log out and log back in for it to work but you might need to reboot.  Then right click on the CD icon on your desktop, and click 'Open in Terminal' and then you should be in your CD drive directory.  To see a list of the files on the CD, type ```
ls
```

---

### Post by boldhoof on 2011-04-25
Thanks for the reply. I installed as you mentioned and re-booted. When I right click on the cd it does not give me the option to open in terminal, just open or eject volume, properties or applications but opening terminal through the applications doesn't seem to give me access.

---

### Post by boldhoof on 2011-04-25
Thanks for the reply. Managed to access the CD. The read me says the following regarding running the install "type #:\INSTALL. Replace # with the letter of your
CD-ROM drive" which I can not seem to get it to run install as I dont know the letter.

---

