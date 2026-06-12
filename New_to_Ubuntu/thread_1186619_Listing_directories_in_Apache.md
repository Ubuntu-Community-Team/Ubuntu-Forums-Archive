---
title: "Listing directories in Apache"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by lmlypfan on 2009-06-13
say i have a directory /media/RAID5 that i would like to be accessed via a web browser. 

i'm assuming i need to edit the index.html file.

what would the code look like.

n00b

---

### Post by chrisod on 2009-06-13
Actually adding an index.htm page would only display the content on the index page. You need to enable directory listing. Google it as there are several ways to do it. You can edit the Apache config if you have root access, or allow it by adding a .htaccess file to the directory that you want to list.

---

### Post by SoftwareExplorer on 2009-06-13
It is that there is *no* index.html in the directory you want to list, and that Apache is set to serve that directory. 

One way to do this (assumes you don't already have a website being served by appache):

```
Alt + F2
```
then, in the box that comes up
```
gksudo nautilus
```
put in your password and navigate to /var (you'll have to go up one most likely and then into the 'var' folder. Assuming you have no website stored in the 'www' folder, you delete it. Navigate to the /media folder and right click on RAID5 and click make link. Cut the link and navigate back to the /var folder. Paste the link and rename it to 'www'. Right click on it and go to the permissions tab. Set the owner to 'www-data' and the group to the same.

I think that should do it-hopefully I haven't overlooked anything.

---

### Post by SoftwareExplorer on 2009-06-13
As far as directory listing, I think it is on by default. It works on my computer right now, and I don't remember ever turning it on, as I have my computer serve a website.

---

### Post by lmlypfan on 2009-06-13
Ok, i created a new file in the /var/www folder. 
Its a headless server, so I'm using ssh. Now when i go to the server, its forbidden in my web browser. 

I changed the ownership and group of the file, but still no luck.

I've made some progress though (I think).

---

### Post by SoftwareExplorer on 2009-06-13
Hmm. Have you tried making the /media/RAID5 folder owned by www-data? I would think that having the link owned by www-data would work, but maybe not.

Another thing you might try is putting a test index.html in the RAID5 folder and see if it comes up. That would mean the link works and that it is something (probably) with allowing directory listing. The thing is that I once knew how to do that but have since forgotten.

---

### Post by lmlypfan on 2009-06-13
Got it. 
Had to do a soft symbolic link as RAID5 is on a separate partition. 

Thanks for all the help.

---

### Post by SoftwareExplorer on 2009-06-13
> **lmlypfan said:**
> Got it. 
Had to do a soft symbolic link as RAID5 is on a separate partition. 

Thanks for all the help.

You're welcome. I don't know what the difference of a soft symbolic link is. It sounds like you do, could you explain it to me?

---

### Post by lmlypfan on 2009-06-13
when i tried the command 

ln /media/RAID5

It said that i could not hard link the directory. I googled it and its because the directory i was trying to link was a different file system, NFS. I had to use the -s option

ln -s /media/RAID5

---

### Post by SoftwareExplorer on 2009-06-13
Thank you lmlypfan. After reading help for the ln program, it became apparent that the -s means symbolic. A good question is why I never read ln's help file before asking

---

