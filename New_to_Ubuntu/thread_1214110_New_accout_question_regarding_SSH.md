---
title: "New accout question regarding SSH"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by Cyked on 2009-07-15
So I created a new user as I want to basically replace the account I created originally when I installed Ubuntu.  I pretty much do everything from putty/terminal on the machine, and the first thing I noticed after logging in via SSH, instead of seeing the normal "userID@machinename:~$" I just see "$".  Also, I seen no font color differences when I do an ls command that indicate file, directory, etc.  What gives?

Like I said this is the first thing I noticed, I'm sure other things will come up later...  My goal is to establish a way to clone existing accounts basically.  So any other tips are appreciated. 

What I have done so far is created the user with useradd and added that user to the same groups as my "clone" account.

Thanks!

---

### Post by Celauran on 2009-07-15
useradd just creates the user -- I think you even have to specify the home directory. adduser, on the other hand, does a lot more for you, including creating the home directory and populating it with some basic files from /etc/skel.

---

### Post by Cyked on 2009-07-15
The exact command I used was 

```
sudo useradd -d /home/newid -m newid
```

---

### Post by Cyked on 2009-07-15
I went back and used adduser.  Thanks!

---

### Post by Cyked on 2009-07-16
Right after creating the account I added the new user to all the groups my pre-existing account was a part.  Just playing around, added a new iptables rule and wanted to back it up.  So I did ```
sudo iptables-save > /etc/rules.iptables
``` and I get Permission denied.  Shouldn't the new account be able to do what the pre-existing account could with the same group permissions, or no?

Thanks!

---

### Post by cariboo on 2009-07-16
Did you add your new user to the admin group?

---

### Post by Cyked on 2009-07-16
here are the groups....

```
@tux:~$ groups userid
userid adm dialout cdrom plugdev lpadmin admin sambashare

```

---

### Post by Cyked on 2009-07-17
I have another permissions related question.  Under /var/www I believe the structure used to be /var/www/files.  Under files I had a like /sounds, /pics, /gifs.  I used to use a simple bat file for pscp to copy files over.  I recently changed the structure around, to something like /var/www/files/images/ with folders like /sounds, /pics, /gifs below that.  Yesterday I tried to run my bat file to upload some files and I was getting permission denied when trying to write to the /pics folder, which worked before with no issues.

I assume the permissions wouldn't have changed when I was moving things around and would have stayed as root:root, though maybe I am wrong.  Why did it stop working, is it because I used sudo mv to change the structure?

At any rate, I created a group and added some users to it with write permissions to my web area and made the permissions root:web.

Still no idea why the new account I created can't write to /etc...... :confused:

---

### Post by Cyked on 2009-07-21
Any ideas on why the new account can't make changes in certain directories?

---

### Post by Cyked on 2009-07-23
No ideas?  I can go in and edit the file with sudo nano and save changes, but the account can't do iptables-save.

---

### Post by Cyked on 2009-08-05
bump

---

