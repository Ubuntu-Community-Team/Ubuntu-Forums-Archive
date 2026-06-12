---
title: "[xubuntu] Problems with mounted samba share"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by toothandnail on 2016-04-19
I have a desktop machine with Win7 and Xubuntu 14.04 (fully updated), working in conjunction with a small network server (Slackware-base) that is showing a most peculiar problem.

The sever has a single Samba share available, intended as a backup medium for the desktop machine (both Windows files and Linux files). Normally I would use NFS for this type of purpose, but since the files need to be accessible from a Windows boot as well as from Linux, I set up Samba on the server.

Since the backup is run by script, I'm using a mount command in the scripts:

```
sudo mount -t cifs //nasbox/files /mnt/smb -o user=xxx,passwd=yyy
```

That works fine. The user exists on the server and has a password saved in the normal Samba password file. Mount performs without problems. However...

Any attempt to write to the share gets a "permission denied" error (though oddly, a zero-length file will be created). My first thought was that I had something incorrectly set with permissions or ownership of the file share (I've had problems with getting Samba permissions and Linux permissions correct for Samba in the past), but checking shows that everything is correct. The other strange thing is if I use Thunar to connect to the share, I can read and write files without any errors at all.

In my attempts to work out what was causing the problem, I pulled the server out of its normal network and stuck it into another network (which has a similar server which has been working fine for a long time). In that environment, I tested share access from my own laptop, using several different Linux distributions. 

First test was with Xubuntu 14.04. Which had exactly the same problem in the new environment. I also discovered that the server already in that network also showed the same problem when using a mount command from Xubuntu.

I then tested using Sparky Linux (Debian testing derived), an oldish Salix install, and Arch (my normal distro of choice). In all instances, I had no problem reading and writing files to the share when it was mounted using the mount command above. I'm at a loss. Permissions are fine, there is a legitimate user, the share mounts without any errors, but Xubuntu continues to give me "permission denied" any time I try to write to the mounted share.

Can anyone give me an idea of what could cause this type of error? It seems entirely specific to the Ubuntu family. There is no firewall enabled on Xubuntu (and I wouldn't expect a permission denied error if a firewall was involved), so I have no idea what the problem might be. Help?

Paul.

---

### Post by May_Masters on 2016-04-20
Well my first thought would be: is your Xubuntu probably running a different Samba Protocol version ?
Is SE-Linux enabled somewhere ?
You can also set IP-restrictions inside the samba.conf ... do they apply to your Xubuntu box ?
Turn-on debugging. Server: [link]("https://www.samba.org/samba/docs/using_samba/ch12.html") - Client: [link]("https://wiki.samba.org/index.php/Client_specific_logging")

---

### Post by toothandnail on 2016-04-20
> **May_Masters said:**
> Well my first thought would be: is your Xubuntu probably running a different Samba Protocol version ?

Don't think so, though I'll check just in case...

> Is SE-Linux enabled somewhere ?

I didn't think SE-Linux was installed in Xubuntu. Unless it is and I've missed it, shouldn't be running

> You can also set IP-restrictions inside the samba.conf ... do they apply to your Xubuntu box ?

They're set, but on a sub-net basis, so any ip in the local subnet should have access. Usually, if there is a restriction of that sort, the share won't mount at all, which isn't the case here.

> Turn-on debugging. Server: [link]("https://www.samba.org/samba/docs/using_samba/ch12.html") - Client: [link]("https://wiki.samba.org/index.php/Client_specific_logging")

Thanks. I'll do that and see what I can find, though I think I may have a fix. I've never needed it before, but I tried adding uid and gid to the mount command:

```

sudo mount -t cifs //nasbox/files /mnt/smb -o user=xxx,passwd=yyy,uid=1006,gid=500

```

After doing that, I've been able to write files to the share without any further errors. 


Still got to check it in its own home environment, but it looks as though that fixes the problem. Odd though - I've never had to do that with any other Samba setup I've used, and I don't see where the requirement comes from. I'll turn on debugging to see if I can see what that turns up.

Paul.

---

