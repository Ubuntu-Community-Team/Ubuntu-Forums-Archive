---
title: "Mounting FAT32 drives permanently in UBUNTU!"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by jadhav92 on 2009-08-08
Hi friends,

I want to use my files in the other partitions(E:, F: . I'm able to use C: (drive which has win xp installed in it) and D: drive which has got Ubuntu in it.

Now can someone help me to make those E: and F: drive accesible in UBUNTU.

Also give me step by step instructions as i'm completely new to this and have been using XP for some 4-5yrs...

Thanks.....

---

### Post by garikaib on 2009-08-08
First question what type of installatioin do you have. The phrase "Ubuntu in it implies an inside windows installation using wubi"
Second what type of file system are you using for both operating systems.

---

### Post by jadhav92 on 2009-08-08
> **garikaib said:**
> First question what type of installatioin do you have. The phrase "Ubuntu in it implies an inside windows installation using wubi"
Second what type of file system are you using for both operating systems.

I Installed it by downloading the jaunty edition from the website and installing it using a boot CD.

I've four partitions. three of them are FAT32 type and one is EXT2 for Ubuntu Jaunty9.04

---

### Post by garikaib on 2009-08-08
Assuming you have drive D: in ext3 format and Ubuntu on it do the following:

1) Open a terminal from Applications- Accessories menu

2) sudo  gedit /etc/fstab

The file should look something like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7fbf38d3-ff1a-42e8-a01e-af8fbd4a42c5 /               ext3    relatime,erro$
# /dev/sdb5
UUID=6146b972-5008-4833-ac7b-e8091ad58579 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




Edit it by adding a line for  /dev/sda1 so that the line looks like
/dev/sda1  /mnt/windows vfat user,,noauto,exec,utf8 0       0

Save the file.

3) sudo mkdir -p /mnt/windows

That's it!. Everytime you reboot you file will be automounted to the folder /mnt/windows

---

### Post by garikaib on 2009-08-08
Following what i said above only the first FAT32 partition will be automaounted. You need to edit the file /etc/fstab to include lines for the other partitions ie
sda2, sda2 etc... and make mount points for them e.g windows1 windows2 etc.

To see what partion you have you can do an ls of /dev/sd*

Remember to always back up your files b4 any changes!

---

### Post by jadhav92 on 2009-08-08
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=12016258-12c7-4d80-a26e-90b946026d62 /               ext2    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Above thing is what i got. Could you please highligh and show me where to edit or replace....

---

### Post by garikaib on 2009-08-08
Open a terminal and do the following:

ls /dev/sd*>>/$HOME/Desktop/partitions.txt 

Then copy and paste the text that appears on your desktop from the file in your reply so i can see the portions you have.

---

### Post by garikaib on 2009-08-08
Open a terminal and do the following:

ls /dev/sd*>>/$HOME/Desktop/partitions.txt 

Then copy and paste the text file that appears on your desktop from the file in your reply so i can see the portions you have.

---

### Post by Liolikas on 2009-08-08
sudo fdisk -l 
Gives more info.

---

### Post by garikaib on 2009-08-08
Thanks. It is true fdisk -l>>/$HOME/Desktop/partitions.txt gives excellent results!!!

---

### Post by jadhav92 on 2009-08-08
> **garikaib said:**
> Open a terminal and do the following:

ls /dev/sd*>>/$HOME/Desktop/partitions.txt 

Then copy and paste the text file that appears on your desktop from the file in your reply so i can see the portions you have.

hey i tried that, but that does'nt give any result it just goes to the next line to enter any command...

EDIT:

I got it,

> /dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7
/dev/sda
/dev/sda1
/dev/sda2
/dev/sda5
/dev/sda6
/dev/sda7



> **Liolikas said:**
> sudo fdisk -l 
Gives more info.

here it is

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb60db60d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2433    19543041    c  W95 FAT32 (LBA)
/dev/sda2            2434        9729    58605120    f  W95 Ext'd (LBA)
/dev/sda5   *        2434        4866    19543041   83  Linux
/dev/sda6            4867        7299    19543041    b  W95 FAT32
/dev/sda7            7300        9729    19518943+   b  W95 FAT32


---

### Post by Liolikas on 2009-08-08
lol first result same repeated many times.


So now you see:
/dev/sda6 4867 7299 19543041 b W95 FAT32
/dev/sda7 7300 9729 19518943+ b W95 FAT32 
In windows/dos notation it would be D: or E: or etc. in Linux it is /dev/sdaX
**S**torage **d**evice **a** partition number **X**.

Now you have to enter in /etc/fstab new lines something like:
/dev/sda6 /mnt/name vfat noatime 0 0
And so on... idea is:
device place where it should be mounted folder (good idea is do not create mess and use special folder inside /media or /mnt like /mnt/sda6) vfat means fat32 and then options and two numbers are options too.

Then file saved you can test it with:
sudo mount -a
Command. ~This command is executed at every Linux boot.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> lol first result same repeated many times.


So now you see:
/dev/sda6 4867 7299 19543041 b W95 FAT32
/dev/sda7 7300 9729 19518943+ b W95 FAT32 
In windows/dos notation it would be D: or E: or etc. in Linux it is /dev/sdaX
**S**torage **d**evice **a** partition number **X**.

Now you have to enter in /etc/fstab new lines something like:
[COLOR=Red]**/dev/sda6 /mnt/name vfat noatime 0 0**[/COLOR]
And so on... idea is:
device place where it should be mounted folder (good idea is do not create mess and use special folder inside /media or /mnt like /mnt/sda6) vfat means fat32 and then options and two numbers are options too.

