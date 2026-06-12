---
title: "Rsync Read Only Destination Folder on Network Share"
date: 2018-12-31
forum: Networking &amp; Wireless
---

### Post by zubbs1 on 2018-12-31
I have two machines that I am trying to copy files between.  Machine A has folders to copy to machine B.  I setup a ssh connection and can remote login from machine A to machine B and navigate directly to the destination folder I am trying to copy to. I can also open the shared folder location I am trying to copy to on machine B from machine A through the nautilus files window.

The folder on machine B is : /media/storemore/Shows
The shared folder seen in nautilus: smb://storemore-deskt/sharemore2/

my smb.conf file on machine B:
> #============================ Global definition ================================
 
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = sharemore
security = user
map to guest = bad user
name resolve order = bcast host
dns proxy = no
bind interfaces only = yes


#============================ Share Definitions ============================== 


[Public]
   path = /samba/public
   writable = yes
   guest ok = yes
   guest only = yes
   read only = no
   create mode = 0777
   directory mode = 0777
   force user = nobody
[Sharemore2]
   path = /media/storemore
   writable = yes
   guest ok = yes
   guest only = yes
   read only = no
   create mode = 0777
   directory mode = 0777
   force user = nobody




I get the following error with my rsync command:
[PHP]rsync -r -t -p -v --progress --ignore-existing -s /media/sharemore/Raid/Shows/To\ Move /run/user/1000/gvfs/smb-share:server=storemore-deskt,share=sharemore2/Shows[/PHP]
> 
sending incremental file list
rsync: recv_generator: mkdir "/run/user/1000/gvfs/smb-share:server=storemore-deskt,share=sharemore2/Shows/To Move" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
To Move/


sent 256,776 bytes  received 813 bytes  515,178.00 bytes/sec
total size is 3,679,904,441,029  speedup is 14,285,953.36
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]


Regardless of if the owner:group was storemore:storemore or nobody:nogroup for the /media/storemore on machine B, the same error message exists.

output of ls -la in /media folder of machine B
> 
drwxrwxrwx   3 root   root    4096 Dec 30 22:43 .
drwxr-xr-x  24 root   root    4096 Dec 30 22:28 ..
drwxrwxrwx+  5 nobody nogroup 4096 Dec 31 12:52 storemore


This is a home network only.  I don't care how insecure it is.  I'm fine having all folders and subfolders 777.  I just want to copy the files over so I can make additional room to add more content to machine A.

Sorry if this is confusing, I can clarify anything for you.

Cheers.

*****
Update:
Out of curiousity, I tried doing it the other way around.  I used rsync from machine B to copy from Machine A.  I just reversed the source and destination and it is working.  This is functional, but I am not sure why it is so?

---

### Post by him610 on 2019-01-01
If you can *ssh* between the machines, you should be able to *scp* between the machines.

---

### Post by SeijiSensei on 2019-01-01
Or run rsync with the appropriate credentials

```

cd /path/to/some/local/directory
rsync -av remote_user@remote:/path/to/directory  .

```

---

