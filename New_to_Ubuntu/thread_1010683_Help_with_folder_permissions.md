---
title: "Help with folder permissions"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by halfelite on 2008-12-14
I set up proftpd as my ftp server and used the allow arguments in it to control what the ftp users can do. But it doesnt seem to work as the folder permissions override it. i tried changing the folder permissions around and either locked myself out or everyone had full control. the folder is /mnt/test

Only permissions I can get to work is sudo chmod -R 777

but that is full control.

I want user1 to have full control read write execute.
i want user 2 to be able to read and write
and user 3 to be able to just read.

here is my proftpd layout
```
<Directory ~mnt/test>
  <Limit ALL>
    AllowUser user1
    DenyAll 
#remove rights from all other users
  </Limit>
  <Limit WRITE RNFR>
    AllowUser user2
 #give user2 write rights. allows file deletion by default !
  </Limit>
  <Limit READ CDUP CWD LIST MDTM NLST PWD XCUP XCWD XPWD>
    AllowUser user2 
#give user2 and user3 read rights
    AllowUser user3
  </Limit>
</Directory>

```

---

### Post by DaGrimReefah on 2008-12-19
I believe you want 755 permissions. Though I could be wrong.

---

