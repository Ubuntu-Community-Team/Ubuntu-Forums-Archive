---
title: "Problem with update in 8.10"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by kloyde on 2009-01-26
I have recently upgraded from 8.04 to 8.10 about 2 weeks ago and have found some of my previous problems righted. (somehow when i updated, a bios bug disappeared) However, i have been having problems with updating my computer. I successfully updated it three days ago, but now I can't get it to check for updates. i keep getting an error which reads "W: Failed to fetch [http://mirrors.cat.pdx.edu/ubuntu/dists/intrepid/Release.gpg](http://mirrors.cat.pdx.edu/ubuntu/dists/intrepid/Release.gpg)  Could not connect to mirrors.cat.pdx.edu:80 (131.252.208.96), connection timed out" several times over. Is there something wrong with the update servers that I wasn't aware of (like the server is down for maintenence or something). If someone else is having this problem, let me know what is going on. Thanks.

---

### Post by linux6994 on 2009-01-26
Try going to System > Administration > Software Sources and select another server or have it choose another one for you.

---

### Post by Tim Sharitt on 2009-01-26
Go to System > Administration > Software Sources. From the 'Download from:' list, select a different server and see if that helps.

---

### Post by kloyde on 2009-01-26
Thanks guys, that fixed it right up. :D

---

### Post by jaxxm on 2009-03-17
hi guys 

I have the same problem tried this and did not work. I can use apt-get to install and update and that works fine. also I can download the files via firefox. But installing from add/remove programs, synaptic package manager and update manager does not work. I have tried to reinstall synaptic, uninstall and reinstall all 3 packages and still does the same. I have changed my repository address to one in america, the main repository and the local one in South Africa, all to no avail. Please could some one help.

thanks

---

