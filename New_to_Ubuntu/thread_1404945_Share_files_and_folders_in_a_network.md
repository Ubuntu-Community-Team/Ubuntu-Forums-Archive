---
title: "Share files and folders in a network"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by PHINCY L PIOUS on 2010-02-12
HOW CAN I SHARE MY FILES AND FOLDERS IN UBUNTU? WHEN I TRIED TO DO THE FOLLOWING ERROR APPEARS

'net usershare' returned error 255: net usershare add: cannot share path /media/POPX/Nithin as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.
I DON'T KNOW WHAT TO DO WITH CAN ANY ONE HELP ME?

---

### Post by joshmuffin on 2010-02-12
Hey and welcome to Ubuntu

Try adding "usershare owner only = false" to the smb.conf by:

Opening up a terminal and entering
```

sudo gedit /etc/samba/smb.conf
```

When the text editor opens add the line "usershare owner only = false" (without the quotation marks) underneath where it says [global] then save and close.

If that doesn't work try it again but instead of using:
```

sudo gedit /etc/samba/smb.conf
```
Use:
```

sudo gedit /usr/share/samba/smb.conf
```


Goodluck

---

### Post by Morbius1 on 2010-02-12
> 'net usershare' returned error 255: net usershare add: cannot share path /media/POPX/Nithin as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.I may be wrong about this but in my experience that is probably the finest error message ever written in the history of computing. It not only tells you what the nature of the problem is, it tells you how to fix it ;)

In addition to what joshmuffin outlined I think you may need to restart the samba service in order for the modified smb.conf file to take affect:

Open **Terminal**
Type **sudo service samba restart**

---

