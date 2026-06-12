---
title: "Ubuntu 10.10.boot/grub/menu.lst missing"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by karthik.chopper on 2011-04-10
Hey guys, i am pretty new to editing this boot thingie. I updated ubuntu regulary yesterday and now it shows me 2 ubuntu boot options and 1 windows instead of the actual 1 ubuntu and 1 windows.

I checked on the net and they said go to /grub/boot/menu.lst but there is no such file

If i use the gedit it opens a brand new file for me.

The laptop still boots as of now. I just want to remove that extra ubuntu boot option as it is annoying as if i have 2 ubuntu installations on my drive

a point by point description would be rather helpful.

---

### Post by DaveMcC on 2011-04-10
This will fix you

[http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/](http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/)

Be careful with it

Dave

---

### Post by garvinrick4 on 2011-04-10
*That is 2 kernels of linux in one install that shows up in grub menu. That is good to have at least 2. 
What happens if a new one that comes out does not work and you threw old one out.
*No menu list anymore that was in old version of grub called legacy now you have grub2
and it does not have the menu list.
*To see your grub menu entrys: In a terminal
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by wep940 on 2011-04-10
For what you want to do, the above and other links will help you.  However, if you're interested or if someone reading the thread is interested, Ubuntu has been using grub2 for a while now and it doesn't work like the old grub.  You don't have a menu.lst file to edit (the file is there with a different name, but you don't edit it now).  I would suggest those interested search the web for a guide to grub2.  I think there is even a how-to type thread on the forum.

---

### Post by karthik.chopper on 2011-04-11
@garvinrick4: i have one query. What did you mean by 2 kernels??? i didnt get that part. It is showing me the same text in both the lines of the boot screen. and there are 2 memory checks. and 1 windows 7

(PS. I am not talking about the recovery mode option. Now there are 2 of them also)

This is what i have

menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda2)" {

---

### Post by oldos2er on 2011-04-11
You have two kernel versions,  2.6.35-28 and  2.6.35-27. Kernel upgrades will always create a new grub entry, so that you can boot the old kernel if there is a problem with the new one. I personally leave at least two kernels.

There is a GUI program available to edit grub2, Grub Customizer. [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by karthik.chopper on 2011-04-14
oh... ok... thanks man.. So i can delete the oldest kernel once i have more than 3 kernels right???

---

### Post by oldos2er on 2011-04-14
You can delete all but one kernel now, if you want. It's up to you.

---

