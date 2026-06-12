---
title: "PHP writing to CIFS share"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Gohtar on 2010-08-23
I am having problems getting my PHP web page to write a file to a cifs share.

On the windows side I have the share set up and gave my user full control.

On the server side I am using fstab to mount my share using the windows credentials.

I have tried quite few ways of mounting the share but none have worked, meaning, The mount works but PHP cannot write to the directory.  I can browse the files in the mount just fine from the shell.

In my php webpage i get the error "Warning: fopen(/mnt/cancellations/myfile.txt) [function.fopen]: failed to open stream: Permission denied in /var/www/rt/index.php on line 4"

My current fstab entry looks like this:
```
//cpf-fileserver/cancellations$/kokoExports /mnt/cancellations cifs deafaults,uid=33,gid=33,credentials=/root/kokoScripts/.smbcreds,dir_mode=0777,file_mode=0777

```

I have tried all sorts of UIDs and GIDs, I have tried adding the RW, tried it without the dir and file mode, added the 0 0 to it... just out of ideas.

Can someone help please? Maybe point me in the direction to troubleshooting it?

Thanks

---

### Post by Gohtar on 2010-08-23
I figured it out...

I had to chmod my /mnt folder to 655 to get it to work.

---

