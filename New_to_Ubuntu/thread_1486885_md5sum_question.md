---
title: "md5sum question"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by oaridus on 2010-05-18
Hi, I burned a 10.04 latest ubuntu on a cd but the cd doesnot work on boot. It gets stuck at the ubuntu icon and the 5 dots. I am trying to check that the md5sum of the cd is fine or not. How do I do it? I was trying to follow the steps in the following site 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

But I am confused with one thing. It says
md5sum /dev/cdrom
will give wrong result which I understand. Then it asks to calculate the actual size of the .iso file on the cd using the command 

ls -l ubuntu-8.10-desktop-i386.iso

Now I don't see a .iso file in the cd folder. It contains many folders 
including md5sum.txt. where do I type this line in the command prompt.
Once the size is known the next line is clear. So please let me know how
to do this stuff.

---

### Post by Chesamo on 2010-05-18
The .iso file isn't *on* the CD. The .iso file *is* the CD.

Something easier would be to use the "Check disc for defects" on the first screen.

---

### Post by CharlesA on 2010-05-18
You can find the MD5SUM of the ISO here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/) depending on which release you are using.

---

### Post by lovinglinux on 2010-05-18
> **oaridus said:**
> Then it asks to calculate the actual size of the .iso file on the cd using the command 

ls -l ubuntu-8.10-desktop-i386.iso

Now I don't see a .iso file in the cd folder. It contains many folders 
including md5sum.txt. where do I type this line in the command prompt.
Once the size is known the next line is clear. So please let me know how
to do this stuff.

Is not on the cd. That is the ISO you have download. Basically it is telling that you first need to calculate the size of ISO to use it as a reference when checking the CD content, because the CD hash is different due to the empty space at the endo of the disk.
Anyway, that is a little bit complicated. Would be simpler to just check the ISO and burn it again if the hash is OK.

If you wan to make that process easier, use [CheckIt](http://checkit-extension.blogspot.com/) extension for Firefox (I'm the developer btw).

If your second burned disc still fails to boot, then use the alternate CD, instead of the Live CD.

---

### Post by oaridus on 2010-05-18
ok I see. I have deleted the .iso file after burning and therefore the question. So if the .iso file was still there, I basically calculate the exact size of it and then use the next command given on the site (dd if=/dev/cdrom bs=1 count=732766208 | md5sum) to check my cd. That makes sense. thanks a lot!!

Another question I had was if the md5sum of the .iso is wrong whom do I let it know to fix this on the server. How do I contact system adminstrator of the particular country in this case India.

---

### Post by CharlesA on 2010-05-18
The only thing to really do if the MD5SUM is incorrect is the download the iso again and check it again.

---

### Post by WinterRain on 2010-05-18
Let's say you've downloaded an iso and it is on your desktop. Simply do:
```
md5sum ~/Desktop/name_of_file.iso
```
and visually compare it to the official md5. Then set your cd burning app to verify after burning.

---

### Post by lovinglinux on 2010-05-18
> **oaridus said:**
> Another question I had was if the md5sum of the .iso is wrong whom do I let it know to fix this on the server. How do I contact system adminstrator of the particular country in this case India.

Most likely a problem on your side. Download it again.

---

### Post by daniell59 on 2010-05-18
> **WinterRain said:**
> Let's say you've downloaded an iso and it is on your desktop. Simply do:
```
md5sum ~/Desktop/name_of_file.iso
```
and visually compare it to the official md5. Then set your cd burning app to verify after burning.

I am also having a problem with the Ubuntu CDs that I have burned. 
I would appreciate it if you would expand upon your explanation.
I have already wasted an abundance of CDs. 

Thanks

---

### Post by maybeway36 on 2010-05-18
Download the ISO again, then check the md5sum of that ISO file. If it is the same as the official MD5, it's a good ISO and it will work.

---

### Post by CharlesA on 2010-05-18
Also, don't forget to burn the cd at the slowest speed.

I have had no problems when burning at 48x, but better safe than sorry.

---

### Post by oaridus on 2010-05-19
I have another question. Say I received CD from someone and I don't have .iso file on my computer, how do I check the size of the .iso file to check the intergrity of the cd. I need to issue two commands 

ls -l ubuntu-8.10-desktop-i386.iso


dd if=/dev/cdrom bs=1 count=732766208 | md5sum

Now the 732766208 number is known only if I  have the .iso file in the computer. But since I just received the CD and not the .iso file, how do I check the CD's is right.

---

### Post by lovinglinux on 2010-05-19
> **oaridus said:**
> I have another question. Say I received CD from someone and I don't have .iso file on my computer, how do I check the size of the .iso file to check the intergrity of the cd. I need to issue two commands 

ls -l ubuntu-8.10-desktop-i386.iso


dd if=/dev/cdrom bs=1 count=732766208 | md5sum

Now the 732766208 number is known only if I  have the .iso file in the computer. But since I just received the CD and not the .iso file, how do I check the CD's is right.

Boot form the CD and choose the option to verify CD integrity from the CD menu.

---

