---
title: "samba + bash script + permissions issues"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by greenex on 2007-10-19
Hi all,
Let me explain some background first.  We have a very small (gumstix) linux computer on an unmanned ground vehicle.  A script takes pictures, then needs to relay them via wifi back to a base station (just a laptop).  We have a shared folder on a windows machine (will also work for a linux machine too) we would like to store the pictures in.

I am using a script with wget to download the picture and rename it as the current date and time.  I would like to see if I can get it to download directly to the samba folder, but it gives me permission issues.  Or, download it and then move the picture to the samba folder.

Here is the code:
wget [http://[website](http://[website) name]/[picturename].jpg -O /home/greenex/test/$(date +"%F-%T").jpg

"test" is a samba mount on a windows machine.  when I run the script, it says permission denied.  Any ideas?

---

### Post by greenex on 2007-10-20
finally figured out how to do it, but it requires i run the script as root.  Is there anyway to move files into a samba share without being root?

---

