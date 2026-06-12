---
title: "Ubuntu/Ubuntu file sharing for non-admin users?"
date: 2019-11-03
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2019-11-03
Hi!

I have a PC running 19.04 & a Netbook running 16.04, both on my local WiFi network.
I am admin on both.
I have File/Folder Sharing working OK between my own files, both ways, on these 2 machines.

But I can't make my wife's Files/Folders shareable on either machine.
If I try from her desk, I get an error message:
```
'net usershare' returned error 255: net usershare add: failed to add share desktop. Error was Operation not permitted
```

Other methods, like accessing her files via file manager from my own desk & trying to make them shareable from there, or "Opening file manager as Admin" from either desk also failed for various reasons (which I could detail if of any interest).

Should it be possible to share non-admin-user's files?
If so - how?

Thanks for any help!

---

### Post by #&amp;thj^% on 2019-11-03
I had this issue when I tried to add a usershare before samba was installed ```
apt install samba
``` 
The simplest solution would to be to add the line,

```
usershare owner only = false
```

to the Global section of the smb.conf file by,
```

sudoedit  /etc/samba/smb.conf
```

then save the file and restart the samba service,
```

sudo restart smbd
```

Then try again to share the selected folder, This is where I first came up this: [https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html)

You did not say what version your Wife's computer is using but this is a new issue there:
Change the following:
```

group = sambashare to force group = +sambashare (required)
map to guest = bad user to map to guest = bad password (optional)
```

Samba 4.8.1 and higher requires the **"+" **now, posible a bug.
I still need to find out from upstream why the **"+"** is now required
Don't forget to add any users:
```
sudo pdbedit -L -v
---------------
Unix username:        me
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-1011378171-xxxxxxxxxxxx-xxx <Sniped by OP>
Primary Group SID:    S-1-5-21-1011378171-xxxxxxxxxxxx-xxx <Sniped by OP>
Full Name:            
Home Directory:       \\archlinux\me
HomeDir Drive:        
Logon Script:         
Profile Path:         \\archlinux\me\profile
Domain:               ARCHLINUX
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          Wed, 06 Feb 2036 08:06:39 MST
Kickoff time:         Wed, 06 Feb 2036 08:06:39 MST
Password last set:    Sun, 03 Nov 2019 15:18:17 MST
Password can change:  Sun, 03 Nov 2019 15:18:17 MST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
```

---

### Post by 2CV67 on 2019-11-06
Thank you very much 1fallen for your detailed help!
And my apologies for the slow response.

"usershare owner only = false" allowed me to declare me wife's folders as "shared" OK from my own file manager, but oddly they don't appear as shared in her file manager...

In the meantime, the old Netbook has been getting too shaky with Ubuntu so I am in the process of switching to Lubuntu.
That means file/folder sharing is not today's priority.

After getting Lubuntu up & running OK, I will get back to this thread with the file sharing situation.

Thanks again!

---

### Post by slickymaster on 2019-11-06
*Thread moved to **Networking & Wireless**.*

---

### Post by TheFu on 2019-11-06
If the systems are both running Unix/Linux, use NFS for file sharing. NFS is server-to-server, not user-to-server.  Normal unix file permissions are used, so there's nothing new to learn and NFS is usually 20-30% faster than other options.  You can run both NFS and CIFS sharing of the same stuff, if you like.  If the system are always on the network, use the fstab to share storage. If a system isn't always there, use autofs so it only gets mounted when requested.

BTW, support for 19.04 ends in January, so it might be worth moving to 19.10 now before trying to fix this.  19.10 changes lots of interoperability things.

---

### Post by 2CV67 on 2019-11-11
After shifting the Netbook to Lubuntu 18.04.3 it was able to see & use my wife's shared files on the PC (set after using 1fallen's suggested usershare owner only = false modification) so I consider this thread SOLVED, thank you 1fallen!

In the meantime I found another method which also worked in Lubuntu where there seems to be no GUI option in the File Manager.

[https://ubuntuforums.org/showthread.php?t=2430916](https://ubuntuforums.org/showthread.php?t=2430916)

---

