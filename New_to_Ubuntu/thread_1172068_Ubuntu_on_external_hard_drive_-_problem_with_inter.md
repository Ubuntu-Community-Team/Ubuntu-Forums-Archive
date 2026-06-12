---
title: "Ubuntu on external hard drive - problem with internal hard drive"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Skrean on 2009-05-28
I installed Ubuntu Intrepid on an external USB hard disk using the instructions at pendrivelinux.com.

Each time I plug in and start thru USB, the Internal hard disk of the computer cannot be opened..Its shows the hard disk as '1xx GB media' in 'places' menu but does not open when clicked. Instead it gives me the following error:

Drive cannot be mounted..according to /etc/mtab sda1 already mounted

Is there no way of bypassing the problem by treating the internal hard disk as though it is connected through a USB port...?


This happens in all the computers in which I've plugged the drive..


Any suggestion on how to solve this problem would be welcome..thanks

---

### Post by Zimmer on 2009-06-14
What does the command
sudo fdisk -l  (that is a lowercase L ) 

tell you?

---

