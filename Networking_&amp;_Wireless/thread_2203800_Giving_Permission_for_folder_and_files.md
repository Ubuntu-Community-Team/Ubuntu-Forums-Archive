---
title: "Giving Permission for folder and files"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by Jijo_Cherian on 2014-02-05
Hi Guys,

I have created some folders and files using python programming on my ubuntu server. I have also shared those folders using NFS with few ubuntu client systems. 

Now the main problem that is occuring right now is that the client cannot change anything in the files that are made. Not even they can add files. I have tired giving 766 permission to the folders but of no use. There is some permission denied. Also the user is shown as root. 

drwxr-xr-x 6 root root 4096 Feb 5 12:43 TES/

I cant change it to write. 
Thanks a lot

---

### Post by Kirboosy on 2014-02-05
Can you post the configuration of your exports file? ```
cat /etc/exports
```

~Caboose

---

### Post by Jijo_Cherian on 2014-02-05
Config of exports files 

/export <ipaddress range>(rw, fsid=0,insecure,no_subtree_check, async)
/export/mywork <ipaddrange> (rw,nohide,insecure,no_subtree_check,async)

FYI - Program is creating folders and files in /mywork folder.

---

### Post by Kirboosy on 2014-02-06
Because the file is owned by root that is most likely the problem. You might want to consider changing the folder permissions. 

```
chown -R <user>:<group> ~/mywork/
```

So you could setup a "nfsusers" group and add anyone you wanted to access the share. Then your command would look something like this.

```
chown -R root:nfsusers ~/mywork/
```

If you are running your program as root that would explain why your folders and files are being created as root user.

~Caboose

---

