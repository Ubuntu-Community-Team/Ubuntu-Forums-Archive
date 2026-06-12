---
title: "error message when backing up with tar -cvpzf"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by z5um on 2011-07-20
hi 

trying to make a backup of my newly installed ubuntu 10.04. Using this command as root 

```
tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev / 
```

after approximately 12 minutes it prompts with this error 

```
/lib/i586/libssl.so.0.9.8
/lib/libssl.so.0.9.8
/cdrom/
tar: /: file changed as we read it
tar: Exiting with failure status due to previous errors
```

what does that mean ? Is the backup unusable ? How to fix ? Other methods to back up ?

---

### Post by Azdour on 2011-07-20
Hi,

If I understand correctly the output of the backup tar is '/'.

Once the tar has completed getting all the files and directories it finds that '/' has been changed. This is because the backup tar has been created there and therefore the contents of '/' have changed.

In this instance I believe it's more of a warning than an error and your backup tar should contain everything.

---

### Post by nothingspecial on 2011-07-20
> **Azdour said:**
> Hi,

If I understand correctly the output of the backup tar is /.

Once the tar has completed getting all the files and directories it finds that / has been changed because the backup tar has been created there and therefore its contents have changed.

In this instance I believe its more of a warning than an error and your backup tar should contain everything.

I agree

---

### Post by z5um on 2011-07-20
i extracted it and everything was fine. thx for your help :KS

---

