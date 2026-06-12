---
title: "how can i solve this problem"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by sazan on 2009-03-02
Here is the scenario,

I had ubuntu 7.10 and vista dual OS in my HP laptop, yesterday i installed ubuntu 8.10 in a new parition inside Windows (since ubuntu 8.10 also allows us to install ubuntu as an exe in windows ). 

Everything was working fine, when i rebooted I got dual OS list for my old kernel and windows , when i checked windows, i got windows and my new ubuntu and i started that . 

Now when the system was idle my friend here happen to run **rm -rf ./*** to the entire disk where my  ubuntu 7.10 lied, and when i rebooted I got grub 15 error, seems like its still looking for the old kernel, how can i solve this issue .....

---

### Post by Yashiro on 2009-03-02
Get better friends.

---

### Post by sazan on 2009-03-02
ya, after this I will :P

---

### Post by Temposs on 2009-03-02
You'll have to reinstall that partition. It is useless now...

---

### Post by sazan on 2009-03-02
i can do that , but looking for a better solution. I am sure there must be one

---

### Post by diablo75 on 2009-03-02
Your friend essentially deleted every file on your 7.10 partition, which required the use of sudo and entering the password to grant permission.  Short from finding better friends, perhaps you shouldn't give out your password to anybody.  Everything has been lost from that partition.  There is a very slim possibility you can recover files by using a program called photorec, after booting off a Live CD and installing while running your live session, then have it scan the partition which once contained your 7.10 install.  But it's a shot in the dark.

---

### Post by sazan on 2009-03-02
well there wasn't any data which was important in that partition which i want to recover, I just want GRUB 15 error resolved, so that i can get back to my new ubuntu and windows.

Last resort will be installing linux again in the same partition.

---

### Post by Liviu-Theodor on 2009-03-02
If you have an Windows Boot diskette or an Windows text mode installation disk (i.e. for Windows 95/98/XP), run from it:
```
fdisk /mbr
```
This will overwrite the Grub MBR with the Windows one, and you will have access to the Windows/Ubuntu 8.10 menu.
Alternatively, you can download the grub iso from [http://www.gnu.org/software/grub/]("http://www.gnu.org/software/grub/") and work solve with it your problem.

---

### Post by sazan on 2009-03-02
right now i am not in my system, but I would like to try that, can i overwrite the GRUB MBR with the help of the live CD.

---

### Post by Joeb454 on 2009-03-02
You say they ran rm -rf ./* or rm -rf /*

The 2 are **_very_** different commands.

But there are tutorials on reinstalling grub

---

### Post by sazan on 2009-03-02
Thanks for the response.

He ran **rm -rf ./*** staying in **root** , I understand what the difference is, but stayin in root deleted everything.

I just acknowledged that even VISTA uses grub, so can you tell me to reset the MBR to use the GRUB of vista. I would reinstall grub if required, but after that will i be able to use the deleted partition normally for other purposes.

---

### Post by caljohnsmith on 2009-03-02
In order to boot Vista and the Ubuntu installed inside Vista, you'll need to restore a Windows MBR to your HDD. You can do that from a Live CD by doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes or if you run into problems.

---

### Post by sazan on 2009-03-02
hi.. thanks for your resonse..
currently i am not with my system, definitely I will try your suggestion and keep you updated with the result... I hope this works fine.

---

### Post by sazan on 2009-03-02
> **caljohnsmith said:**
> In order to boot Vista and the Ubuntu installed inside Vista, you'll need to restore a Windows MBR to your HDD. You can do that from a Live CD by doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes or if you run into problems.


thanks a lot...the MBR was overwritten, and I can finally run my OS without have to reinstall linux or grub...

---

