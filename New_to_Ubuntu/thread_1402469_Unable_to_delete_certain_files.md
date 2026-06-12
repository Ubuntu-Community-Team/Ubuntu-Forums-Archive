---
title: "Unable to delete certain files"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by bharaths_jois on 2010-02-09
Hi guys,

Up on deleting a file, I get the response that the file is not there. But I can open the file and view its contents. The file does not have any special characters.

First of all, the file I am trying to delete is not the file I actually saved.

i.e (Eg)
I had a file lab2.pdf in /media/Tech/Folder1/lab2.pdf

I then saved a file paper2.pdf in /media/Tech/Folder2/paper2.pdf

Then, I don't exactly know how / when, there was no file in /media/Tech/Folder2/ but the same file was in /media/Tech/Folder1/ with the name lab2.pdf. So, now I have lost the actual lab2.pdf and I am not able to delete that bad file lab2.pdf.

Hope I could convey my concern. This has been happening since quite some time. fsck does not help.

OS: Ubuntu Karmic Koala
System: Dell studio 15

Warm regards,
Bharath

---

### Post by Cheezespread on 2010-02-09
Can you do a 'ls' on the directories you are mentioning, Though I am not sure if its a privilages issue ?. Are you getting any errors while you save a file in the directory "Folder2" ?


```
ls -al /media/Tech/
```

Is the Tech folder a mounted external HDD or something ?

---

### Post by bharaths_jois on 2010-02-09
The /media/Tech is an in internal HDD partition and nope, I have the rights, both r/w to the Folder2, thus no errors on saving. Allz fine with that...

---

### Post by Cheezespread on 2010-02-09
What is the name of the file ?. I presume **lab2.pdf** was just an example.I am just trying to see if the name of the file you are trying to delete is the same as you are typing ( incase the file has a long name ).

Try opening a Nautilus window from terminal using sudo and then see if the file persists after deleting ?

```
gksudo nautilus
``` . Please be careful with this.

---

### Post by bharaths_jois on 2010-02-09
Precisely, the path is /media/TechStuph/LiU/TDTS07/Labs/lab2/lab2.pdf.

But the whole problem started probably because of a file with a really long name. and its in the path /media/TechStuph/LiU/ which I am not able to delete either.

---

### Post by Cheezespread on 2010-02-09
Were you able to delete the file in nautilus launched from terminal ?.

If the file you are deleting has spaces in the names ( not in the case of lab2.pdf though ) , you should rather tab-complete it. ( Press tab after entering a small portion of the file name )

Eg:
Cheeze_spread 
Cheez<tab> should do it unless you have another file with "Cheez" as starting letters.

---

### Post by bharaths_jois on 2010-02-09
The su nautilus was also not able to delete the file.

From terminal, this is what I can see:

```

bharath@reveredone:/media/TechStuph/LiU/TDTS07/Labs/lab2$ ls 

AltBitProtocol.xml  exercise.xml  fischer_2.xml  fischer_3.xml  simple.q
exercise.q          fischer_2.q   fischer_3.q    lab2.pdf       simple.xml

bharath@reveredone:/media/TechStuph/LiU/TDTS07/Labs/lab2$ rm lab2.pdf 

rm: cannot remove `lab2.pdf': No such file or directory


```
This time, the rm was followed by la<TAB> to get the auto-completion lab2.pdf. But no success.

---

### Post by bharaths_jois on 2010-02-09
Any suggestions?

---

### Post by Paddy Landau on 2010-02-09
Please type:
```
ls -lqA /media/TechStuph/LiU/TDTS07/Labs/
```and show us the output.

---

### Post by JKyleOKC on 2010-02-09
It looks like "lab2.pdf" is the only pdf file in that directory. If so, have you tried going into the directory and doing "ls *.pdf" to make sure, then doing "rm *.pdf" which should get rid of the file. It's possible that the file name has some invisible control character in it that would not show on the display but would prevent the shell from locating the file without the wildcard reference. This trick also works in many other situations, such as a file whose name begins with a dash...

---

### Post by bharaths_jois on 2010-02-09
@ Paddy: Here it is...
```

