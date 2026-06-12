---
title: "fat 32 partition permissions"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by chriszatch on 2010-05-23
i created a partition just to put all of my data on because i have multiple os's. My problem is that whenever i try to change things on ubuntu, it says that i dont have permission to change things. i tried changing the permissions, but they always revert back to the old ones. i tried chmod and it didnt work either, but i could've typed the wrong stuff in. So, if someone could give me the chmod command to change the permissions, just so i can make sure i entered it in right, i would be grateful. However, if that doesnt work, what should i do? on windows, i can change things in the partition, but not in ubuntu. thanks!

---

### Post by mbzn on 2010-05-23
This is what the entry should be for mounting

This is in the fstab file(use for internal disks)
Go to Applications>Accessories>terminal and enter

gksu gedit /etc/fstab

/dev/sdb1 /media/documents ntfs-3g defaults,locale=en_ZA.UTF-8 0 0

Note this is for a ntfs partition where sdb1 is mounted as /media/documents

so where /dev/sdb1 is the partition
/media/documents is the mount point
and where ntfs-3g you should have vfat

I think that'll work, you could just wait for confirmation from someone that knows better.

---

### Post by chriszatch on 2010-05-23
alright, so my new entry for fstab is 
/dev/sda4  /media/Llama  vfat  defaults,locale=en_ZA.UTF-8 0 0

im gonna try rebooting and see if that makes a difference.

---

### Post by mbzn on 2010-05-23
Fine with me, I cant guarantee that it will work but it's should get you in the right direction.

---

### Post by chriszatch on 2010-05-23
well, that did not work. adding everything in between defaults and 0 0 caused the partition to fail to mount. so i reverted to the old line which was literally what you had said, minus the stuff between defaults and 0 0. any other suggestions?

---

### Post by chriszatch on 2010-05-23
just for clarity, the partition is mounting fine and i can access it fine, but i can not change anything while in ubuntu. 

am i posting this in the right category?

---

### Post by mbzn on 2010-05-23
That was the line i have in my fstab... guess that stuff is for ntfs only then. As i don't know much about mounting vfat I'm out of ideas. 

You can try this [http://ubuntuforums.org/showthread.php?t=219472](http://ubuntuforums.org/showthread.php?t=219472)

or a google "vfat fstab entery" could hold some info.

Good luck

---

### Post by randolf_ambrose on 2010-05-23
> **chriszatch said:**
> alright, so my new entry for fstab is 
/dev/sda4  /media/Llama  vfat  defaults,locale=en_ZA.UTF-8 0 0

im gonna try rebooting and see if that makes a difference.


try this...
**/dev/sda4 /media/Llama vfat iocharset=utf8,umask=000 0 0 **

ref: [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
ref: [http://ubuntuforums.org/showthread.php?t=1471427](http://ubuntuforums.org/showthread.php?t=1471427)

hope it helps...

---

### Post by chriszatch on 2010-05-23
thanks for the help! the last link that mbzn gave me fixed it though. i was just coming back to say that. :D thanks though

---

