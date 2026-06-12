---
title: "Network Share"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by Omnikurt on 2006-10-11
I'm a complete noob at Linux, but so far Ubuntu looks good.

I'm connected to a Windows Server network, and would like to "Map a Network Drive" like you do in windows.  I've been able to connect to a shared resource by entering my Windows User Name/Password, but everytime I go back, I need to browse to it again.  Is there anyway to set up this share as a permanent link in the menu or on the desktop?  Thanks?

---

### Post by dannyboy79 on 2006-10-11
> **Omnikurt said:**
> I'm a complete noob at Linux, but so far Ubuntu looks good.

I'm connected to a Windows Server network, and would like to "Map a Network Drive" like you do in windows.  I've been able to connect to a shared resource by entering my Windows User Name/Password, but everytime I go back, I need to browse to it again.  Is there anyway to set up this share as a permanent link in the menu or on the desktop?  Thanks?

under places, click on connect to server, then you would chose the windows share from the pull down, enter your username and password, then click done or ok and a icon should show up on your desktop. this works for authenticated ftp as well as anony ftp sites and most anything i think. nautilus is really cool that way with the connect to server thingy.

---

### Post by TheWizzard on 2006-10-11
if you want to access this network drive often/always, you can automatically mount it on bootup.

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

if you want only certain users to mount, you should not change fstab, but put a full mount command in a script in the autostart folder. you should put an umount scipt in a directory that runs scripts on logout. in kde this is ~/.kde/shutdown.

---

### Post by dannyboy79 on 2006-10-11
> **TheWizzard said:**
> ]
if you want only certain users to mount, you should not change fstab, but put a full mount command in a script in the autostart folder.

An easier solution is in fact TO modify your fstab with the network drive but use the noauto option along with users, that way you don't have to mess around with a autostart script and whatnot, all a user would have to do is type sudo mount -a which will mount anything in fstab and then of course it would get automatically unmounted upon shut down instead of again having to create a shutdown script. These are just my opinions just like the Wizards suggestions are his opinion or the way he does it. You need to always realize that just because someone offers there suggestion that doesn't mean that't the only way or even the best way, it could just be the only way that person knows how. (I am not saying that The Wizard didn't know about the noauto option within fstab, i am just stating a fact.)

---

### Post by Omnikurt on 2006-10-11
Thank you all for your assistance!  I really am a complete idiot.  After I posted the question, I saw the "Connect to Sever" option in the Places menu.  Prior to that, I was accessing the shares by clicking on Network Servers.  Going through the Connect to Server placed a Folder/Link on my desktop that seems to be there after reboot.  I do have to enter my password after reboot to see the contents though...  Something about keyring needing a password?

Anyway, thanks again!

---

### Post by Iowan on 2006-10-11
Have a look at the 3rd link in my signature.
(I've done it the way you just described, and it seems to work just fine...)

---

### Post by TheWizzard on 2006-10-12
> **dannyboy79 said:**
> An easier solution is in fact TO modify your fstab with the network drive but use the noauto option along with users, that way you don't have to mess around with a autostart script and whatnot, all a user would have to do is type sudo mount -a which will mount anything in fstab and then of course it would get automatically unmounted upon shut down instead of again having to create a shutdown script. These are just my opinions just like the Wizards suggestions are his opinion or the way he does it. You need to always realize that just because someone offers there suggestion that doesn't mean that't the only way or even the best way, it could just be the only way that person knows how. (I am not saying that The Wizard didn't know about the noauto option within fstab, i am just stating a fact.)

it's just that i have different users on my computer so i want the mounting to be user-specific. fstab is cool if there's one user.
cheers

---

