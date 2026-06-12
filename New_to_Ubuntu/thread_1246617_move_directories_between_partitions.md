---
title: "move directories between partitions"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by namluc on 2009-08-21
Hello

[LIST=1]
[/LIST]I have partitioned my hard drive one to many times. I would like to move my music and fspot directories from my primary partition to another partition, and also from my usb drive as well. I cannot seem to use point and click to move the files, do I have to use the terminal. The new partitions are ext3.

I want to give my partitions fixed names but ubuntu won't let me rename them.

Originally i wanted to make my hard drive one, but couldn't do that from within gparted. Is there another way i could do that?

Thanks

namluc

---

### Post by earthpigg on 2009-08-21
> I cannot seem to use point and click to move the files

we will need more details than that, friend.

---

### Post by namluc on 2009-08-22
> **earthpigg said:**
> we will need more details than that, friend.

I mean that when i try and drag the files over to the desired partition, a box comes up telling me permission denied. 

This happened when i formatted my pen drive last night, in the end i had to make it fat32, as ext2-4 locked the drive down. 

I assume that ext2-4 are better than fat32, if not i'll just use that. But i would also like to understand why it isn't working. 

i tried using terminal, but this error message comes up:

> luke@luke-laptop:~$ sudo mv -t &#38899;&#20048;/media/disk/
mv: &#35775;&#38382; &#8220;&#38899;&#20048;/media/disk/&#8221;: &#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;


&#38899;&#20048; just means music
the second line just means that this file or directory doesn't exist


thanks

---

### Post by earthpigg on 2009-08-22
can you write to the partition at all?

try creating a simple text file or something and saving it there.

---

### Post by namluc on 2009-08-22
I have two new partitions, one is ext2 one is ext3. I can write to neither of them. The message that comes up tells me i do not have the privileges to write to these partitions.

---

### Post by earthpigg on 2009-08-22
i believe this will be beyond my ability to help you with. but i am fairly sure those that can help you with it will want to see your fstab:

> cat /etc/fstab

---

### Post by namluc on 2009-08-22
Thanks for your help anyway!

here is my fstab

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f9a0484a-1397-4d5c-8d9d-f71c9d0b35fa /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5c511845-2827-4802-8189-019b45bf5a06 none            swap    sw              0       0

Deeper Recap 


Originally my hard drive was split in to 2, jaunty and intrepid. Jaunty needed more room, and it was getting annoying going into intrepid just to listen to a song every time. So I deleted it. 

After i deleted it i tried to format the new partition to ext3. It failed and the partition in gparted shew up as black. I&#12288;started again, ext2. Still a failure. I then split that partition into three. A linuxswap, and then two 30gig partitions. The first new partition still could not be formatted, but the second new i could make in to ext2.

After a reboot the first new partition was formattable, ext3. But I cannot save anything to it. 

I had the same problem with my thumb drive, that is now fat32 and works fine.

---

### Post by earthpigg on 2009-08-22
wait, you aren't giving these ext3 partitions any crazy and uneeded flags (bootable, etc) by chance, are you?

i usually delete a partiton, apply, then create new partition, apply.... just to ensure nothing is left behind.

---

### Post by gastly on 2009-08-22
hmm...I can't see any other partition in your fstab except / and swap. So I'll assume you're mounting the other partitions manually (by clicking on the drive icons in nautilus...or some other way :P).
By default the partitions are mounted read-only; So you will need to mount them read-write by modifying your fstab file.

Here's a nice little tool you can use to do that: [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)
```

sudo apt-get install pysdm

```

The GUI is pretty self-explanatory :)

---

### Post by namluc on 2009-08-22
[ATTACH]125809[/ATTACH]

here is a picture of my gparted status

I have been mounting everything manually, I didn't realize there was a less painful way to do it. :)i'll have a look at that thing

thanks

---

### Post by namluc on 2009-08-22
Thanks gastly, I have just installed pysdm.

I do not, however, understand the user friendly GUI.&#12288;&#65335;here is the best place to mount my other drives, and what buttons do i press so that it is automatically accessible by myself and the system, without need for passwords.

or whatever lines i need to add to my fstab file are also fine!
thanks

---

### Post by Penguin Guy on 2009-08-22
> **namluc said:**
> &#65335;here is the best place to mount my other drives, and what buttons do i press so that it is automatically accessible by myself and the system, without need for passwords.
Mount them where you want them, so if you want to make a music partition it would make sense to mount it at [COLOR="Green"]~/My Music[/COLOR]. Also, I believe that it will be accessible to you by default, you won't need to press a button. I am not 100% sure about all that though, so you might want to check with someone else.

---

### Post by namluc on 2009-08-22
I've managed to completely screw my computer up. 

