---
title: "Samba Configuration Broken With Window Update"
date: 2022-01-23
forum: Networking &amp; Wireless
---

### Post by dwayne-hopkins on 2022-01-23
My shares have quit working with upgrade to Windows 10. I have tried even the simplest configuration and I still cannot get it to work. I have attached disk and Samba information.

---

### Post by rsteinmetz70112 on 2022-01-24
Is this a new upgrade from to Windows 10 or an upgrade to Windows 10?
What kind of Samba installation do you have? 
Is there a Domain/Workgroup? 
If so is it NT4 or AD? 
If NT4 you need to enable **SMB1/CIFS File Sharing**  Support in Windows 10 and in the smb.conf set ```
server max protocol =  NT1

```
Please post the output of ```
testparm -s
```

---

### Post by Morbius1 on 2022-01-24
It is not clear from your description what exactly the Win10 machine can not do.

All I can do is comment about your share definitions:

> [guest]
        [B][COLOR="#FF0000"]# This share allows anonymous (guest) access
        # without authentication![/COLOR][/B]
        path = /media/xxxxxxx/
        read only = no
        guest ok = yes
        guest only = yes

If xxxxxxx is dwayne it will do no such thing. Only dwayne has the right to traverse the /media/dwayne folder and even then he cannot add anything to that folder. He can only access something under that folder.

This has nothing to do with samba this has to do with how Linux handles the /media/$USER folder.

Your other shares have a similar template like this one:
> [Server_Share]
    comment = Samba on Ubuntu Drive
    path = /media/xxxxxxx/Svr_Drive1
    read only = no
    browsable = yes
    guest ok = yes

There is no way a guest user will gain access to the /media/dwayne/Srv_Drive1 folder. The only user that will gain access to that share is dwayne and only if you tell samba that dwayne is a samba user:
```
sudo smbpasswd -a dwayne
```

You could also use a "force user = dwayne" applied to the share definitions or to the [global] section that will make the guest user appear to be dwayne. All depends on how you want to do this.

---

