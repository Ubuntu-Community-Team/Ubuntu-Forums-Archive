---
title: "What Do You Use as an ISO Burning APP ?"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by mikodo on 2009-08-05
Hello everyone,
  
In Ubuntu; What is thought to be the best ISO Image Burning Application(s). I would like to stick to ones in the repositories.

Thank you.

---

### Post by pmlxuser on 2009-08-05
K3b, Brasero Disc burner

---

### Post by mikodo on 2009-08-05
> **pmlxuser said:**
> K3b, Brasero Disc burner

That's what I thought I would hear about!

Was just curious if any others were available and well thought of.

Thank you.

---

### Post by credobyte on 2009-08-05
Brasero ( GnomeBaker seems to be a little buggy on burning ISO's ).

---

### Post by 3rdalbum on 2009-08-05
Right-click the disc image and choose "Burn to Disc". (this actually invokes Brasero, but it doesn't feel like a different program).

All programs that burn ISO files just use growisofs as the backend.

---

### Post by Katalog on 2009-08-05
Brasero here.

---

### Post by mikodo on 2009-08-05
> **3rdalbum said:**
> Right-click the disc image and choose "Burn to Disc". (this actually invokes Brasero, but it doesn't feel like a different program).

All programs that burn ISO files just use growisofs as the backend.

Didn't know about growisofs. I'll read about it!

Thanks

---

### Post by Dan_Dranath999 on 2009-08-05
Brasero.

---

### Post by louieb on 2009-08-05
I just right click the iso, choose **write to disk** and off it goes.  lol - just works for me - guess I really should find out what the default program is.  Works for burning CDs and DVDs.

---

### Post by wizard10000 on 2009-08-05
> **credobyte said:**
> Brasero ( GnomeBaker seems to be a little buggy on burning ISO's ).

Everybody's experience is different but I've had better luck with gnomebaker than I have with brasero.

---

### Post by Shig on 2009-08-05
I just use growisofs for DVDs... nice and simple. :D

To burn an ISO file (test.iso) to the first optical drive (/dev/sr0) you would simply type the below in a terminal after navigating the to the directory containing test.iso:
```
growisofs -Z /dev/sr0=test.iso
```

---

### Post by Pierrot Lafouine on 2009-08-10
I was using k3b, but now try to use growisofs to automate backup of source code.  So far, I have failed to find appropriate options, I have trouble with Rock Ridge !!!

I may stick with k3b longer... lol

---

### Post by ZankerH on 2009-08-10
I don't use disks, but I do use dd to mount iso images, I believe it can also be used to burn them to disks.

---

### Post by mikodo on 2009-08-14
> **ZankerH said:**
> I don't use disks, but I do use **dd **to mount iso images, I believe it can also be used to burn them to disks.

Sorry; What is dd?

Thanks.

---

### Post by slakkie on 2009-08-14
k3b

---

### Post by mikodo on 2009-08-14
> **slakkie said:**
> k3b

Thanks!

---

### Post by relay_man on 2009-08-14
K3b has worked perfectly every time for me and is easy to use.

---

### Post by andrew.46 on 2009-08-14
Hi Pierrot,

> **Pierrot Lafouine said:**
> I was using k3b, but now try to use growisofs to automate backup of source code.  So far, I have failed to find appropriate options, I have trouble with Rock Ridge !!

Some parts of this page may help out with that:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

Andrew

---

### Post by marcgh on 2009-08-14
I'm always using K3b, nerver let me down and with near perfect results!

---

### Post by raymondh on 2009-08-14
brasero and/or k3b

---

### Post by HotShotDJ on 2009-08-14
Another vote for K3B -- I've been using it for years and have never had any reason to look further for most of my burning needs.  Although, looking at other posts, perhaps I should be using right-click -> "Write to Disk" for simply burning ISO files.

---

### Post by konqui on 2009-08-14
k3b on kubuntu here

---

### Post by MrWES on 2009-08-14
> **mikodo said:**
> Hello everyone,
  
In Ubuntu; What is thought to be the best ISO Image Burning Application(s). I would like to stick to ones in the repositories.

Thank you.

For command line, try wodim: [http://kurinchilamp.kurinchilion.com/2009/08/how-to-burn-iso-image-from-ubuntu-command-line.html]("http://kurinchilamp.kurinchilion.com/2009/08/how-to-burn-iso-image-from-ubuntu-command-line.html")

```
wodim dev=/dev/cdrw driveropts=burnfree -v -data cd_image.iso
```

Bill

---

### Post by rabbi burns on 2009-08-14
gnome baker x1 speed works for me

---

