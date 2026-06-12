---
title: "password does not match"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by allenl675 on 2011-01-23
Brand new PC, attempting wubi installation. User name came up correctly and I typed the exact PW that I entered originally at PC start up. Received PW does not match. What must I do. Does it make a difference that I have it on another notebook. I am not using same PW. In fact do not know PW I used on old PC. Please advise and thanks

---

### Post by cavh on 2011-01-23
Easiest would simply be to redo the installation, making 100% certain you write down the password correctly (NB the password is case-sensitive).

---

### Post by ubudog on 2011-01-23
> **cavh said:**
> Easiest would simply be to redo the installation, making 100% certain you write down the password correctly (NB the password is case-sensitive).

+1  

That worked for me.

---

### Post by yetiman64 on 2011-01-23
<edit wubi installation sorry - wrong info>

---

### Post by ubudog on 2011-01-23
That is easier, and works also.

---

### Post by bcbc on 2011-01-23
If you've completed the install, then it's easier just to change the password. Boot in recovery mode, select root terminal, and change the password:
passwd <username> 

Where username is the user name provided when you installed (not the one Wubi displays which is actually your windows user account you installed under).
That may be your confusion too - Wubi shows a different user name so you might be confused into entering your windows password. You need to enter the password you supplied when installing Wubi. This is a confusing feature of Wubi.

PS if you can't remember the wubi username, just type "ls /home" (lower case LS).

---

### Post by allenl675 on 2011-01-23
Hey bcbc you got that right totally confused. Lets assume just for a moment I had never used wubi. If they are not getting it from my windows pass word where are they getting it?
Someone said its easier to re-install! Reinstall what windows. I just went through a recovery trying to get a wubi install. Know what the user name generated in the wubi was my user name I just created after recovery.
I know how to partition, but sadly its using gparted only which by way caused me to go into recovery as win 7 will not abide gparted under any circumstances or not for me.
Wish I had more expertise but but seemingly lost all my know how when I lost XP, gparted and extended partitions with logicals to play with. Thanks for your input

---

### Post by sandyd on 2011-01-23
> **allenl675 said:**
> Hey bcbc you got that right totally confused. Lets assume just for a moment I had never used wubi. If they are not getting it from my windows pass word where are they getting it?
Someone said its easier to re-install! Reinstall what windows. I just went through a recovery trying to get a wubi install. Know what the user name generated in the wubi was my user name I just created after recovery.
I know how to partition, but sadly its using gparted only which by way caused me to **go into recovery as win 7 will not abide gparted **under any circumstances or not for me.
Wish I had more expertise but but seemingly lost all my know how when I lost XP, gparted and extended partitions with logicals to play with. Thanks for your input
use windows disk manager (control panel -> administrative tools -> computer management -> disk management)

---

### Post by bcbc on 2011-01-23
Wubi is separate from Windows - it doesn't have any knowledge of your windows password. 

Please avoid reinstalling windows or using system restore in windows when you're trouble shooting Wubi issues. 

Windows user name: wubi uses this as your User Description - Presented at logon
Ubuntu user name: all lower case name you entered in the WUBI GUI when you install.
Ubuntu password: the case-sensitive password you need to enter twice in the WUBI GUI when you install.

When you boot Ubuntu after installing through Wubi you'll see your User Description, not the user name - and the User description is the same as your Windows account.
The password must be the Ubuntu password.

To uninstall Wubi, go to Control Panel, Add/remove programs, and remove "Ubuntu". Reinstalling will uninstall first. Uninstalling deletes the entire Ubuntu install including all data.

Wubi installs Ubuntu onto a virtual disk - a file called root.disk that you can see under Windows - c:\ubuntu\disks\root.disk. This contains your Ubuntu install and you can back it up.

When using Ubuntu, try to avoid updating certain packages. The Update Manager prompts you automatically, but (often way down in the list, under "Recommended") you might see grub-pc and/or grub-common. Avoid updating these.

Please see the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide") for more info.

---

### Post by bcbc on 2011-01-23
> **sandyd said:**
> use windows disk manager (control panel -> administrative tools -> computer management -> disk management)

+1. If you want to install Ubuntu direct without Wubi.

In that case, you cannot use the Windows installer - you need to boot from an Ubuntu CD/USB to install.

Wubi is for installing to a virtual disk only.

---

