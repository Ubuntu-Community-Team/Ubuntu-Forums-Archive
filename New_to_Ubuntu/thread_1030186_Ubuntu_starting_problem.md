---
title: "Ubuntu starting problem"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by viladkarab on 2009-01-04
I am having dual boot. I upgraded to 8.10 and been using it for many days happily. Today I did some playing in Start Up , that has created a mess. Now, when I start laptop, and select Ubuntu, I get following: - 

Booting Ubuntu 8.04.1, Kernel 2.6.24-19-Generic
Filesystem is ntfs,partition 0x7,
kernel/boot/vmlinuz-2.6.24-19-generic root=UUID=0084F28084F2278C loop=/Ubuntu/disks/root.disk ro quiet splash
Error 15: File not found
Press any key to continue

When I press, I get following; - 

GRUB4005 0.4.3 2008-04-22, Memory: 639K/1006M,CodeEnd: 0x41228

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-(recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-16-generic
Ubuntu 8.04.1, kernel 2.6.24-16-(recovery mode)
Ubuntu 8.04.1, memtest86*
Other operating system:
Microsoft Windows XP Professional.

Whenever I select anything, nothing happens except I get error 15 message. 

I am in a fix. What should I do? Pls help me somebody. 

Regards.

---

### Post by Elfy on 2009-01-04
Boot the livecd - opena terminal and run ```
sudo fdisk -l
```

IT will give list of partitions, one will look similar to
 > 
/dev/sda2             552        2675    17061030   83  Linux
Replace the sdxy below with your correct partition 

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp
```

Assuming that has reported no errors - run this and post the result

```
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2009-01-04
You make a reference to "GRUB4005 0.4.3", so it looks like you might be using Grub4DOS; is your Intrepid installed inside Windows as a Wubi install? 

In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might

---

### Post by viladkarab on 2009-01-04
Thanks for the replies. But unfortunately, I am unable to boot from LiveCD. Now what next?

---

### Post by viladkarab on 2009-01-04
Initially i had loaded 8.04 from Wubi. Then I upgraded to 8.10. I have made necessary changes to my boot order, but despite of this, 8.10 CD does not boot, neither 8.04.

---

### Post by viladkarab on 2009-01-04
I cleaned my CD-drive with lens cleaner CD. Now the system booted from LIVE CD. I installed fresh 8.10 from the same.

---

