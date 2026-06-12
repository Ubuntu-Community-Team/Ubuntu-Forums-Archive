---
title: "Need help to repair GRUB(2)"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by edwardLS on 2011-02-25
Using Lucid Lynx 10.04 LTS (i386) on a laptop with a 250GB HDD.

The results of "sudo fdisk -l" are: (omitting the sizes)
dev/sda1 NTFS
dev/sda2 ext4

In the process of getting updates for the Windows XP OS (Dual Boot System) earlier this week, I suddenly lost my GRUB menu, and starting the laptop booted directly into Windows XP.

After three days of attempting to repair this issue, I am about to give up as I feel I may not know enough to make the repair.  I have repaired legacy-GRUB in the past successfully.

I reason that the GRUB installation in the MBR of /dev/sda has been removed and the standard Microsoft MBR replaced it.  Is this reasonalbe?

After trying several methods all with failure, it seems that the most used method is by way of the Lucid Lynx Live CD.  

I have accomplished the following in a booted Live CD from the terminal:
```

sudo fdisk -l
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/dev/sda

```

The last command results in "install_device not specified."
At this point I am in over my head.

Can anyone help me or point to a solution that will clear my head!

---

### Post by Quackers on 2011-02-25
Try a space in between /mnt and /dev

---

### Post by edwardLS on 2011-02-25
Thanks Quackers.

I now have my GRUB menu back, but I still am unable to boot into Lucid Lynx.  I need to do some further research.  It may be that whatever took place to destroy GRUB did more than just that.  BTW:  I manually attempted to recover by running "sudo update-grub".  I was surprised that it did not ask for the password.

---

### Post by Quackers on 2011-02-25
This might give us some ideas. Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by n-n-nebbl on 2011-02-25
> **edwardLS said:**
> 
I now have my GRUB menu back, but I still am unable to boot into Lucid Lynx.

What's the error message?
Or what exactly is the problem booting into ubuntu?

> **edwardLS said:**
> 
I was surprised that it did not ask for the password.


I think you were in the Live-CD Ubuntu?
There is no password you could enter ;)


If your grub starts and you just have booting problems you can edit the /boot/grub/grub.cfg of your ubuntu

My config is:
```

menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e268cee4-43b7-4c36-b551-80ee121113ff
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=e268cee4-43b7-4c36-b551-80ee121113ff ro   splash quiet
	initrd	/boot/initrd.img-2.6.35-25-generic
}

```

old grub was easier to config manually...
you just have to put your partition (where /boot is located) in "set root=...".
the lines starting with "linux" and "initrd" should be similar to your files.

---

### Post by edwardLS on 2011-02-25
All is well now!

The issue was that when I attempted to boot after selecting Ubuntu in the GRUB menu, I eventually got an error message stating that something could not be mounted.  As it turned out, my problem destroyed my /home partition.  I had it backed up to an image, so I restored it, and all is well.  

Thanks all for the helpful advice.

---

### Post by Quackers on 2011-02-25
Glad to hear that :-)
Will you mark the thread as solved please, using the Thread Tools at the top of the page> Thanks.

---

