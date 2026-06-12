---
title: "After 18.04 (4.15.0-45-generic) can't mount mybook"
date: 2019-02-04
forum: Networking &amp; Wireless
---

### Post by jesse_h._goode_jr. on 2019-02-04
after an update of the kernel to 4.15.0-45-generic (18.04) , i can no longer mount my Western Digital MyCloud filesystem. No problems before.  I see this in the log :

Feb  2 22:02:25 zinny kernel: [78263.880792] No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3), from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3 (or SMB2.1) specify vers=1.0 on mount.

I've been attempting to get this mounted and using the following command :
sudo mount -t cifs //192.168.1.16/jesse /wdmycloud --verbose -o rw,noauto,iocharset=utf8,file_mode=0664,dir_mode=0775,user=jesse,uid=1000,gid=130,vers=1.0

After prompted for and typing in the password for the jesse folder, i get no error.  Nothing in the /var/log/kern.log  . it's just when i change directory to /wdmycloud and ls -l  ..... nothing is there.  

Not sure what i'm missing here.  the option vers=1.0 was added to supposedly get SMB 1.0 default support as from earlier kernels. I asked western digital. They just confirmed that they only support SMB 1.0 in their original MyCloud devices. They then passed and said to contact ubuntu to see if they have an answer.  From the Western Digital app on my phone, i can see the jesse folder and all it's content. I just get nothing after mounting.  

My thanks to anyone with insights here.
- jesse h. goode jr.

---

