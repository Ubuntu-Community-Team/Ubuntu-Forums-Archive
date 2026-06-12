---
title: "grub rescue"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by toddken on 2011-05-11
hello there!
 
I read about "grub rescue", but none solved my problem. 
New to Ubuntu 10.10, just installed it on Win XP, but I think I messed up everything. 
I have the following:
 
device        Boot      Start               End               Blocks           ID      System
/dev/sda1     *          63             40965749         20482843+      7    HPFS/NTFS
/dev/sda2               40965750    78140159         18587205         f    W95 Ext'd   (LBA)
/dev/sda5               40965813    78140159         18587173+      7    HPFS/NTFS
 
If i normally turn on my laptop, I get "grub rescue>"
 
I could access the terminal using a disc: ubuntu 10.10 on the "try" option. Could not even install the disk. Boot not found
 
Thanks

---

### Post by deonis on 2011-05-11
you can use any other ubuntu disks. Grub rescue operation is quite standard. check this out: [http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/](http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/)

---

### Post by toddken on 2011-05-12
[LEFT]Hello Deonis!
 
I am getting an error after finding my root partition. I typed:
"sudo mount --bind /dev/media/AC88B4BA88B483FC/ubuntu/dev" and got an error message:
"mount: can't find /dev/media/AC88B4BA88B483FC/ubuntu/dev in /etc/fstab or /etc/mtab.[/LEFT]

---

### Post by Hedgehog1 on 2011-05-12
We need to get a look at what shape your system is in.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

p.s. Unless you installed Ubuntu on a second disk, I wonder of you managed to install Grub and no Ubuntu at all...

---

### Post by deonis on 2011-05-12
> **toddken said:**
> [LEFT]Hello Deonis!
 
I am getting an error after finding my root partition. I typed:
"sudo mount --bind /dev/media/AC88B4BA88B483FC/ubuntu/dev" and got an error message:
"mount: can't find /dev/media/AC88B4BA88B483FC/ubuntu/dev in /etc/fstab or /etc/mtab.[/LEFT]


please make a space between /dev and  /media/AC88B4BA88B483FC/ubuntu/dev

cheers...

---

### Post by toddken on 2011-05-12
your link is not working.
So there is no way I could just roll back to XP? I gave you my prompt, and thought that a series of codes will easily fix it. I think my XP is no more on my laptop.
Please help

---

### Post by wilee-nilee on 2011-05-12
> **toddken said:**
> your link is not working.
So there is no way I could just roll back to XP? I gave you my prompt, and thought that a series of codes will easily fix it. I think my XP is no more on my laptop.
Please help

See link 4 again that script is the most likely tool that will get you the answers you need. 

A line of code will not just magically fix this without more information, the script provides all this information.

At the least boot a ubuntu live cd open gparted and look if XP is there.

---

### Post by audiomick on 2011-05-12
The partition info you posted in your first post shows only windows partitions, so there is a chance that your xp is still there.

Follow Hedgehog's advice and post the results.txt back here. That tells you pretty much all you need to know to solve problems like those you are having.

---

### Post by deonis on 2011-05-12
what is wrong with something like: df -h in terminal ? why does he/she need a script?

---

### Post by wilee-nilee on 2011-05-12
> **deonis said:**
> what is wrong with something like: df -h in terminal ? why does he/she need a script?

I see no Linux install.
```
/dev/sda1 * 63 40965749 20482843+ 7 HPFS/NTFS
/dev/sda2 40965750 78140159 18587205 f W95 Ext'd (LBA)
/dev/sda5 40965813 78140159 18587173+ 7 HPFS/NTFS

``` 

What we have here is more then likely a wubi install, that has put grub in the mbr. We ask for the boot script, because we want solid evidence to act with not just throwing out code with conjecture.

This is a standard problem with wubi, and there is a megathread with the fix.

Basic care for the OP, getting their set up working is what comes first.;)

---

### Post by deonis on 2011-05-12
Thanks, I see now :)

---

### Post by toddken on 2011-05-12
Sorry guys I tried both codes, and it is not working.
But when I put the second one #```
 su 
``` it asks for a password

---

### Post by toddken on 2011-05-12
When I turn on my Laptop I directly get the prompt "grub rescue"

---

### Post by wilee-nilee on 2011-05-12
And?;)

---

### Post by toddken on 2011-05-12
nothing has changed

---

### Post by wilee-nilee on 2011-05-12
> **toddken said:**
> nothing has changed

Hmm, well maybe if you post the text from the bootscript we could help you.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Not sure what you have been doing, but no legitimate instructions have been posted, none really, a nothing is changed really means nothing.

I think I know the problem, but I don't advise without being sure.

At the least your going to need a recovery or install disc for the windows, and a Ubuntu disc to run the script.

The Ubuntu disc can fix this if it is a reload of the mbr that is needed. Do not try without the correct instructions though, unless you are fully aware of what you're doing. If you put any Linux bootloader in any of those partitions shown you will be in real trouble.

---

### Post by toddken on 2011-05-12
I could not find the (#) you mentioned. Here is the response after downloading the file on my laptop. It shows under laptop as Example.

```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

```

---

### Post by toddken on 2011-05-12
I believe I put the loader in one partition if not all. Not sure at the beginning I tried a lot of things before discovering the forum

---

### Post by wilee-nilee on 2011-05-12
> **toddken said:**
> I could not find the (#) you mentioned. Here is the response after downloading the file on my laptop. It shows under laptop as Example.

```

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

```

So for that script command to work the downloaded file should be on the desktop so drag it there and run the command again.

This is the reply window, and this is the (#) for creating code tags, paste all the text from the file generated when you have run that command with the bootscript on your desktop.
[ATTACH]191985[/ATTACH]

Thanks we are almost there, let me know if you have a recovery or install disc on the MS , and if you have a Ubuntu disc. Or either loaded to a usb thumb and can be booted.

---

### Post by toddken on 2011-05-12
I just got it. I forgot how to get into a directory in linux. This is my result:
#
```

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda5/Wubi for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop

```

I could not get into the result folder

---

### Post by toddken on 2011-05-12
Tried the following to get into result: 
#
```

ubuntu@ubuntu:~$ /home/ubuntu/Desktop/RESULTS.txt
bash: /home/ubuntu/Desktop/RESULTS.txt: Permission denied
ubuntu@ubuntu:~$ cd /home/ubuntu/Desktop/RESULTS.txt
bash: cd: /home/ubuntu/Desktop/RESULTS.txt: Not a directory
ubuntu@ubuntu:~$ cd .../home/ubuntu/Desktop/RESULTS.txt
bash: cd: .../home/ubuntu/Desktop/RESULTS.txt: No such file or directory
ubuntu@ubuntu:~$ 

```

---

### Post by toddken on 2011-05-12
Sorry has to go to sleep. midnight on the East Coast here. Your help is very valuable to me. Will catch up tomorrow night.
Have a nice one

---

### Post by bcbc on 2011-05-13
look on the desktop, double click on the file RESULTS.txt

Or from command line:
```
gedit /home/ubuntu/Desktop/RESULTS.txt
```
(case sensitive)

---

