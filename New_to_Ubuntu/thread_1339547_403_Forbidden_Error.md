---
title: "403 Forbidden Error"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by cerah on 2009-11-27
I'm pretty new to linux... I'm running Ubuntu 9.04 on my msi wind and it's been fairly good.

I've been designing a very basic html/css portfolio website for one of my artists and this is the first time I've done any of the webpage editing on linux.

I've been working off my mem stick using Adobe GoLive on a Windows computer at the shop but I needed to do some at home so I decided to run it through WINE which worked fine and I was able to do all the updates I needed.

I uploaded all the pages via gFTP and now they all get a 403 Forbidden Error "You don't have permission to access /index.html on this server".

I thought it was my file/folder permissions (even though I've uploaded and downloaded numerous times on this stick in this folder from the Windows PC I was using) so I looked at them and in the "others" section it says folder access none but every time I click to change it it changes right back to none.

I've tried resaving the files outside of that directory... I've tried 'sudo chmod -R a=rx /path/location' to no avail... I've even booted up an old laptop which runs Windows to uncheck the "read-only" permissions on the folder and then I resaved the files and reuploaded them and nothing.

I'm at a complete loss as to what to do... any help would be great... I'm nervous about messing around in the terminal on my own and I've done a couple seraches but everything seems rather over my head.

---

### Post by wheatpenny on 2009-11-27
Who is the owner of the folder? If it's "root" then you'll have to use a sudo command to change the permissions or ownership

---

### Post by cerah on 2009-11-27
owner: cerah - Cerah
folder access: create and delete files
file access: ---

group: root 
folder access: none
file access: ---

Others:
folder access: none
file access: ---


Whenever I click anything under "Group" or "Other" it just reverts back to nothing...

---

### Post by wheatpenny on 2009-11-27
for some reason it appears to be assigned to Root's group. Reassign it to your own group by typing sudo chgrp <group name> <folder path>.
If there are other subdirectories inside the folder then instead of chgrp type chgrp -R.

---

### Post by cerah on 2009-11-27
The group cannot be changed.
You do not have the permissions necessary to change the group of "folder name".

And when I do it in the terminal I get...

chgrp: changing group of `folder path': Operation not permitted

I tried copy/pasting the source html of the index file into notepad n then into a whole new adobe golive page and saved it on my desktop of the windows pc and when I uploaded it I still got the forbidden error.

---

### Post by wheatpenny on 2009-11-27
try logging in as root (if you haven't already done so, type sudo passwd root, then input your password, then you will be asked to assign a 'UNIX password' (actually a root password). do so
then type su and enter the root password when prompted. You'll get a different prompt that indicates you are now root. Then try to change the group. 
also, when logged in as root, you don't need to type sudo at the beginning of the command.
Once you've unlocked the root account like this, it's permanent. from now on you only need to type su and the root password to get root power.

---

### Post by cerah on 2009-11-28
Logged in as root... 

root@xxxxxxx:~# chgrp <group name> <path>
chgrp: changing group of <path>: Operation not permitted

I'm starting to go a lil crazy here... 

I was told by someone I need to set my permission levels at 755 

sudo chmod 755 <path>
cd <path>
sudo chmod 644

But that didn't do anything either...

---

### Post by wheatpenny on 2009-11-28
ok, well I can't think of anything else (I'm still pretty new at Ubuntu myself)

---

### Post by jolx on 2009-11-28
> **cerah said:**
> I've tried 'sudo chmod -R a=rx /path/location'

> **cerah said:**
> Logged in as root... 

root@xxxxxxx:~# chgrp <group name> <path>
chgrp: changing group of <path>: Operation not permitted

I'm starting to go a lil crazy here... 

I was told by someone I need to set my permission levels at 755 

sudo chmod 755 <path>
cd <path>
sudo chmod 644

But that didn't do anything either...

Are you typing "/path/location", "<group name>" etc instead the actual path and group?

---

### Post by rudy.b on 2009-11-28
If you're trying to chmod or chgrp on files/directories in a Windows file system (e.g. FAT32), you will have problems.  Can you change the permissions of the files directly on the server?

---

