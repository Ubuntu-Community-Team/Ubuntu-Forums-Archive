---
title: "How to transfer Grub from one HD to another where Ubuntu is installed?"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by henriquelm on 2010-01-31
I have just installed Ubuntu Desktop 9.10 on my external hard drive, but the installation configured grub on my internal (primary) hard drive, which I didn't wanted. That really s**** cause now ubuntu messed up my Windows 7 boot.

:mad:

So, Is there any way that I can transfer grub to my external hard drive? Or not even have grub at all, and just remove it from my internal hd and just setup my external hd to boot ubuntu?

:confused:

---

### Post by Bucky Ball on 2010-01-31
You could just point the grub to the Windows partition as well so that is included as a choice at boot.

If you want to do that could you possibly open a terminal and paste back here a copy of your grub file and the results of this command:

```
sudo blkid
```

---

### Post by Methuselah on 2010-01-31
Grub usually installs on your boot drive to allow you to switch between ubuntu and windows at boot.
I guess if it installed to the external drive you'd have to switch it to be the first boot device in order to boot into ubuntu (assuming your bios allows booting from such a drive) and then it'd 'mask' the windows drive whenever it's present.

Try booting into ubuntu, opening applications->terminal then typing:
```
sudo update-grub
``` 
Hopefully, this produces and entry in the grub menu to launch windows if it is not already present.

---

### Post by kansasnoob on 2010-02-01
Look what I did here:

[http://ubuntuforums.org/showthread.php?p=8746321#post8746321](http://ubuntuforums.org/showthread.php?p=8746321#post8746321)

Note: realize that your device numbers may be different so unless you're sure please post the output of the Boot Info Script as described there so I can give you the proper commands :)

---

### Post by henriquelm on 2010-02-01
You guys, I already have grub dual booting ubuntu and windows.
The problem is that I don't need nor want grub, cause windows is in one hd and ubuntu is on the other. So as I see, there's no need for a boot loader.

What I really want to know is how I remove grub from my primary hd and direct boot ubuntu on the external hd? This way I can boot windows fast, and whenever I want to boot ubuntu, I will plug my external hd and force to boot on it!

---

### Post by oldfred on 2010-02-01
Use this to reinstall boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Grub wants to install to the drive that is first in boot order. I think if you just do a one time boot from the external the internal is still first so grub installs there. I am not sure if in BIOS you set the external first if grub will only install there?

Someone previously recommended this, I do not know if it works:
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by meierfra. on 2010-02-01
> So as I see, there's no need for a boot loader
Even  if Ubuntu  is the  only operating system, you still need a boot loader. Follow the link  in kansasnoob's post, it's the best solution for your problem. 

Once you completed those instruction, we can  show you how to configure Grub, so that the Grub menu does not appear and you automatically boot into Ubuntu, whenever you boot from  the external drive.

Edit: My next post contains complete instructions for all the required steps,

---

### Post by meierfra. on 2010-02-02
[QUOTE=oldfred]sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.[/QUOTE]
Good point. That is actually missing in kansasnoob's solution. So let me put all the steps together.  


**Step 1 Install a Windows style MBR in the internal drive.**

```
sudo apt-get install lilo
```
(Ignore all messages  and warning you might get. Just press enter)

```
sudo lilo -M [COLOR="Red"]/dev/sda[/COLOR]  mbr
```

[B]Step2 Install Grub to the MBR of the external.
[/B]
```
 sudo grub-install --recheck [COLOR="Red"]/dev/sdb[/COLOR]
```

**Step 3 Make sure that Grub does not get installed to the MBR of the internal drive during kernel/grub updates.**

```
echo "SET grub-pc/install_devices /[COLOR="Red"]dev/sdb[/COLOR]" |sudo debconf-communicate

```

The parts maked in red  assume that the   internal drive is /dev/sda and the external drive is /dev/sdb and so might need to be adjusted. Post the output of "sudo fdisk -lu" if you need help with that.

Once you did those changes you will boot directly into Windows, if you boot from the internal drive;  and the Grub menu will appear if you boot from the external drive. 

If you only have your external drive plugged in to boot into Ubuntu, you should also:

**Step 4 change the  time out period for the Grub menu:**

Open the file /etc/default/grub

```
gksudo gedit /etc/default/grub
```

Change 

GRUB_TIMEOUT="??"

to

GRUB_TIMEOUT="2"

and save the file.

Now  the Grub menu will appear for   2 seconds, in which you can switch to recovery mode  or Windows if you ever need or want to. You can also use "GRUB_TIMEOUT=0", but when you won't be able to get to the recovery mode. Or  you can hide the Grub menu during the time out period, but that's a little bit of a hack.

---

### Post by naval9 on 2010-02-02
You can setup the grub on the external hd itself.
1.```
 sudo fdisk -l
```
2. check the partition where your ubuntu is installed
3. mount the external hard disk using:
   ```
sudo mount /dev/sdXY /mnt
``` where XY are from the table displayed by      fdisk
4. Install the grub on external hard disk
   ```
sudo grub-install --root-directory=/mnt /dev/sdX
```
5. To restore boot loader of windows 7, use the Windows 7 DVD/USB disk and select the repair option->startup repair

Now, you will have the grub on external hard disk, which will only show when the hard disk is connected. Otherwise, windows 7 will boot automatically.

---

