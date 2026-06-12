---
title: "Recover Lost Disk Space"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by olddai on 2010-10-13
At the moment i am getting online via a Live CD after a failed attempt to install Ubuntu 10.10. i failed because i don't have enough disk space (i think). So i opened a terminal and typed in the following:

sudo find / -type d -name '*Trash*' | sudo zargs du -h | sort

and i got the following output:

ubuntu@ubuntu:~$ sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
find: File system loop detected; `/mnt/temp/mnt/temp' is part of the same file system loop as `/mnt/temp'.
0    /home/ubuntu/.local/share/Trash/expunged
0    /home/ubuntu/.local/share/Trash/info
588M    /home/ubuntu/.local/share/Trash
588M    /home/ubuntu/.local/share/Trash/files
588M    /home/ubuntu/.local/share/Trash/files/Downloads
ubuntu@ubuntu:~$

Could someone please tell me how i might clear/purge this trash. Thanks

---

### Post by ibizatunes on 2010-10-13
home/ubuntu/.local/share/Trash/

isnt this your live disc ubuntu home folder??

you need to mount your old harddrive 
then cd your old harddrive then your old home directory (and any other home directory on your hardrive to clear some more space) and then cd .local/share/Trash/files/

the sudo rm -rf *.*

(or open nautilus as root) and do the same actions in the GUI
that might work

---

### Post by olddai on 2010-10-13
I don't understand it but when i open the Disk User Analyzer i can see that the total file system capacity is 144 GB (Used: 2.7 GB and available: 141.8 GB)

Isn't there some way i can clear the hard drive of everything on it and then start from scratch so-to-speak?

---

### Post by ibizatunes on 2010-10-13
just install your ubuntu 10.10 over the top and do a format, that will clear it completely!
tip ,put / on separate partition of about 10gb  and the rest a /home that way you don't need backup your data when rebuilding your computer , you just reinstall on top of / 
just remember to back your own personal data up first before formatting!

---

