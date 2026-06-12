---
title: "Can not connect to Windows share"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Lab on 2007-03-22
I am trying to connect to **TESTAPPS**

Any ideas?

```
smbclient \\\\testapps\\ -U username
Connection to testapps failed
```


```
user@linux:~$ smbclient -L \\SHARENAME
Password: 
Anonymous login successful
Domain=[SHARENAME] OS=[Windows Server 2003] Server=[Windows Server 2003]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to SHARENAME failed (Called name not present)
Anonymous login successful
Domain=[SHARENAME] OS=[Windows Server 2003] Server=[Windows Server]

        Server               Comment
        ---------            -------
        DOCUMENTIMAGE1       
        DOCUMENTIMAGE2       
        DOCUMENTIMAGING      
        SHARE-APPS1           
        SHARE-BACKUP          
        SHARE-PDC             
        SHARE-REC             
        SHARE-SQL-1           
        SHARE-TEST            
        ESSWEB1              
        TESTAPPS             

        Workgroup            Master
        ---------            -------
        SHARENAME              SHARE-PDC
        SDXWIU               
        TESTAD               
        WIU-AD               
        WORKGROUP            RADIO4
```

---

### Post by spd106 on 2007-03-22
You need the server and the share name to connect. Also as you are probably using a bash shell the backslashes will normally be used as escape characters. To avoid this I usually use single quotes, e.g.
```
smbclient '\\server\share'
```

This works on Edgy, I'm not so sure about Dapper or earlier.

---