I thought that it would be nice to mount my partition on my home account if that is the right name for it (/home/luke/???)

This is working as planned, it mounts at boot with no password required as requested! However it is sitting on top of all of my stuff. Gnome is not loading properly, I can only execute commands via terminal, anything GUI related doesn't work. 

I'm writing this from using lynx via the terminal. 

I would like to know how i can unmount this partition so i can get back in to my account.

I cannot open gparted, because of the GUI.

I logged in as root from safe mode, but i don't know what to do with it.

Please could someone be so kind as to give me step by step instructions that i can write down and follow. 

I do not have a live version of ubuntu lying around!

Thanks in advance

---

### Post by gastly on 2009-08-22
hmmm, you probably should mount your drives in /media/<drive-name> (you will have to create directories yourself tho).

And as for your messed up GUI; try this:

Boot normally and when you're at the Gdm screen press Ctrl+Alt+F2 (this will open a terminal environment).

```
sudo umount -a 
```

Then, Press Ctrl+Alt+F7 to go back to gdm.
And then try to login using gdm. After that you can change the settings in pysdm. I hope this helps :)

---

### Post by namluc on 2009-08-22
the reply to that was

umount: /home/luke: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

what now?

---

### Post by namluc on 2009-08-22
When accessed from the root, the devices are still busy

---

### Post by gastly on 2009-08-22
That command will unmount all the partitions (except the ones that are busy, like / and /home etc.), so if you're having problems logging in, because you mounted the partitions in your /home dir, you will be able to login.

Run the command and then login to gnome and see if you can change the options in pysdm.

---

### Post by namluc on 2009-08-22
Ok thanks gastly, that has cured my catastrophe!!

I was a little worried for a second then.

I am still working on my original problem!

Regards

---

### Post by namluc on 2009-08-22
Well my computer isn't about to explode, but my original problem still remains. I've been playing around with different file systems for a while now and with pydsm as well but i still cannot get my other partitions in to a writable state. 

all i want to do is have somewhere easy and sensible to store my music and photos on my computers fragmented drive

Why is this so difficult??

Here is my fstab

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  defaults                    0  0  
# / was on /dev/sda1 during installation
UUID=f9a0484a-1397-4d5c-8d9d-f71c9d0b35fa  /               ext3  relatime,errors=remount-ro  0  1  
# swap was on /dev/sda7 during installation
UUID=5c511845-2827-4802-8189-019b45bf5a06  none            swap  sw                          0  0  
/dev/sda3                                  /media/bigdisk  ext2  defaults                    0  0  
/dev/sdb1                                  /media/sdb1     vfat  defaults                    0  0  
/dev/sda4                                  /media/sda4     ext3  defaults                    0  0  

/dev/sda3 has been reformatted to ext4. This shows up in gparted but not in fstab, i don't understand why.

---

### Post by gastly on 2009-08-22
You can change the ext2 to ext4 manually. 
```
gksudo gedit /etc/fstab
```

And as for the read-write thing...you will need to do this to actually mount with read-write **after** you change the fstab file.

```

sudo umount -a
sudo mount -a

```

---

### Post by namluc on 2009-08-22
gastly

I've successfully edited the fstab file, thankyou for that.

I've however tried changing the pysdm settings for the last few hours now but still cannot make either of the partitions writable. Could you tell me what lines to insert into the fstab file and so i can change it manually.

Thanks ever so much for your help

namluc

---

### Post by gastly on 2009-08-22
I'm sorry I assumed you had it working using pysdm...
Here's what to do, I searched around a bit and found the solution:

You have two options:

1. Chown the files and directories in /media to your username (i.e Make you the owner of the files) so that only **you** can write to the drive.
```

sudo chown -R <username> /media/bigdisk
sudo chown -R <username> /media/sda4
sudo chown -R <username> /media/sdb1

```

[color="Blue"]Replace the <username> with your username.[/color]

**OR**

2. Chmod the files and directories in /media so that **everyone** can write to the drive.

```

sudo chmod -R 777 /media/bigdisk
sudo chmod -R 777 /media/sda4
sudo chmod -R 777 /media/sdb1

```

I personally recommend the 2nd option **if** you don't have any sensitive or confidential data on the drive.

[color="Blue"]**Note:** If you still can't get the vfat patition to read-write then do this.[/color]

Change the line is your fstab file:
```

/dev/sdb1 /media/sdb1 vfat defaults 0 0
Change this to:
/dev/sdb1 /media/sdb1 vfat fmask=0111,dmask=0000,user 0 0

```

Cheers :)

- gastly

---

### Post by namluc on 2009-08-24
Thanks ever so much for your help gastly. I used the chmod method, and now everything is working the way i want it to!

---

### Post by gastly on 2009-08-24
My pleasure :)

---

