---
title: "Error Mounting Windows Share in fstab"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Nrgh on 2008-04-28
After upgrading to 8.04 I am having an issue mounting a Windows Share in fstab.  Previously I've had this working in 6.10, 7.04, and 7.10.  I've always followed the directions posted here: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently).  The problem occured after doing an upgrade from 7.10, which I had previously upgraded from 7.04.  Figuring it was time to start fresh, I reformatted and installed 8.04.  Got the same error.  Anyways heres the error:

mount error 20 = Not a directory

First thing I did was a 'sudo apt-get install smbfs'.  I created a new directory to mount the share on in my home folder called 'storage'.  The name of the server is 'storage' and the name of the share is 'public', the servers IP address is listed in my host file with the alias 'storage'.  I created a file called '.smbcredentials' in my home folder with the correct user name and password for the share.  The line I added to fstab looks like this:

//storage/public /home/me/storage smbfs credentials=/home/me/.smbcredentials,uid=1000 0 0

and my .smbcredentials looks like this:

username=correctusername
password=correctpassword

I then did a 'sudo mount -a' and got the error posted above.  I switched the smbfs to cifs just to test, since the directions in the url I linked above provide both.  Also tried using the IP address of the server instead of the alias.  Got the same error.

On a side note, I used to get this same error in 7.10 when I tried using cifs to mount the share.  Using smbfs worked perfectly however.

---

### Post by mlewis-everley on 2008-04-28
I am mounting windows shares perfectly in Hardy. For some reason it took the windows server a while to except the authorization though, for me a couple of hours and several re-boots later and then it just started working.

I am using CIFS rather than SMBFS to mount the filesystem however. I am not sure if that is a possible cause of your problems (I used to have a lot of problems getting anything to mount using SMBFS in previous versions of Ubuntu).

Hope thats of some help,

Mo

---

### Post by gpeck157 on 2008-04-29
Hi,
I was having a similar problem but is now resolved and my Windows shares are mounted automatically every time I log in. Here is a copy of what I have in my /etc/fstab file:

> //192.168.1.102/Dad /media/Dad smbfs credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777 0	0


Here is my /root/.smbcredentials file:
> 
username="defaults"
password="defaults"

I hope this helps...

---

### Post by Nrgh on 2008-04-29
Thanks for the replys, still haven't been able to get it working.  I can connect to the share from Places->Connect to Server, so that might just have to get me by.  Only reason I really want a static mount is so I can import my music library into Rhythmbox and it knows where to look for the files every time, but it's not the end of the world if I can't.

---

### Post by gpeck157 on 2008-04-29
Sorry you're still having issues. You probably already did this too, but just in the interest of being thorough, I not only installed smbfs, but also installed winbind. My smbcredentials file was placed under /root/.smbcredentials. I gave my external drive a static ip address (noted in post) and my mount points were added under /media/Dad. I also made sure my mount points and .smbcredentials file had full read/write capability for all users and groups even though the folder ownership was still under "root". 
Again, hope this helps...

---

