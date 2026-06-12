---
title: "File defragment in Windows"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by user_linux on 2011-08-01
Hi,
I'm defragmenting my Windows XP,but my wubi 10.04 file is large and it can't be defragmented. What can I do to defragment it?

Thanks.

---

### Post by Rex Bouwense on 2011-08-01
Ubuntu has a different file system, ext4, and should not be affected by the Microsoft Windows defrag.

---

### Post by user_linux on 2011-08-01
Ok, so what you're saying is I can just leave it alone?

---

### Post by oldos2er on 2011-08-01
Wubi installs to a file on your Windows partition. You can use jkdefrag to defragment from within Windows.

download jkdefrag [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

unzip
run: jkdefrag c:\ubuntu (or c:\wubi in 7.04 and above)

The above taken from [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by lordievader on 2011-08-01
You installed Ubuntu through Wubi, right? This indeed creates a file on your Windows drive.

Did you try to defrag this file with the standard defragmentation tool from Windows? If so perhaps you can try to defrag the file with a different program like Defraggler, from [http://www.piriform.com/defraggler](http://www.piriform.com/defraggler)

---

### Post by Rubi1200 on 2011-08-01
> **oldos2er said:**
> Wubi installs to a file on your Windows partition. You can use jkdefrag to defragment from within Windows.

download jkdefrag [http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

unzip
run: jkdefrag c:\ubuntu (or c:\wubi in 7.04 and above)

The above taken from [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
I second this suggestion. 

The software mentioned should be more than capable of getting the job done.

---

### Post by Frogs Hair on 2011-08-01
Programs like Auslogics or Smat Defrag for windows can see and count the Ubuntu clusters , but can't do anything with them .

---

### Post by psusi on 2011-08-01
> **Frogs Hair said:**
> Programs like Auslogics or Smat Defrag for windows can see and count the Ubuntu clusters , but can't do anything with them .

It is a file just like any other.  It should not have any trouble defragging it.

---

### Post by philinux on 2011-08-01
> **user_linux said:**
> Hi,
I'm defragmenting my Windows XP,but my wubi 10.04 file is large and it can't be defragmented. What can I do to defragment it?

Thanks.

Wubi is meant to be used as a try ubuntu and not for long term use. If you intend using ubuntu on a regular basis you should now consider dual booting with a proper install.

---

### Post by madjr on 2011-08-01
hm, the time it takes to defrag that big file, i would probably just reinstall ubuntu (maybe a new version and maybe to its own partition to place it off windows :))

---

