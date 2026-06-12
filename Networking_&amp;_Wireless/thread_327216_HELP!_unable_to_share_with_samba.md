---
title: "HELP! unable to share with samba"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by stounfree on 2006-12-28
Hi All,

I am unable to share folders from my ubuntu box (it's a dapper server). The share is visible from other windows machines, but _its content is always empty_.

I tried the linux client from the same machine but it gives me this output :

```

me@server:~$ sudo smbclient -N //Server/backup -c 'ls'
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.22]
NT_STATUS_NETWORK_ACCESS_DENIED listing \*

                0 blocks of size 0. 0 blocks available

```

As you can see, the smbclient logged in successfully but was unable to list the files in my share (backup).

Here's the share section in /etc/samba/smb.conf

```

[backup]
  comment = My backup
  path = /home/me/backup
  public = yes
  read only = no
  create mask = 0777
  directory mask = 0777
  guest ok = yes
  browseable = yes

```

Any ideas about this problem? Especially about the NT_STATUS_NETWORK_ACCESS_DENIED error...


Thanks in advance.

---

### Post by stounfree on 2006-12-29
Forget about my question, now it seems to work :

The unix and the samba accounts didn't have the same password. It was apparently the cause.

I hope it helps somebody having the same problem.

---

### Post by jtwadsworth on 2006-12-30
I have a similar problem and was wondering how you fixed yours?  From my wired LAN, the WinXP boxes can see the Ubuntu machine's ID but when clicking on it to access it I am presented with a login/pw box in WinXP.   I cannot log into the shared Ubuntu box using the logins/pw for the appropriate users in Ubuntu.  I have created users on the Ubuntu box with the same names as the names of the WinXP computers on the network.

Going from the Ubuntu box to the shared WinXP boxes goes fine though and I am able to see those files, etc.

I have ready many HOWTOs on this and still having problems...help appreciated.

jtw

---

### Post by stounfree on 2006-12-30
_I STRONGLY advice you_ to follow the steps of this thread, Since it **really** helped me : **[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)**


In my case, i found that the mapping wasn't well defined in /etc/samba/smbusers, it should be this way :

```

UNIX_ACCOUNT=SAMBA_ACCOUNT

```

I also found that the shared folder didn't have enough permissions to be listed. (it requires execute permission for this purpose)

```

chmod 0755 /home/myself/samba/

```

And finally, i fixed 'browseable' in this share definition in /etc/samba/smb.conf :

```

[myshare]
    path = /home/myself/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = UNIX_ACCOUNT
    force group = UNIX_GROUP

```

I hope this helps,

Stounfree

---

### Post by stounfree on 2006-12-30
Another thing that helped troubleshooting is smbclient command, available from apt :

```
sudo apt-get install smbclient
```

the 'ls' command is straight forward :

```
smbclient -U<SAMBA_USER> //SERVERNAME/Share -c 'ls'
```

It is equivalent to browsing your linux share from Outside,

If you don't want to be bothered by the password prompt :

```
smbclient -U<SAMBA_USER>%<SAMBA_PASSWORD> //SERVERNAME/Share -c 'ls'
```

Regards

---

### Post by jtwadsworth on 2006-12-30
Really helpful so far!  I have now gotten the XP machines to see the Ubuntu machine and can use its printer.

To test things I shared out my /home/<user> folder by chmod 0777 it...oops!  How do I set the permissions back to normal?

What I am trying to share out is my music collection which resides on an NTFS drive (I am dual booting this computer with XP)

Here is what I have for the share in my smb.conf:

```

[MyMusic]
    path = '/media/hdb1/My Music'
    browseable = yes
    read only = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = <my user>
    force group = <my user>

```

<my user> is my own login, of course.  This share is seen by the XP boxes but when trying to log into it, I get the login box and no login works.  The NTFS drive is mounted and easily used by the Ubuntu box.

When trying to login using smbclient I get:

tree connect failed: NT_STATUS_BAD_NETWORK_NAME


Any ideas please ?

jtw

---

### Post by stounfree on 2006-12-31
1 - Home folder permission: the normal mode for your home folder is : drwxr-xr-x, cith chmod 0777 you have permissions like : drwxrwxrwx

so to restore it's original permission you can do :

```
chmod go-w /home/<user>
```

*go-w* means : Group Others minus Write, as you can guess, it removes write permission from users of the same group and other users.

Your music share's permission dont need to be changed since it is NTFS, which is usually read-only under linux. It also has the execution permission enabled by default.

2 - Share login box rejects your user/pwd : Did you declare your samba account in Ubuntu?
    it requires calling smbpasswd and editing the /etc/samba/smbusers in order to link the samba account to your unix account, **([see the thread i mentionned earlier]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto"))**.

3- NT_STATUS_BAD_NETWORK_NAME : smbclient means the url is not recognized, you should use an url like this in argument : //<Your Ubuntu Box Name>/MyMusic

The command is something like that :

```
smbclient -U<SAMBA_USER>%<SAMBA_PASSWORD> //<Your Ubuntu Box Name>/MyMusic -c 'ls'
```


Another thing : Always restart samba after modifying configuration files under /etc/samba/

```
sudo /etc/init.d/samba restart
```

Happy New Year

---

