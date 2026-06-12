---
title: "Will WUBI Installer erase my drive?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by megalight on 2011-03-03
Hello everyone, I'm a Windows User for about 10 years and I decided to try Linux (Ubuntu) because it seems interesting, but I need a little help before starting.
I have two drives, C (Windows OS) and D (Data), I decided to use WUBI to install Ubuntu in D, it says that it will be installed as a Windows application but I'm worry about losing my data, I have a huge amount of data that I keep in D Drive, so I'm asking: Would WUBI installer erase my entire partition or it will only use some space?
Thanks.

---

### Post by maqtanim on 2011-03-03
No ... Wubi does not delete anything. It will create a folder named "Ubuntu" (or something like that) in your D drive and put ubuntu related everything there.

---

### Post by megalight on 2011-03-03
Thank you very much!

---

### Post by Rex Bouwense on 2011-03-03
Using WUBI to install Ubuntu merely installs it like any other program that you would install on a Microsoft system.  While you will get an idea about using Ubuntu, it will not be as responsive and has been been know to do some weird things, it will not over write your data as the previous poster has stated.  You will be able to see it in your add/remove programs list.  Enjoy.

---

### Post by mastablasta on 2011-03-03
note that wubi is ment just for trying and do not update any grub packages.
 
also i suggest you read a bit about Ubuntu in the Ubuntu Manual.

---

### Post by beew on 2011-03-03
If you really want to try Ubuntu give it full control by installing side by side with Windows or install it in an external hard drive (then you don't change anything in your internal hard drive or the Windows installation,--unlike WUBI which has to be installed in Windows,--you can run Ubuntu by booting into it from almost any machine) WUBI is a crippled and castrated shadow of the real thing. It is a program in Windows and as others pointed out there are things you can't do in WUBI so you are not really trying Ubuntu.

---

### Post by robgraves on 2011-03-03
depending on how much hard drive space you have, you could shrink the windows partition and make the remaining free space an ubuntu installation.  i started with a wubi installation myself and found it to act unpredictably, so i created its own partition and did a proper install.

---

