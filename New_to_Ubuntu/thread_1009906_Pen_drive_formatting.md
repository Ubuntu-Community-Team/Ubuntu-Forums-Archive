---
title: "Pen drive formatting"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by kubes on 2008-12-13
[CENTER]Pen drive formatting[/CENTER]

I want format my pen drive(usb). How to do it in ubuntu.
In windows its easy..just right click and click on format drive. ut i havent found such option on ubuntu. And yes my windows has crashed, so thats not an option either.

---

### Post by Keith Hedger on 2008-12-13
make sure the drive is unmounted and use mkfs from the command line see the man page for full details - BE CAREFUL - you dont want to accidentally format the wrong drive!

---

### Post by jolx on 2008-12-13
or use gparted

---

### Post by Moop on 2008-12-13
You can use gparted to format the pendrive.

---

### Post by Cincinnatux on 2008-12-15
> **kubes said:**
> [CENTER]Pen drive formatting[/CENTER]

I want format my pen drive(usb). How to do it in ubuntu.
In windows its easy..just right click and click on format drive. ut i havent found such option on ubuntu. And yes my windows has crashed, so thats not an option either.

Kubes, 

My apologies if the following response is excessively detailed.  Your original post does not indicate your degree of familiarity with your options, so I'm assuming you have never used gParted and that you are very new to Linux.  

I'll also say in advance that I'm still new to Linux and there are better/easier/quicker ways to achieve your objective, but the following is the best I can offer given my limited understanding of Linux.

**[SIZE="4"][COLOR="Red"]How to format a USB pendrive/thumbdrive in Ubuntu in five easy steps:[/COLOR][/SIZE]**

**1.  Insert your USB pendrive/thumbdrive into your computer.**
[B]
2.  Open a terminal window. [/B] (In the APPLICATIONS menu, select ACCESSORIES, then select TERMINAL.)

**3.  Start GParted. ** (At the ~$ prompt, enter the command:  **[FONT="Lucida Console"][SIZE="3"][COLOR="DarkOrange"]sudo gparted[/COLOR][/SIZE][/FONT]**.)

**4.  Have GParted display your USB device.**  (Under GParted's GPARTED drop menu, select DEVICES and then look for a listing that shows your USB device's memory.  Select that option.  

**5.  Format the drivespace.**  (Click on the partition window to select the drivespace.  Under GParted's PARTITION drop menu, select UNMOUNT.  Under GParted's PARTITION drop menu, select FORMAT and then choose the format type you need.  Under GParted's EDIT drop menu, select APPLY ALL OPERATIONS.  Close GParted, close Terminal.)

You now have a formatted USB pendrive/thumbdrive.  Please advise if these instructions mislead you in any way or fail to work as claimed.

- Cincinnatux

---

### Post by southbound395 on 2009-08-20
> **Cincinnatux said:**
> Kubes, 

My apologies if the following response is excessively detailed.  Your original post does not indicate your degree of familiarity with your options, so I'm assuming you have never used gParted and that you are very new to Linux.  

I'll also say in advance that I'm still new to Linux and there are better/easier/quicker ways to achieve your objective, but the following is the best I can offer given my limited understanding of Linux.

**[SIZE=4][COLOR=Red]How to format a USB pendrive/thumbdrive in Ubuntu in five easy steps:[/COLOR][/SIZE]**

**1.  Insert your USB pendrive/thumbdrive into your computer.**
[B]
2.  Open a terminal window. [/B] (In the APPLICATIONS menu, select ACCESSORIES, then select TERMINAL.)

**3.  Start GParted. ** (At the ~$ prompt, enter the command:  **[FONT=Lucida Console][SIZE=3][COLOR=DarkOrange]sudo gparted[/COLOR][/SIZE][/FONT]**.)

**4.  Have GParted display your USB device.**  (Under GParted's GPARTED drop menu, select DEVICES and then look for a listing that shows your USB device's memory.  Select that option.  

**5.  Format the drivespace.**  (Click on the partition window to select the drivespace.  Under GParted's PARTITION drop menu, select UNMOUNT.  Under GParted's PARTITION drop menu, select FORMAT and then choose the format type you need.  Under GParted's EDIT drop menu, select APPLY ALL OPERATIONS.  Close GParted, close Terminal.)

You now have a formatted USB pendrive/thumbdrive.  Please advise if these instructions mislead you in any way or fail to work as claimed.

- Cincinnatux

Well this almost answers a question I've been trying to answer. 
My main problem is that I'm not the super user, so i can't sudo... I'm using public computers set up by our apartment manager/owner for his (lucky) tenants to use.

Can anyone tell me how to format a 2GB drive pen drive  without being the super user?

---

### Post by pedro3005 on 2009-08-20
Use a LiveCD and it will let you.

---

### Post by LewRockwell on 2009-08-20
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

.

---

