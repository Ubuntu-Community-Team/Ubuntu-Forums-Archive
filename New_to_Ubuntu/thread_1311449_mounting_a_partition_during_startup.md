---
title: "mounting a partition during startup"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by dagarshali on 2009-11-02
Hi..
I made a ext4 partition in my hard drive..I have to mount it every time i got to use that..

I want that partition to be mounted on boot..

So i went /etc/fstab and edited to add the last line for the 16GB partition

# /etc/fstab: static file system information.                                                                                                                           
#                                                                                                                                                                       
# Use 'vol_id --uuid' to print the universally unique identifier for a                                                                                                  
# device; this may be used with UUID= as a more robust way to name devices                                                                                              
# that works even if disks are added and removed. See fstab(5).                                                                                                         
#                                                                                                                                                                       
# <file system> <mount point>   <type>  <options>       <dump>  <pass>                                                                                                  
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation                                                                                                                                
UUID=e1541d22-19ee-4d71-a7c7-8cd39bbb2291 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation                                                                                                                             
UUID=f26fc011-7e47-495a-ab0b-e6068340a034 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[B]#mounting the 16GB partition to /DATA                                                                                                                                   
UUID=b2655f05-699c-485e-94e6-02570bd5ec89 /DATA ext4 relatime,errors=remount-rw 0       2[/B]


I still need to use sudo to access this folder..

How do I make it to be mounted without asking for a password..

Regards,

vishwa

---

### Post by aktiwers on 2009-11-02
If you right-click inside the folder and pick "properties".
Under the permission tab, who is the owner of the drive?

Is it root? If so, you should be able to simply open terminal and type:
```
sudo chown -R **username**:**username** /media/DATA
```

Where **username** should be changed to YOUR OWN UBUNTU username and /media/DATA changed to the location of your drive.

---

