---
title: "separate partition for home"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by cosine352 on 2009-02-01
Hi friends,
I am using ubuntu 8.10 and having some problem. Si I decided to reinstall it again. I found that it is easy to move the home directory to a new partition. In this way I can reinstall the OS and will not lose my data and configuration. 
So I was trying to follow this 
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am stuck in the process of moving the home to the new partition. This command is not working for me
> find . -depth -print0 | cpio --null --sparse -pvd /new/

This is the out put of fdisk -l
> Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         637     5116671   83  Linux
/dev/sda2            4680        4866     1502077+   5  Extended
/dev/sda3             638        4679    32467365   83  Linux
/dev/sda5            4680        4866     1502046   82  Linux swap / Solaris

you can also see the attach file for the hd formatting. 
I am trying to move the home from /dev/sda1 to /dev/sda3. 
Any help of moving the home to a separate partition will be greatly appreciated. 

Thanks in advance

---

### Post by cosine352 on 2009-02-01
bump

---

### Post by Daveth on 2009-02-01
did you cut and paste that command, or try to be clever and type it in?

---

### Post by cosine352 on 2009-02-01
> **Daveth said:**
> did you cut and paste that command, or try to be clever and type it in?:p:p:p:p:p:p

anyone with better answer ?

---

### Post by tuxxy on 2009-02-01
Whats the error message when you paste the command in
```

find . -depth -print0 | cpio --null --sparse -pvd /new/
```

---

### Post by cosine352 on 2009-02-01
thanks tuxxy for replying. 
The error message is very long but it is mainly some permissing issule. Here is an example

> cpio: cannot make directory `/mnt/newhome//./user': Permission denied
cpio: /mnt/newhome//./user/Pictures: Cannot stat: No such file or directory
cpio: /mnt/newhome//./user: Cannot stat: Permission denied
0 blocks


---

### Post by cosine352 on 2009-02-01
I got it working

> find . -depth -print0 | sudo cpio --null --sparse -pvd /mnt/newhome/

I was missing "sudo" for the "cpio"

---

### Post by tuxxy on 2009-02-01
heh ye I was just about say you could use a sudo there :p

---

### Post by cosine352 on 2009-02-02
thnaks tuxxy:guitar:

---

### Post by EvilRobotDrew on 2009-02-02
[http://ubuntuforums.org/showthread.php?t=986798](http://ubuntuforums.org/showthread.php?t=986798)

in case you have any other issues, or someone else comes across this thread.

BTW, a seperate /home partition is the best thing i have ever done to my computer, at least until 9.04 comes out and i have to format it to ext4 (by "have to" i mean "my inner nerd will compel me").

---

### Post by cosine352 on 2009-02-02
thanks EvilRobotDrew. I will try that too.

---

