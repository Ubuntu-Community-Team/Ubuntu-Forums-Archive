---
title: "Remove data from external H.D. without changing UUID"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by mikodo on 2011-07-28
Hi, I want to remove the data from an external HD, that I have been using as a backup. A screenshot below is attached of the /media/UUID/**Duplicity backup files.**

I want to preserve the UUID and I don't think reformatting the drive will preserve it.

Deleting each entry of duplicity individually, would take forever!

Any quick solutions to this?

Thanks.

---

### Post by ingeva on 2011-07-28
> **mikodo said:**
> Hi, I want to remove the data from an external HD, that I have been using as a backup. A screenshot below is attached of the /media/UUID/**Duplicity backup files.**
I want to preserve the UUID and I don't think reformatting the drive will preserve it.
Deleting each entry of duplicity individually, would take forever!
Any quick solutions to this?
Thanks.
Yes, formatting would change the UUID.
However, going into terminal mode and use "rm -r <maindirectory>", possibly with sudo " preceding the command, should remove the complete directory and subdirectories very quickly. The "rm" command leaves nothing in the trash bin, so nothing more is necessary. The contents will be gone forever. Be aware.

---

### Post by mikodo on 2011-07-28
> **ingeva said:**
> Yes, formatting would change the UUID.
However, going into terminal mode and use "rm -r <maindirectory>", possibly with sudo " preceding the command, should remove the complete directory and subdirectories very quickly. The "rm" command leaves nothing in the trash bin, so nothing more is necessary. The contents will be gone forever. Be aware.
Thanks I was just reading about "cd" into the directory and then using the "rm" command. I cannot just highlight them all then send them to trash, I found.

I have never used these commands so, I need to read more about them to be *sure*

Thanks ingeva

---

### Post by wildmanne39 on 2011-07-28
Hi, you sure want to be careful with that command if you tell it the wrong directory you can delete your entire ubuntu installation.

---

### Post by mikodo on 2011-07-28
> **wildmanne39 said:**
> Hi, you sure want to be careful with that command if you tell it the wrong directory you can delete your entire ubuntu installation.
Yes, I am not sure how to do it, so I am scared!

rm -r <maindirectory>

Here is the path to all the files:

```
/media/af2dd1ed-2b55-40eb-879d-5158ee37741e/<All the Duplicity files I want to get rid of>

```so, would this remove all the files?

```
sudo rm -r /media/af2dd1ed-2b55-40eb-879d-5158ee37741e/duplicity
```EDIT:  Or, following another forum thread, would this work?

```
cd/media/af2dd1ed-2b55-40eb-879d-5158ee37741e/duplicity
``````
sudo rm -rf *
```Here's the Ubuntu thread I have been following:

[http://ubuntuforums.org/showthread.php?t=1329689](http://ubuntuforums.org/showthread.php?t=1329689)

---

### Post by wildmanne39 on 2011-07-28
Hi, it all looks right except are you sure the files has duplicity in the name at the end of the file? if it does then you should be ok.

---

### Post by Blasphemist on 2011-07-28
The command looks good but me, I'd cd into the directory and make sure my prompt reflects that directory and then issue rm -r

---

### Post by mikodo on 2011-07-28
> **wildmanne39 said:**
> Hi, it all looks right except are you sure the files has duplicity in the name at the end of the file? if it does then you should be ok.

All the files are either called duplicity2 or duplicity new ...

---

### Post by ingeva on 2011-07-28
> **mikodo said:**
> Thanks I was just reading about "cd" into the directory and then using the "rm" command. I cannot just highlight them all then send them to trash, I found.
I have never used these commands so, I need to read more about them to be *sure*
Thanks ingeva
The thing is that if you send them to trash you don't really remove them. They are only moved to another directory (trash). To free up space you would need to use the rm command, or to empty the trash directory after deletion, which takes some time.
If you use "sudo rm -r <directory>" you'll have the directory and everything in it removed effectively, but you'll have very little chance to recover from a mistake, so be sure that you type correctly.
Also, check out "man rm" and "rm --help".

---

### Post by mikodo on 2011-07-28
> **Blasphemist said:**
> The command looks good but me, I'd cd into the directory and make sure my prompt reflects that directory and then issue rm -r

Like this:
    
   ```
   cd/media/af2dd1ed-2b55-40eb-879d-5158ee37741e/duplicity 
```   

    ```
 sudo rm -r duplicity
```

---

### Post by mikodo on 2011-07-28
I am so *nervous* about this, I need to go outside and have a smoke, then I will come in and pull the trigger on one of the "sets" of commands and I will report back.

Thanks everyone.

---

### Post by Blasphemist on 2011-07-28
If you look into the manual and help that was previously posted you'll understand the command and know both how to understand and use the command and, you'll know why we are asking you to be so careful.

---

### Post by bodhi.zazen on 2011-07-28
Just format it , use the -U option

List your partitions by UUID

```
blkid
```

Then format

```
mkfs.ext4 -U UUID_here /dev/sdxy
```

See man mkfs.ext4 

-U does not work with all file systems mind you, see the relevant man pages.

---

### Post by mikodo on 2011-07-28
Well I am not getting to the directory.

```
mikodo@mikodo-desktop:~$ cd/media/af2dd1ed-2b55-40eb-879d-5158ee37741e/duplicitybash: cd/media/af2dd1ed-2b55-40eb-879d-5158ee37741e/duplicity: No such file or directory
mikodo@mikodo-desktop:~$ 

```

I will look at what bodhi has posted.

Thanks.

---

### Post by Blasphemist on 2011-07-29
there is no duplicity directory, just files with that name. Just take the duplicity off of the cd command.

---

### Post by wildmanne39 on 2011-07-29
Hi. you need a space between cd and /media.
```
cd /media/af2dd1ed-2b55-40eb-879d-5158ee37741e
```

---

### Post by mikodo on 2011-07-29
> **bodhi.zazen said:**
> Just format it , use the -U option

List your partitions by UUID

```
blkid
```Then format

```
mkkf -U UUID_here /dev/sdxy
```See man mkfs.ext4 

-U does not work with all file systems mind you, see the relevant man pages.

Didn't work for my external HD.

```
mikodo@mikodo-desktop:~$ sudo mkkf -U af2dd1ed-2b55-40eb-879d-5158ee37741e /dev/sdf1
[sudo] password for mikodo: 
sudo: mkkf: command not found
mikodo@mikodo-desktop:~$ 

```Thanks.

---

### Post by Blasphemist on 2011-07-29
The command should have been mkfs, not mkkf. I do believe the rest is right.

---

### Post by bodhi.zazen on 2011-07-29
> **Blasphemist said:**
> The command should have been mkfs, not mkkf. I do believe the rest is right.

OOps, I fat fingered that one =)

I edited my post , sorry about that

Also, specify a file system mkfs.ext4 or mkfs.vfat ;)

---

### Post by mikodo on 2011-07-29
Thank you everyone for the help!

Sorry for the confusing thread. 

Instead of trying to recap what worked and why some commands didn't work; because of my limited knowledge, I'll just state what did remove the backup data! 

```
sudo rm -r /media/af2dd1ed-2b55-40eb-879d-5158ee37741e
```Fast as a flash the external drive started pecking faster than a woodpecker and the data was gone. The UUID was kept, the drive has a different partition designation (no worries). It mounts and umounts as before. Below is a screenshot of my partitions, the bottom one (dev/sdg1) is the external drive showing empty!

:D

---

### Post by wildmanne39 on 2011-07-29
Hi, your welcome! glad you got it the way you want it.

---