bharath@reveredone:~$ ls -lqA /media/TechStuph/LiU/TDTS07/Labs/
total 112
drwxrwxrwx 1 root root  4096 2010-01-26 15:31 lab1
drwxrwxrwx 1 root root  4096 2010-02-09 10:59 lab2
drwxrwxrwx 1 root root  4096 2010-02-09 10:58 lab3
-rwxrwxrwx 1 root root 99344 2010-01-17 23:52 TDTS07_Le1.pdf
bharath@reveredone:~$ 

```

@ JKyleOKC

```

bharath@reveredone:/media/TechStuph/LiU/TDTS07/Labs/lab2$ ls
AltBitProtocol.xml  exercise.xml  fischer_2.xml  fischer_3.xml  simple.q
exercise.q          fischer_2.q   fischer_3.q    lab2.pdf       simple.xml
bharath@reveredone:/media/TechStuph/LiU/TDTS07/Labs/lab2$ rm *.pdf
rm: cannot remove `lab2.pdf': No such file or directory
bharath@reveredone:/media/TechStuph/LiU/TDTS07/Labs/lab2$ 

```

But guys, I can tell you what probably started it all...
```

bharath@reveredone:/media/TechStuph$ ls *.pdf
2009_11_22_1714170744_F68A76D7A640F3251C912922631FE2FF.pdf
2009_11_22.pdf
2010_01_23_1704140819_1BF61985EFC47DE7C5491DC757251956.pdf
2010_01_23_1707160309_1BF61985EFC47DE7C5491DC757251956.pdf
GoodMath.pdf
ubuntupocketguide-v1-1.pdf
bharath@reveredone:/media/TechStuph$ 

```
Those three files there, first signs of the problem showed up after those were downloaded...

---

### Post by Paddy Landau on 2010-02-09
[QUOTE=bharaths_jois;8799369]```

drwxrwxrwx 1 root root  4096 2010-01-26 15:31 lab1
drwxrwxrwx 1 root root  4096 2010-02-09 10:59 lab2
drwxrwxrwx 1 root root  4096 2010-02-09 10:58 lab3
-rwxrwxrwx 1 root root 99344 2010-01-17 23:52 TDTS07_Le1.pdf
bharath@reveredone:~$ 

```Sorry, I didn't realise that lab2.pdf was inside directory lab2. My bad.

Please do this instead:
```
ls -lqA /media/TechStuph/LiU/TDTS07/Labs/lab2/
```

---

### Post by bharaths_jois on 2010-02-09
Here it is 
```

bharath@reveredone:/media/TechStuph$ ls -lqA /media/TechStuph/LiU/TDTS07/Labs/lab2/
total 330
-rwxrwxrwx 1 root root   3409 2010-02-08 23:44 AltBitProtocol.xml
-rwxrwxrwx 1 root root     93 2008-01-04 10:33 exercise.q
-rwxrwxrwx 1 root root   1628 2010-02-08 21:07 exercise.xml
-rwxrwxrwx 1 root root   1304 2010-02-08 22:18 fischer_2.q
-rwxrwxrwx 1 root root   1684 2010-02-08 22:18 fischer_2.xml
-rwxrwxrwx 1 root root    503 2010-02-08 22:43 fischer_3.q
-rwxrwxrwx 1 root root   1578 2010-02-08 22:43 fischer_3.xml
-rwxrwxrwx 1 root root 308407 2010-02-03 00:33 lab2.pdf
-rwxrwxrwx 1 root root     97 2008-01-04 10:33 simple.q
-rwxrwxrwx 1 root root   1905 2010-02-08 21:07 simple.xml
bharath@reveredone:/media/TechStuph$ 

```

---

### Post by Paddy Landau on 2010-02-09
> **bharaths_jois said:**
> ```

-rwxrwxrwx 1 root root 308407 2010-02-03 00:33 lab2.pdf 
```
Thanks.

The 'q' in the ls -lqA would show any funny characters (which is what JKyleOKC was talking about). So, we can see that there are no funny characters.

I'm puzzled as to why your attempts to delete say that the file is not there.