Then file saved you can test it with:
sudo mount -a
Command. ~This command is executed at every Linux boot.

hmmm...sorry to ask lot of questions...i'm new to this...

do i have to copy that line in RED to fstab???

---

### Post by Liolikas on 2009-08-08
Yes you be sure that folder /mnt/name exists if not change it to something else or create it.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> Yes you be sure that folder /mnt/name exists if not change it to something else or create it.
actually, where should i create that folder?

---

### Post by Liolikas on 2009-08-08
it gives a reply: Permission denied.
It means that you have to use sudo in front of command.
This is for security only person who knows sudo password can apply important changes to system.

>actually, where should i create that folder?
Where you want it does not matter, but in general as I said folder for this purpose is created inside /mnt or /media.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> it gives a reply: Permission denied.
It means that you have to use sudo in front of command.
This is for security only person who knows sudo password can apply important changes to system.

hey sorry about that... i entered that in terminal instead of fstab....thats the reason for the permission denied...

now i just checked it and entered it in Fstab....

now i get a reply:
> 
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by SuperSonic4 on 2009-08-08
Did you open up gedit as root? To do so ```
gksu gedit /etc/fstab
```

---

### Post by Liolikas on 2009-08-08
Yes, or other ways like:
```

sudo nano /etc/fstab

```
But you have to lean nano editor in this way too.

---

### Post by jadhav92 on 2009-08-08
> **SuperSonic4 said:**
> Did you open up gedit as root? To do so ```
gksu gedit /etc/fstab
```


hey now i opened using this command, it opened up and saved this time..

now what should i do next

> **Liolikas said:**
> Yes, or other ways like:
```

sudo nano /etc/fstab

```But you have to lean nano editor in this way too.

---

### Post by Liolikas on 2009-08-08
Now:
```

sudo mount -a

```
And you will find your contents of drive in folder.
After every reboot too.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> Now:
```

sudo mount -a

```And you will find your contents of drive in folder.
After every reboot too.

Now i get this:

> mount: mount point /mnt/name does not exist
mount: mount point /mnt/name does not exist

---

### Post by Liolikas on 2009-08-08
You have  to create folder /mnt/name ...
```

sudo mkdir /mnt/name

```

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> You have  to create folder /mnt/name ...
```

sudo mkdir /mnt/name

```

Ok. I did this. Whats up next?

---

### Post by Liolikas on 2009-08-08
sudo mount -a

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> sudo mount -a


hey i don't get a reply to that....

check out that screen shot....

---

### Post by Liolikas on 2009-08-08
> **jadhav92 said:**
> hey i don't get a reply to that....

check out that screen shot....

Good it means it works fine. 
In Linux/Unix world you will not see Windows-style messages like:
hey Internet is working!!!

Now you can go to /mnt/name and find contents of your drive always (until you edit /etc/fstab in other ways).

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> Good it means it works fine. 
In Linux/Unix world you will not see Windows-style messages like:
hey Internet is working!!!

Now you can go to /mnt/name and find contents of your drive always (until you edit /etc/fstab in other ways).

where can i find that mnt directory?

---

### Post by Liolikas on 2009-08-08
Ahh in Gnome ... really open this window:
[http://www.breakitdownblog.com/wp-content/uploads/2008/07/ubuntu-810-alpha3-nautilus-file-manager-screenshot.jpg](http://www.breakitdownblog.com/wp-content/uploads/2008/07/ubuntu-810-alpha3-nautilus-file-manager-screenshot.jpg)
(nautilus)
And then click file system. And thre will be mnt folder.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> Ahh in Gnome ... really open this window:
[http://www.breakitdownblog.com/wp-content/uploads/2008/07/ubuntu-810-alpha3-nautilus-file-manager-screenshot.jpg](http://www.breakitdownblog.com/wp-content/uploads/2008/07/ubuntu-810-alpha3-nautilus-file-manager-screenshot.jpg)
(nautilus)
And then click file system. And thre will be mnt folder.

hey thank you very much....i got the F: drive.

so now to get my E: drive do i need to follow the same procedure again?

---

### Post by Liolikas on 2009-08-08
nope ;)
Yes not ideally same just one more different line (I hope you can design it yourself if not just ask) in /etc/fstab and one more folder in /mnt.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> nope ;)
Yes not ideally same just one more different line (I hope you can design it yourself if not just ask) in /etc/fstab and one more folder in /mnt.

i can do the other stuffs all i need to know is which one is F drive...

coz i added SDA6 and SDA7

---

### Post by Liolikas on 2009-08-08
There is two practical methods:
1)guess (add everything and check contents: F not A mostly means big number something like 7 not 1)
2) fdisk -l shows size of everything if you remember size of F: you can find it.

---

### Post by jadhav92 on 2009-08-08
> **Liolikas said:**
> There is two practical methods:
1)guess (add everything and check contents)
2) fdisk -l shows size of everything if you remember size of F: you can find it.

Thank you very much bro....i'll try things out....

once again thanks..

---

### Post by jadhav92 on 2009-08-08
HEy i've a problem now....

Previously i had access to C drive as Media 20gb drive in system it went missing after this..

What could be the problem guys?

EDIT: I've solved it guys ..thanks

btw....all the drives are write protected, is there any options to write and delete files???

---

### Post by jadhav92 on 2009-08-09
any help pls:(

---

