---
title: "help unlock folder with permissions"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by b3d3g1 on 2010-12-10
I followed some instructions to successfully install Veetle for an online streaming website using the following commands:
sudo chmod +x veetle-0.9.16-linux-install.sh
sudo sh veetle-0.9.16-linux-install.sh

now the folder titled with the same as my username is locked.  I can not delete the install file in the folder.

I know this has something to do with my permissions but I've only had only about 1 month with linux and I have no idea how to change this back.

---

### Post by vathul on 2010-12-10
try using chmod 777 file name .. Guess that should do the trick :)

---

### Post by b3d3g1 on 2010-12-10
sudo chmod 777 veetle-0.9.17-linux-install.sh

(should have been 0.9.17 in the first post)

I tried this and I still can't delete the file and there is still a lock symbol on my user name folder

---

### Post by b3d3g1 on 2010-12-10
I figured it out using the Keir Thomas ubuntu pocket guide.  
It was just a matter of permissions and changing them back using 
sudo chmod ugo+rwx /home/b3d3g1

---