Try this (though I'm not sure that it will work):
```
sudo rm /media/TechStuph/LiU/TDTS07/Labs/lab2/lab2.pdf
```If this doesn't work, then please let us have the results of:
```
lsattr /media/TechStuph/LiU/TDTS07/Labs/lab2/lab2.pdf
```

---

### Post by bharaths_jois on 2010-02-09
Hi,

The sudo rm ... didnt give any positive result either...
But here is the other result:

```

bharath@reveredone:~$ lsattr /media/TechStuph/LiU/TDTS07/Labs/lab2/lab2.pdf
lsattr: Function not implemented While reading flags on /media/TechStuph/LiU/TDTS07/Labs/lab2/lab2.pdf
bharath@reveredone:~$ 

```

I dont think thats helpful now...

---

### Post by bharaths_jois on 2010-02-09
Now, its taking too much of a toll. Any file I save loses its identity and either is lost or is renamed and not deletable.:confused:

All my work... I just save it, and vrrooom, its gone!!

---

### Post by bharaths_jois on 2010-02-09
To improve the information, from my side, 

- My linux is running on a ext2 partition.
- The other OS is Windows Vista and I can delete, move, rename files at the problematic location without any problem.
- I deleted lab2.pdf from windows, but it still appears in Linux and guess what, it has retained its contents even now...!

---

### Post by Cheezespread on 2010-02-09
Had gone for the day yesterday and I was thinking about this alone for the whole day ! I stand a bit helpless here now. SOrry . Looks a bit strange infact even with sudo.

---

### Post by Paddy Landau on 2010-02-10
Yes, something does seem somewhat strange, and I too feel a bit confused.

Please post the results of the command
```
mount
```

---

### Post by bharaths_jois on 2010-02-10
Hi,

I logged on to windows and deleted all the files that were causing the problem. It seems clean (at least for now) on linux. But I cannot be sure until a few more days of work.

I have this Linux running on ext2. And all the other paritions are NTFS. Does that cause a problem?
Can big file names be a problem?

@ Paddy:
Here is the result of 'mount'
```

bharath@reveredone:~$ mount
/dev/sda10 on / type ext2 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda9 on /media/Important type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /media/Setup files type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/Entertainment type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/Media type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/TechStuph type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bharath/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bharath)
bharath@reveredone:~$ 

```

---

### Post by Pritamsng on 2010-02-10
are you deleting as that user which create that file. not sure then log in as root and try to delete. 
go to specific folder by " cd <path> and do rm -rf <folder name> f stands forcefully.

---

### Post by Paddy Landau on 2010-02-10
OK, I'm sorry, at this point, as with Cheezespread, I don't know how to progress.

> **bharaths_jois said:**
> I logged on to windows and deleted all the files that were causing the problem. It seems clean (at least for now) on linux. But I cannot be sure until a few more days of work.
Well, at least that's done!

> **bharaths_jois said:**
>  I have this Linux running on ext2. And all the other paritions are NTFS. Does that cause a problem?
No problem. Ubuntu can easily mount and access NTFS.

Why ext2, though? That's a really old format. I would suggest ext4 for Karmic, which you said you use.

> **bharaths_jois said:**
> Can big file names be a problem?
No problem if Windows has saved the file. See Wikipedia's [Comparison of file systems]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits").

> **Pritamsng said:**
> are you deleting as that user which create that file...
I don't think that's the problem, as it's NTFS mounted with the nosuid option.

What I suggest at this point is to get Windows to check the NTFS partitions for errors. I don't remember off-hand how to do it in Vista; I think that for each partition, you right-click and select Properties, then Tools, then Check disk for errors. Something like that, anyway.

Do that for every NTFS partition (not for the ext2 one!); you may have to reboot Vista in order to complete the checks, in which case the reboot may take a long time.

(You can do this check from Linux, but at this point I'd recommend using Windows.)

---

### Post by bharaths_jois on 2010-02-10
@ Pritamsng:

Yes, I was the user who created the file, and now trying to delete it... But it was still a problem...

@ Paddy:

Thank you very much for your views and support on this. And yes, I guess I moved on with ext4. :)

---

### Post by bharaths_jois on 2010-02-10
@ Cheezespread: Thank you too!!

I hope this can be marked solved until it pops up next...

---

