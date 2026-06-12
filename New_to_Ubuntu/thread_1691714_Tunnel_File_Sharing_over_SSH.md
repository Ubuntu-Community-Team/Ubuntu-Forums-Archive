---
title: "Tunnel File Sharing over SSH"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by erilidon on 2011-02-20
I have vnc setup to tunnel over ssh without any issues. However now I am trying to set up file sharing over ssh and I can't get it to work. I am trying to forward port 139 through ssh. However it just doesn't seem to work for me.

The server is running linux and has smaba shares setup that can be accessed on the internal network. The client on an external network is also running linux however I can get this to work.

Any ideas?

Thanks.

Also: I have been able to get this to work on a windows PC by disabling the "server" service.

---

### Post by erilidon on 2011-02-24
anyone got any ideas? I though it might be the fact that samba was on the remote computer. I stopped it... and then uninstalled it. Still does not work.

---

### Post by wishyjr on 2011-02-24
will FTP do? I know most FTP clients can FTP via SSH these days, maybe that'll help?

---

### Post by erilidon on 2011-03-11
> **wishyjr said:**
> will FTP do? I know most FTP clients can FTP via SSH these days, maybe that'll help?

It's not really what I'm looking to do. This is so aggravating because I can get it to work with windows just not ubuntu.

I have a firewall with ssh. I connect to it and tunnel vnc, rdp, samba, internet proxy, etc through it. Just to keep things secure when I am accessing them elsewhere.

With windows all I have to do is turn of the server service and it works. I though it might be samba on the linux machine... its not.

Any other ideas? thanks.

---

### Post by asmoore82 on 2011-03-11
I highly recommend sFTP — all you have to install is 'openssh-server'
If you are doing any sort of SSH tunneling — you've got it already.

Linux clients can handle this natively: "Places -> Connect to Server -> Service Type -> SSH"
Windows clients can use Filezilla.

Also, in general, Samba is just not suitable for sharing between linux boxes.
*Everything* else but handles proper Unix file permissions, *even* Apple AFS —
how disturbing is that?

---

### Post by HermanAB on 2011-03-11
Howdy,

Tunnel port 445, not 139.

However, bear in mind that SMB is an extremely chatty protocol, so tunneling it is never a particularly good idea.

---

### Post by erilidon on 2011-04-10
> **HermanAB said:**
> Howdy,

Tunnel port 445, not 139.

However, bear in mind that SMB is an extremely chatty protocol, so tunneling it is never a particularly good idea.

Port 139 is file sharing and I have got it to work correctly using port 139 on windows so that is no the issue. That being said I did try port 445 as well, no luck.

There has to be a way to turn of local file sharing or something. Like I said I had the same exact issues in Windows until I turned off the "Server" service... maybe this just can't be done in Linux.

---

### Post by bodhi.zazen on 2011-04-10
If you want to tunnel over ssh, use winscp , which is basically sftp with a (graphical) windows client.

Where is samba come from and what does samba have to do with your title "Tunnel File Sharing over SSH"

There is no need to tunnel the samba protocol over ssh.

If you want to test the ssh connection , try connecting from putty.

If you can not connect with putty we need more details.

Firewall (either windows or linux) ? Did you forward ports ? Are yo trying to use keys ? Did you install openssh-server on Ubuntu ?

---

### Post by stmiller on 2011-04-10
```
sftp username@yourserver.com
```

---

### Post by bodhi.zazen on 2011-04-10
> **stmiller said:**
> ```
sftp username@yourserver.com
```

sshfs would be better =)

samba can be tunneled over kerberos, but I would not use samba outside a LAN.

---

### Post by erilidon on 2011-04-12
> **bodhi.zazen said:**
> If you want to tunnel over ssh, use winscp , which is basically sftp with a (graphical) windows client.

Where is samba come from and what does samba have to do with your title "Tunnel File Sharing over SSH"

There is no need to tunnel the samba protocol over ssh.

If you want to test the ssh connection , try connecting from putty.

If you can not connect with putty we need more details.

Firewall (either windows or linux) ? Did you forward ports ? Are yo trying to use keys ? Did you install openssh-server on Ubuntu ?

The firewall is a Linux firewall. It's a smoothwall. I can connect to it with putty, which is how I tunneled the filesharing within windows...

---

### Post by bodhi.zazen on 2011-04-13
> **erilidon said:**
> The firewall is a Linux firewall. It's a smoothwall. I can connect to it with putty, which is how I tunneled the filesharing within windows...

If you can connect with putty you can connect with winscp

---

### Post by erilidon on 2011-04-13
> **bodhi.zazen said:**
> If you can connect with putty you can connect with winscp

correct me if I'm wrong, but isn't winscp a windows program? I am wanting to connect with a linux machine. And does winscp tunnel?

See the machine with the shares is not the firewall it is behind the firewall this is why I am using putty with ssh to connect to the firewall.

Connecting is not the problem. I would really prefer no more tips on how to connect. I am having no problem connecting. I can vnc the machine within linux, so I know I am getting to the computer on the other side of the firewall.

What I need to know is why in linux when I tunnel the connection I can't see the shares. I connect the exact same way I do within windows however I can't view the shares.

In Windows I had to disable the "server" service which is what controls that computers ability to share folders.

Thanks

---

### Post by bodhi.zazen on 2011-04-13
My mistake, when you said putty I assumed you were connecting from windows as most people do not use putty on linux 9although it is a fine client).

If you can connect via ssh, use ssh to share files. You have several options, scp , sftp, and sshfs.

[http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://embraceubuntu.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

If you are asking about "shares" or windows shares, that would be samba on a Linux (Ubuntu) server. I would not tunnel samba over ssh, use one of the above methods instead.

---

