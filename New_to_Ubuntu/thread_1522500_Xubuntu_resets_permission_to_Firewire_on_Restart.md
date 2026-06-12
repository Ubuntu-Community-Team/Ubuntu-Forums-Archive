---
title: "Xubuntu resets permission to Firewire on Restart"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by avast on 2010-07-02
It seems Xubuntu keeps on resetting the permission settings for the  1394 driver after I restart. Each time I have to sudo thunar and change  it to Read & Write, but it changes it back to none after the  restart. I was wondering why that is and what would be the best way to  stop this from happening?

 Thanks in advance!

---

### Post by sisco311 on 2010-07-03
Hi and welcome to the forums!

What are the default permissions of the device?
```
ls -al /dev/**name**
```
where **name** is the name of the device.

If the video group has read/write permissions then simply add your user to the video group:
```
sudo gpasswd -a user video
```
where **user** is your login name.

Log out and log back in. 

Otherwise you have to create an udev rule. Check out the community doc:
[uhelp]community/Firewire[/uhelp]
the ArchLinux wiki: 
[http://wiki.archlinux.org/index.php/Udev](http://wiki.archlinux.org/index.php/Udev)
and
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

If you are unsure how to write the rule, open a terminal and post the output of:
```
sudo udevadm info -a -p $(sudo udevadm info -q path -n /dev/**name**)
```
Replace **name** with the name of the device.

You have to create a new file for the rule, run:
```
gksu mousepad /etc/udev/rules.d/99-custom-1394.rules
```
to create the file and open it in the text editor.

To set the permissions you need something like:
```
KERNEL=="raw1394", GROUP="video", MODE="0664"
```

NOTE: This sets read/write permissions for root and the video group and read permissions for others, so you may have to add your user to the video group.

---

### Post by avast on 2010-07-12
That worked perfectly! Thanks for the help.

---

### Post by sisco311 on 2010-07-12
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

