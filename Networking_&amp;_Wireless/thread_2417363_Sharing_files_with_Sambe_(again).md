---
title: "Sharing files with Sambe (again)"
date: 2019-04-22
forum: Networking &amp; Wireless
---

### Post by pflass on 2019-04-22
Sorry to post what is an FAQ, but I've spent a lot of time browsing Q+A and haven't found a usable answer. I have two Linux machunes (Windows not in play at the moment): Release 16.04.6 LTS (Xenial Xerus) 64-bit, MATE 1.12.1 and Release 16.04.5 LTS (Xenial Xerus) 64-bit, MATE 1.12.1, both Samba 0.3.2. I have the same user (let's say "Me") defined on both systems and I want to share /home/Me.

Finally at the end of my rope I copied one smb.conf to the other, changing only the machine name (attachment). I can see the folder from the other machine. I have tried to connect both without creating a Samba userid (supposed to use Linux id?) and after creating with smbpasswd -a Me and creating a password. In either case, when I get the "Password required for share Me..." I chose "connect as user", enter my userid, group, and password, and get the same panel back again.

I have also tried creating another share for the folder with caja-share, and get the same.

Any help appreciated!

---

### Post by TheFu on 2019-04-23
I haven't a clue, but userids should be all lowercase on Unix systems.  Yes, it shouldn't matter, but sometimes it does if the programmer didn't convert all userids used throughout their code to lowercase for all comparisons. If they missed 1 place, ouch.

BTW, if only Unix systems are involved, then NFS is the better solution.

I looked over the smb.conf file.  This is very different than mine.  I don't use WINS nor AD nor LDAP. If you aren't using them either, it can be greatly trimmed/simplified. If the security is set to user, doesn't that prevent LDAP/AD?   If those are desired, shouldn't security be set to DOMAIN?

The [homes] section is a special area that allows sharing all the userid HOME directories, based on the valid users setting.  The /home/Me stanza would be in conflict with it. IDK if this matters or not.

A few things that jumped out at me as odd.

```
valid users = %S
```
is different on yours.

In the global section ```

   security = user
   min protocol = SMB2
   protocol = SMB2

```

---

### Post by Morbius1 on 2019-04-23
You used gadmin-samba didn't you?

No one is going to help you with that because everyone who knew how Version2 of samba worked is dead.

I would suggest starting over with a fresh smb.conf. There is a copy of it already present on your system:

Make a copy of the monstrosity you currently have:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
Copy the default over to the correct location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```
Restart smbd:
```
sudo service smbd restart
```

**Only If you have a problem "discovering" you Linux machines in your file manager**: Since this is an all Linux network don't even think about doing network discovery the Windows way with netbios ( even Windows doesn't do netbios anymore ). Do it the Linux way:

Create a file at: 
[B]/etc/avahi/services/samba.service

[/B]Add this to it:```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>

```

---

