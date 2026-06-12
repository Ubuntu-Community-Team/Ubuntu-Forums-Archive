---
title: "Fresh install?"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by Aero_Zeppelin on 2011-07-23
I encountered kernel panic while booting up..n i think its not something worth solving..so i decided to make a clean install after taking a backup of my files using the live disk..but wen i try to open the home folder of d previous install,i get a message saying i dont have permisson to do so..so my questionis- is there anyway i can take a backup of my files?they are really important to me and may cost me my job if i lose them.please help.

---

### Post by westie457 on 2011-07-23
> **Aero_Zeppelin said:**
> I encountered kernel panic while booting up..n i think its not something worth solving..so i decided to make a clean install after taking a backup of my files using the live disk..but wen i try to open the home folder of d previous install,i get a message saying i dont have permisson to do so..so my questionis- is there anyway i can take a backup of my files?they are really important to me and may cost me my job if i lose them.please help.
 The proper way is to change the ownership of the files and folder using chmod. But I have no idea how to do that.

You either wait for more advice or do the procedure below. The choice is yours. 

In a terminal run ```
gksudo nautilus
```
This will open Nautilus with root privileges.

**Be very careful what you do here** as mistakes EG deleting something are permanent with no recovery option.

Navigate to your old home folder, select all the files you need, copy and paste them into the new home folder or wherever you want them. When finished for your own peace of mind immediately exit Nautilus then close the terminal window.

One other thing you may or may not get some error messages appearing in the terminal, these can be ignored.

PS You might still need to change permissions after this.

---

### Post by Aero_Zeppelin on 2011-07-23
@westie467-thank you very much.iv copied the files to a pendrive..but how do i change the permissions?and should i change the permission now or after installing ubuntu?

---

### Post by Rex Bouwense on 2011-07-23
There is a command that you can use but for the life of me my mind has went blank at the moment.  As a check I would right click one of the files and select properties just to see what the permissions are.  You should be able to change the permissions from there.
See:  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by westie457 on 2011-07-23
Here is something I have tried as an experiment after accidentally copying a directory called gdm into /var/log. the directory gdm has a 'X' on it meaning I cannot look at it in the normal system.

However using a LiveCD  and the terminal and nautilus I mounted the partition using Nautilus in the normal way. Directory 'gdm' properties no access at all with the note at the bottom "You are not the owner. You cannot change permissions".

Then opened a terminal and ran 'gksudo nautilus and navigated my way to the 'gdm' folder. Right-clicked to check the properties and found I now had full access. Clicked at the bottom of the window 'Apply permissions to enclosed files.

Am now going to reboot and check if it worked. 
Will report whether success or failure.

Look for the edit at the bottom of this.

It Failed. And am willing to admit defeat on this as I do not want to give wrong advice and stuff your files completely. 

Now you have a back up of sorts for your files you could try using a LiveCD and adapting what I tried. Moving them from where they are to a different place EG your new /home folder might allow you read and write access.

---

### Post by Aero_Zeppelin on 2011-07-23
@westie -Thank you for your sparing your time for me....is there anyway to change permissions from d terminal,i.e if i manage to copy those files to my new home folder?

---

### Post by westie457 on 2011-07-23
> **Aero_Zeppelin said:**
> @westie -Thank you for your sparing your time for me....is there anyway to change permissions from d terminal,i.e if i manage to copy those files to my new home folder?

Absolutely not sure if this will work.

Found an old thread 2008 that has a similar situation to yours. 

[http://ubuntuforums.org/archive/index.php/t-680709.html](http://ubuntuforums.org/archive/index.php/t-680709.html)

I am not going to be available for a few hours.
If it works could you mark this as solved using 'Thread Tools' to help others in the same boat please.

Good luck

---

### Post by Aero_Zeppelin on 2011-07-23
@westie467 -after a lot of trial and error,i finally succeeded in transferring the backup and in changing the ownership/permissions for those files..i want to elaborate what i did for the benefit of others who might b facing the same situation that i did..heres what i did-firstly i booted from the live cd and used the gksudo nautilus command..then i copied all d files to a pendrive.but was unable to access the files in a different pc because i didnt have necessary permissions..So again i booted from d live cd n copied d files again-this time to a hard disk formatted to ntfs filesystem.I tried accessing the files again on a different pc,i succeeded this time.n when i checked the permissions,it was automatically changed to my username...i think the NTFS filesystem had something to do with this..

---

### Post by westie457 on 2011-07-24
> **Aero_Zeppelin said:**
> @westie467 -after a lot of trial and error,i finally succeeded in transferring the backup and in changing the ownership/permissions for those files..i want to elaborate what i did for the benefit of others who might b facing the same situation that i did..heres what i did-firstly i booted from the live cd and used the gksudo nautilus command..then i copied all d files to a pendrive.but was unable to access the files in a different pc because i didnt have necessary permissions..So again i booted from d live cd n copied d files again-this time to a hard disk formatted to ntfs filesystem.I tried accessing the files again on a different pc,i succeeded this time.n when i checked the permissions,it was automatically changed to my username...i think the NTFS filesystem had something to do with this..

Admittedly a not very elegant way of doing things but YAY. Whatever works is okay by me.
Could you mark this as solved please to let others with a similar problem know there is a working solution.

---

