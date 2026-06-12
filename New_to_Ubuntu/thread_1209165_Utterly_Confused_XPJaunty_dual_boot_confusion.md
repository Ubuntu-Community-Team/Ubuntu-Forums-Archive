---
title: "Utterly Confused XP/Jaunty dual boot confusion"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by annie227 on 2009-07-10
#-oI had,until yesterday,Jaunty(32) installed thru' Wubi in my XP pro and after reading related posts,and instructions booklet,around the forum,I thought it was time to install side by side on C;160g ide in case anything nasty happenned to XP.
It IS straight forward but installed on D:500g sata and didn't work at all,though I know it's there.
I figured that will need a format(later)so I unplugged it and tried again,giving Ubuntu 25g on C:
Now,in properties it now says C: is 128 g and options come up when booting and Ubuntu is there,as is XP but when I try to install the updates the error message says there's only a matter of MB available.Strangely enough I was able to install a couple of programs thru' add/remove.........?
So,before spending further hours formatting and reinstalling I am hoping there is a solution here-I AM A NEWBIE but very keen.
-AMD athlon 64 dual core
5600+core processor
2 G ram
2.91GHZ
160g C: IDE
D:500g SATA
Ext:320g SATA
-I am guessing I will need to format the 500g or is there another way I can remove it easily enough?"easy" being the operative word. 
I'd also like,if poss not to have to reinstall my xp,who am I kidding,of course i don't!I am very much over that phase in my life,hence this sincere desire for Ubuntu.
Thankyou(face melting into keyboard)
I've forgotten how to fix the display on my 22inch so I'm trying to answer on a less than desirable screen res at the mo,sorry

---

### Post by Peter09 on 2009-07-10
can you post the output of the terminal command

```
df -h
```

---

### Post by Bucky Ball on 2009-07-10
Also the output of:

```
fdisk -l
```... and:

```
nano /boot/grub/menu.lst
```Just in case, to open a terminal: Applications->Accessories->Terminal

The stuff at the bottom of the last file (menu.lst) where the lines don't start with '#' are the important bits. 

The 'menu.lst' file tells us what you have to select at boot and where exactly it is booting from (what drive/partition (represented in Linux as sd1,1 = Windows hd0,0)), and the command 'fdisk -l' tells us how you have your drives partitioned and what file format is on each partition. Another similar command is:

```
sudo blkid
```'sudo' makes you root for the command that follows it (ruler of the universe, capable of changing anything on the system, which is why you don't want to be root permanently). Basically, su=superuser and do=do. Superuser do.

'blkid' identifies the block devices in your machine (hard drives, optical drives, etc.).

Well, you said you were keen! Welcome to the learning curve ...


You can copy and paste the commands into a terminal and copy and paste the output back here. Ctl/C and Ctl/V to copy and paste respectively, but in the terminal, SHIFT/Ctl/C and SHIFT/Ctl/V, or mark and select from 'Edit' menu.

You can also do a neat thing by selecting text, copy, then click the scroll wheel where you want to paste! I only discovered that the other day; sorry if it is old news ...

Also, what version of Ubuntu? 
 
:)

---

### Post by annie227 on 2009-07-10
> **Peter09 said:**
> can you post the output of the terminal command

```
df -h
```

computer@computer-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5              19G   19G     0 100% /
tmpfs                 976M     0  976M   0% /lib/init/rw
varrun                976M  104K  976M   1% /var/run
varlock               976M     0  976M   0% /var/lock
udev                  976M  144K  976M   1% /dev
tmpfs                 976M  464K  975M   1% /dev/shm
lrm                   976M  2.4M  973M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
computer@computer-desktop:~$ 
computer@computer-desktop:~$ 

is this what you mean?
Thanks
bear with me while I get my monitor organised-it's blooming impossible and it's getting late here(not good idea when tired)

---

### Post by annie227 on 2009-07-10
computer@computer-desktop:~$ fdisk l

Unable to open l
computer@computer-desktop:~$ computer@computer-desktop:~$ sudo blkid
[sudo] password for computer: 
/dev/sda1: UUID="64B8355DB8352EC4" TYPE="ntfs" 
/dev/sda5: UUID="99ba3a89-92fb-4e0b-a3ca-bb2dae7ec093" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="97e67365-2b90-45e5-a3d7-746e8164a8ff" 
computer@computer-desktop:~$ 


and it's JAUNTY,thanks
> **Bucky Ball said:**
> Also the output of:
```
fdisk -l
```... and:

```
nano /boot/grub/menu.lst
```Just in case, to open a terminal: Applications->Accessories->Terminal

The stuff at the bottom of the last file (menu.lst) where the lines don't start with '#' are the important bits. 

The 'menu.lst' file tells us what you have to select at boot and where exactly it is booting from (what drive/partition (represented in Linux as sd1,1 = Windows hd0,0)), and the command 'fdisk -l' tells us how you have your drives partitioned and what file format is on each partition. Another similar command is:

