---
title: "Connecting iMac to Ubuntu Samba Share"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by rapidwiz on 2008-03-01
I had a lot of problems connecting my iMac to my Ubuntu shares which works fine for my linux/windows shares but not for my iMac. I originally thought it was an encryption problem and maybe it is somehow, anyway I was getting the following in my samba log files. Anyway I am posting this in the hope it will be useful for others out there.


Below is the error I was getting in my samba log file.
check_ntlm_password:  Authentication for user [rapidwiz] -> [rapidwiz] FAILED with error NT_STATUS_WRONG_PASSWORD

Which implies a password issue, however when i used smbfs_mount and smbclient from my iMac, it worked perfectly, I was able to mount the shares no hassle.

It was just when I went to to Finder -> Connect to Server, it refused to connect with error -43 which implies permissions or share issues etc. I also read lots of incompatible Samba versions between Tiger and Samba 3. Also recommendation was to change the security from share to user, you can leave it at share if you want.

Anyway hopefully this can help some iMac users out there.


By the way I am using Mac OS 10.5 and Ubuntu 6.10 with Samba 3.0.22



I had to take 3 steps

1. Create a guest usser account: I used smbuser (useradd smbuser)
2. Enable Guest account in global section (guest account = smbuser)
3. Enable Public = Yes in share section


 more /etc/samba/smb.conf 
[global]
   workgroup = MYGROUP
   server string = VMS Server
   hosts allow =  192.168.2.
;   printcap name = /etc/printcap
   load printers = yes
   printing = lprng
   guest account = smbuser
   log file = /var/log/samba/%m.log
   ;max log size = 0
   security = share
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 
   log level = 2
   debug level = 2

[fs2]
   path = /fs2/movies
   only guest = no
   writable = yes
   valid users = smbuser
   browseable = no
    public = yes

---

