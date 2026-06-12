---
title: "ubuntu won't boot, GRUB4DOS?"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by bunta123 on 2009-12-23
Hello ubuntu users,  I have a dual boot with vista and forced a hard shutdown, now I can't boot into ubuntu 9.10.  It's installed through wubi.  I have the live cd, but do not know what to do next.  HELP!

---

### Post by FreezWay on 2009-12-23
not sure if this will work but try holding shift while booting. do you have grub or grub2

---

### Post by bunta123 on 2009-12-23
not exactly sure but i have all these files that i do not want to lose and i don't want to reinstall, i just want to fix it and log into ubuntu again.

---

### Post by bunta123 on 2009-12-23
can anyone help? i have so many important documents there that cannot be erased!!!!!!

---

### Post by drs305 on 2009-12-23
> **bunta123 said:**
> Hello ubuntu users,  I have a dual boot with vista and forced a hard shutdown, now I can't boot into ubuntu 9.10.  It's installed through wubi.  I have the live cd, but do not know what to do next.  HELP!

[COLOR="DarkRed"]Note: Only for Grub 2, which you may or may not be using. [/COLOR]

Can you get to the Grub 2 menu? If so, try what I found worked for me in this post:
[http://ubuntuforums.org/showpost.php?p=8385203&postcount=62]("http://ubuntuforums.org/showpost.php?p=8385203&postcount=62")
It's post 62. You can click on the link at the upper right of the post to see the entire thread if you need to.

If you have questions, ask them in this post (yours).

---

### Post by bunta123 on 2009-12-23
yes i can get into the grub menu.  it lists this,

find /ubuntu/disks/boot/grub/menu.lst
find /ubuntu/install/boot/grub/menu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst

followed by commandline, reboot, and halt.

grub>

---

### Post by gcc2011 on 2009-12-23
Does the Live CD can not help you to get your material back?

What's the error message when you boot?

Is it something like this "[SIZE=4][COLOR=#ff0000]one or more of the mounts listed in /etc/fstab cannot be"?
[COLOR=Black]
If so, when you boot, press ESC to enter recovermod shell, and input this:
[/COLOR][/COLOR][/SIZE][SIZE=4]sudo mount -o remount,rw /
sudo dpkg --configure -a[/SIZE]

Otherwise, wait for other guys to help you:guitar:

---

### Post by bunta123 on 2009-12-23
can i access the files on vista?

---

### Post by garvinrick4 on 2009-12-23
At vista command line "bcdedit'  without qoutes. There should be a boot that
says Wubi in it. 
  	 	 	 	 	 	  

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

---

### Post by bunta123 on 2009-12-23
> **garvinrick4 said:**
> At vista command line "bcdedit'  without qoutes. There should be a boot that
says Wubi in it. 
  	 	 	 	 	 	  

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

do i create the win directory at root "/"? or the home directory?

---

### Post by bunta123 on 2009-12-24
sorry i didn't pay attention to the next line, i was in the home directory, when i mounted it said it couldn't because there was no etc/mtab...

any ideas?

---

### Post by bunta123 on 2009-12-24
I found this on wubiguide-

"Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into Windows, run chkdsk /r from Windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again. 

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the Windows Explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location. 

Make sure you did not install on a RAID array or in an encrypted disk. Also make sure you did not install using an Alternate or DVD ISO."

---

### Post by bunta123 on 2009-12-24
EVERYONE!!! thanks for your help!!! i saved my data whew.

the above post did it!! after getting the frustration out of the way and my mind was working again hehe i got a sense of how things were and where the files were supposed to be.  and learned a little something here and there!!! it's a good feeling. yea!!!:popcorn::guitar:

---

