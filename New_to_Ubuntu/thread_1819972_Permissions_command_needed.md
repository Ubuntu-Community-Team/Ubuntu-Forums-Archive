---
title: "Permissions command needed"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by nnjond on 2011-08-07
Hi,

I cannot mkdir on an ancillary HDD 


:/media/eeeb4ef8-a57b-40c2-b830-78adf552941e$ mkdir Lax
mkdir: cannot create directory `Lax': Permission denied
nnjond@nnjond-laptop:/media/eeeb4ef8-a57b-40c2-b830-78adf552941e$ cd /
nnjond@nnjond-laptop:/$ chmod 777 /media/eeeb4ef8-a57b-40c2-b830-78adf552941e/ 
chmod: changing permissions of `/media/eeeb4ef8-a57b-40c2-b830-78adf552941e/': Operation not permitted
nnjond@nnjond-laptop:/$

---

### Post by snip3r8 on 2011-08-07
sudo mkdir Lax?

---

### Post by ~!geek!~ on 2011-08-07
Command mentioned in above post will help you to solve your problem i.e. creating the directory. But it seems you want to create directories, copy files n directories in the hdd without using sudo each time. To do this you may want to own the hdd. 
If this is the case you may want to do this: 
> sudo chown <username 'nnjond' in this case> /media/eeeb4ef8-a57b-40c2-b830-78adf552941e  -R

---

### Post by idoitprone on 2011-08-07
> **nnjond said:**
> Hi,

I cannot mkdir on an ancillary HDD 


:/media/eeeb4ef8-a57b-40c2-b830-78adf552941e$ mkdir Lax
mkdir: cannot create directory `Lax': Permission denied
nnjond@nnjond-laptop:/media/eeeb4ef8-a57b-40c2-b830-78adf552941e$ cd /
nnjond@nnjond-laptop:/$ chmod 777 /media/eeeb4ef8-a57b-40c2-b830-78adf552941e/ 
chmod: changing permissions of `/media/eeeb4ef8-a57b-40c2-b830-78adf552941e/': Operation not permitted
nnjond@nnjond-laptop:/$

Is the filesytem ntfs?
If it is then all the commands will not work
Try to mount it as a normal user because since ntfs does not understand permissions, by default, it set permissions upon mount

---

### Post by Serpher on 2011-08-07
> **idoitprone said:**
> Is the filesytem ntfs?
If it is then all the commands will not work
Try to mount it as a normal user because since ntfs does not understand permissions, by default, it set permissions upon mount

False. You're thinking of file permissions using the chmod and chown commands. Linux is capable of making and removing files and directories in an NTFS filesystem.

---

### Post by idoitprone on 2011-08-07
> **Serpher said:**
> False. You're thinking of file permissions using the chmod and chown commands. Linux is capable of making and removing files and directories in an NTFS filesystem.

ummmmmmmm?????? yep. that was exactly what i was thinking. Now i am confused. Do you agree with me or disagree with me?

---

### Post by Morbius1 on 2011-08-07
This is a UUID of a linux filesystem not NTFS or FAT32:
> /media/[COLOR=Blue]eeeb4ef8-a57b-40c2-b830-78adf552941e[/COLOR]If I had to vote on who has likely the correct answer it would be:
> **snip3r8 said:**
> sudo mkdir Lax?

---

### Post by Paqman on 2011-08-07
> **Morbius1 said:**
> 
If I had to vote on who has likely the correct answer it would be:

What's the point in making a directory you can't put any files in? Taking ownership of the whole drive as suggested by ~!geek!~ would be much more practical.

---

### Post by Morbius1 on 2011-08-07
The original question was:
>  I cannot mkdir on an ancillary HDD 
We don't know the intent or content of the HDD to offer more than an answer to that specific question.

---

### Post by fdrake on 2011-08-07
i guess it's time to mark this as "SOLVED",,,

---

