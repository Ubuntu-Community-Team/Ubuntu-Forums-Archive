---
title: "Ubuntu 11.04 Installation"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Maese909 on 2011-08-26
Hey guys. I have just finished getting Ubuntu 11.04 onto my CD and have successfully "tried" it out. Now I just started to install it but came upon a screen titled Allocate Drive Space. On this screen it says Quit Back and Install Now. I clicked Install Now and it says "No root file system is defined. Please correct this from the partitioning menu." 
I have no idea what this means so any help os very much appreciated. 
 
P.S. I want to install it so that I can use Windows 7 and Ubuntu both, so at boot time I can choose which OS to use. I already have Windows 7 on this machine.

---

### Post by Actonix on 2011-08-26
What OS are you in at the moment ?

Windows 7 or the Live CD ?

---

### Post by Maese909 on 2011-08-26
I am on the Live CD

---

### Post by coffeecat on 2011-08-26
@Maese909, I read you other thread and I see that the installer offers you only replace Windows and "something else". Normally it will offer you an option to install Ubuntu next to Windows as well. I suspect that your manufacturer has used up the 4 primary partitions limit and that is why you are not getting the side-by-side option. More advanced partitioning would be needed, such as you can do in the "something else" option, but you need to know a bit about partitioning.

From the live CD, open the application Gparted. Be careful not to do anything with any of your partitions. Gparted is a full-featured partitioner. All we want is a screenshot. When the Gparted window is on screen, press Alt-PrintScr to get a screenshot of the Gparted window. Please post this, which will show us the partition layout on your machine.

Also - you might find this link useful:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

