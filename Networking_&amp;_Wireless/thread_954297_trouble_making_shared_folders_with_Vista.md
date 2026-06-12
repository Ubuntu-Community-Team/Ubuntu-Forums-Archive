---
title: "trouble making shared folders with Vista"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by etheesdad on 2008-10-21
Hi Im trying to get Ubuntu to read folders on my Windows box. 

Have been trying for the last couple of hours to follow the instructions here
[http://blogs.zdnet.com/Bott/?p=237](http://blogs.zdnet.com/Bott/?p=237)

but keep getting the same errors

Instructions:
sudo mount -t smbfs -o username=windows_username,password=windows_password
//vista_pc_name/share_name   mount_folder_name

Im entering:
sudo mount -t smbfs -o username=j,password=*** //Desktop/share //home/j/movies

and it comes back with

mount error 6 = No such device or address

there is a folder on Desktop called share

there is also a folder in /home/j called movies

Can anyone point me in the right direction? What am I doing wrong?

---

