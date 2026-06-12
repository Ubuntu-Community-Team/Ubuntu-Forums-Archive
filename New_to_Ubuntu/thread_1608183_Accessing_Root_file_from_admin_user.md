---
title: "Accessing Root file from admin user"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by theunionstreet on 2010-10-28
Hey, I am building a website on my Ubuntu Server 10.10 box. I have an external hard drive mounted under /media/store. I want to use these files on my site. However, the /media directory is under the root account and I am building my site under my primary account. 

How can I refer to these files when writing my code?

Example: <img src="picture.jpg">
               -In html, picture.jpg would point to a picture in my public_html folder under my primary account. How would I make this point to a picture in /media/store under the root account? (this directory being my mounted drive)

---

### Post by AngusH on 2010-10-28
Perhaps change the perms on the file so that you can access it? If you don't want to let "others" access the file then change the group to a group which your in, and give the group read perms.
Angus

---

### Post by endotherm on 2010-10-28
in short, you wil have to change the ownership on those files to match or be compatible with the credentials used by the process that will run your app.

or you could grant everyone read access to the file path
'sudo chmod -R a+r /media/<external disk mount name>'

---

### Post by theunionstreet on 2010-10-28
I used 
ln -s path/to/mounted/drive
within the folder I host my site in.
Is this approach bad?

---

### Post by endotherm on 2010-10-28
> **theunionstreet said:**
> I used 
ln -s path/to/mounted/drive
within the folder I host my site in.
Is this approach bad?
hmmm. I don't know. it sounds reasonable. I am not sure how links work in relation to the physical path permissions. try granting everyone read access to the image folder itself, and see if the link allows you to skip over the dirs in the path that are not readable by that user. if that doesn;t work, you may have to grant read rights up the entire path.

---