```
sudo blkid
```'sudo' makes you root for the command that follows it (ruler of the universe, capable of changing anything on the system, which is why you don't want to be root permanently). Basically, su=superuser and do=do. Superuser do.

'blkid' identifies the block devices in your machine (hard drives, optical drives, etc.).

Well, you said you were keen! Welcome to the learning curve ...


You can copy and paste the commands into a terminal and copy and paste the output back here. Ctl/C and Ctl/V to copy and paste respectively, but in the terminal, SHIFT/Ctl/C and SHIFT/Ctl/V, or mark and select from 'Edit' menu.

You can also do a neat thing by selecting text, copy, then click the scroll wheel where you want to paste! I only discovered that the other day; sorry if it is old news ...

Also, what version of Ubuntu? 
 
:)

---

### Post by annie227 on 2009-07-10
computer@computer-desktop:~$ sudo blkid
[sudo] password for computer: 
/dev/sda1: UUID="64B8355DB8352EC4" TYPE="ntfs" 
/dev/sda5: UUID="99ba3a89-92fb-4e0b-a3ca-bb2dae7ec093" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="97e67365-2b90-45e5-a3d7-746e8164a8ff" 
computer@computer-desktop:~$ 

> **Bucky Ball said:**
> Also the output of:

```
fdisk -l
```... and:

```
nano /boot/grub/menu.lst
```Just in case, to open a terminal: Applications->Accessories->Terminal

The stuff at the bottom of the last file (menu.lst) where the lines don't start with '#' are the important bits. 

The 'menu.lst' file tells us what you have to select at boot and where exactly it is booting from (what drive/partition (represented in Linux as sd1,1 = Windows hd0,0)), and the command 'fdisk -l' tells us how you have your drives partitioned and what file format is on each partition. Another similar command is:

```
sudo blkid
```'sudo' makes you root for the command that follows it (ruler of the universe, capable of changing anything on the system, which is why you don't want to be root permanently). Basically, su=superuser and do=do. Superuser do.

'blkid' identifies the block devices in your machine (hard drives, optical drives, etc.).

Well, you said you were keen! Welcome to the learning curve ...


You can copy and paste the commands into a terminal and copy and paste the output back here. Ctl/C and Ctl/V to copy and paste respectively, but in the terminal, SHIFT/Ctl/C and SHIFT/Ctl/V, or mark and select from 'Edit' menu.

You can also do a neat thing by selecting text, copy, then click the scroll wheel where you want to paste! I only discovered that the other day; sorry if it is old news ...

Also, what version of Ubuntu? 
JAUNTY
 
:)

---

### Post by b@sh_n3rd on 2009-07-10
> **annie227 said:**
> computer@computer-desktop:~$ fdisk l

Unable to open l
computer@computer-desktop:~$

Hi **annie227**, in reply to the error above, did you append a *dash* to "l"?? As in, "fdisk -l"?

---

### Post by Peter09 on 2009-07-10
According to df -h you have a 19GB partition which is full ...... things to check

Empty the trash
System->Admin->Computer Janitor  ---  see if you have a lot of things that you can delete
Application->Accessories->Disk Usage Analyzer to examine your disk usage

---

### Post by Bucky Ball on 2009-07-10
Thanks annie227. And as b@sh mentioned, yes, it is with the hyphen:

```
fdisk **-**l
```Now could you post:

```
nano /boot/grub/menu.lst
```, please?

---

### Post by LewRockwell on 2009-07-10
while running the LiveCD you can take a screen shot of the partition manager and then attach it to your next post

IIRC, it's System > Administration > Partition Manager

and to take the screen shot it's somewhere close in one of the application menus

***Note to self: If possible, always give a GUI solution AND a CLI solution***

.

---

### Post by annie227 on 2009-07-10
er,no,didn't use dash,will do.
Thanks for your patience.

---

### Post by annie227 on 2009-07-10
computer@computer-desktop:~$ fdisk -l
computer@computer-desktop:~$ 
as you see did it again and this is all it came up as.........

---

### Post by annie227 on 2009-07-10
ran system janitor and nothing at all came up
disk analyzer says 96.1%,18.2GB used.
also having a heck of a time with the monitor as I can't adjust it and the vital update packages keep coming up and sitting there,of course unable to install-including the nvidia driver.
I originally set the installation at 25.1 G.
if I have to reinstall is there any way it can be done within the allotted partition?
-I also defragged and chkdsk'd f before the install

---

### Post by annie227 on 2009-07-10
I tried and tried for the screenshot so I copied the data
partition       file system            size
/dev/sda1      ntfs                 128.95G
/dev/sda2      extended          20.10G
/dev/sda5      ext.3               19.22G
/dev/sda6      linux-swap       902MB

---

### Post by Peter09 on 2009-07-11
In disk analyzer you need to dig around to find out what is using all the space, for a straight install 19GB is far to much.

---

### Post by b@sh_n3rd on 2009-07-11
Hi, I find the fdisk command unresponsive too, but appending sudo to that gave me results. I tried it today when checking something and that's how *I* discovered that :D As for the screenshot you could hit "Print Scrn" on your keyboard and Ubuntu would respond after a second's delay and ask you where to save the file.

According to your manual disk layout, is sdb1 your /home partition? I've heard that using NTFS for a linux partition is a bad idea but can't rightly remember why. The /home partition would be no harm though I'd suppose...

---

### Post by Bucky Ball on 2009-07-12
Once more, could you post the result of:

nano /boot/grub/menu.lst

:)

---

