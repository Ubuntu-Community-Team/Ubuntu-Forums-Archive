---
title: "[SOLVED] Tunnelling and Samba"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by drlock on 2008-09-01
I am trying to pass a samba mount through an SSH tunnel to my file server. The basic setup is:

Linux Client -- |Firewall| -- Windows File Server

The Windows File Server is running OpenSSH for Windows (BTW freeSSHd has a tunneling bug and won't work) and can accept tunnels and local forwarding.

I can create the tunnel, I can even browse the file server with smbclient, but I can't get it to mount the samba share. My slightly modified terminal session is:

```

rairighd@rairighd-lab:~$ ssh -N -f -L 20139:10.0.0.1:139 magni.domain.com
rairighd@magni.domain.com's password:
rairighd@rairighd-lab:~$ smbclient //magni/backups -p 20139 -U rairighd -I 127.0.0.1
Password:
Domain=[MAGNI] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> ls
  .                                   D        0  Fri Dec 22 11:16:38 2006
  ..                                  D        0  Fri Dec 22 11:16:38 2006
  .Trash-rairighd                    DH        0  Mon Feb 26 15:31:21 2007

                48618 blocks of size 4194304. 9347 blocks available
smb: \> exit
rairighd@rairighd-lab:~$ sudo mount -t smbfs //magni/backups /mnt/bak/ -o port=20139,ip=127.0.0.1,username=rairighd
Password:
mount error 112 = Host is down
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

10.0.0.1 is a loopback device on the Windows file server

Why can't smbfs talk to the host when smbclient can? I have read lots of HowTos on about this but none seems to solve this problem. Any help would be appreciated.

Thanks

---

### Post by bab1 on 2008-09-01
> Why can't smbfs talk to the host when smbclient can?
My guess is that there is a problem gvfs and ssh.  Do other Gnome applications tunnel successfully?

I don't use ssh for anything other than CLI stuff so this is just my opinion based on my Samba experience.  The client smbclient is a CLI based app.  It's very similar to a basic FTP client. As you say, it has no problems with ssh.  On the other hand smbfs uses GUI interfaces and Ubuntu that would be gvfs.

Edit:  This may not be the case for other variants.  I understand Kubuntu does not use the gvfs (Gnome Virtual File System) amd does not have the same GUI response.

---

### Post by drlock on 2008-09-02
Yes. I don't think that smbfs uses the GUI at all. Ubuntu has a GUI interface for accessing samba shares but I was bypassing that and doing everything from the command line.

I had to think about the gvfs part for a while, but I don't think I am using that either. If I use the "Connect to Server" menu option that makes a connection that is never really mounted to the file system, but can be browsed from Nautalis. I think that is gvfs. However, smbfs make a real mount to the file system.

Either way, I still can't access my file server.

---

### Post by bab1 on 2008-09-02
Actually it does mount the share.  The mount is a "soft" mount.  The config is stored at /var/lib/samba.  The share is unmounted when you close the connection.  You will never see it in smb.conf.

But, as you say, your idea does not work.

---

### Post by drlock on 2008-09-12
I got some help from the linux-cifs-client mailing list. So for those who may need it, here is my final solution:

The key is to use port 445. Then mounting works a lot smoother (notably smbclient no longer works).

To make things easier add something like the following to your ~/.ssh/config
```

Host server
HostName server.domain.com
	User username
	LocalForward 20445 10.0.0.1:445

```
Note that 10.0.0.1 has to be setup as a loop back device on the Windows file server.
Now you can create the tunnel to the Windows machine with
```

ssh -N -f server

```
By the way, this tunnel will run on forever in the background unless you kill it or reboot. Have a look [here]("http://www.g-loaded.eu/2006/11/24/auto-closing-ssh-tunnels/") for more details.

Now we can setup fstab to make mounting easier:
```

//server.domain.com/share /mnt/bak smbfs rw,user,credentials=/credentials/path,uid=user,gid=group,file_mode=0664,dir_mode=0775,port=20445,ip=127.0.0.1	0	0

```

And finally mount the share with
```

sudo mount /mnt/bak

```

Hope that is a help to others

---

