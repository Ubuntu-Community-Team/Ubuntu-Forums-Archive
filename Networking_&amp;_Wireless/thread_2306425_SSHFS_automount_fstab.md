---
title: "SSHFS automount fstab"
date: 2015-12-15
forum: Networking &amp; Wireless
---

### Post by juraj4 on 2015-12-15
Hi folks,

I 'm struggling with mounting remote webhosting. I'd like to mount it automatically every startup. Everything works fine when I mount it manually via terminal. I am using RSA to authentificate me. Public key is obviously stored on both servers in /.ssh/authorized_keys. Whats more, when I startup my Ubuntu(14.04) it doesn't say anything about unsuccessful mounting and it rapidly slows down. The mount point is visible in Nautilus, but after clicking on it, I see only error: "Unhandled error message: Error when getting information for file '/home/juraj/SSHFS': Input/output error". I have tried to mount it also in home folder and /media/..., but without any success. I am relatively new to Linux, so I will be glad for any suggestions. Here are my fstab lines: 

[EMAIL="xkorce01@merlin.fit.vutbr.cz"]usernameonserver@merlin.fit.vutbr.cz[/EMAIL]:/ /home/juraj/SSHFS/ fuse.sshfs delay_connect,_netdev,user,idmap=user,transform_symlinks,identityfile=/home/juraj/.ssh/rsa,allow_other,default_permissions,uid=1000,gid=1000 0 0


[EMAIL="pediatersucha.sk@pediatersucha.sk"]usernameonserver@pediatersucha.sk[/EMAIL]:/ /media/juraj/pediatersucha.sk fuse.sshfs delay_connect,_netdev,user,idmap=user,transform_symlinks,identityfile=/home/juraj/.ssh/rsa,allow_other,default_permissions,uid=1000,gid=1000 0 0

---

### Post by ian-weisser on 2015-12-16
Network-based filesystems should generally be marked 'noauto'. You *don't* want them mounting at the same time as local storage filesystem(s).
There's a reason for that - the local filesystems are mounted *before* the network becomes available.

There probably is a mount-failure for the sshfs filesystem logged in /var/syslog within the first few seconds of boot. That mount failure also slows down your boot (slightly).

One proper way to handle mounting root or multiuser sshfs in 14.04 is to create an Upstart job that mounts the sshfs (a systemd task in newer releases of Ubuntu). The job depends upon both filesystem-up and network-up, and will run before anyone logs in.

Another proper way of handling *personal* files that you want to mount in your /home is to create a user-level Upstart job that mounts the filesystem at login.
Another way of handling personal files is to write a non-Upstart script that does the mount, and place it in your ~/.config/autostart folder.

---

### Post by SeijiSensei on 2015-12-16
I mount remote filesystems with SSHFS from one of my [Linodes]("http://www.,linode.com/") onto another one by running a script from /etc/rc.local on the client machine.  It consists of little more than commands to mount each shared directory like this:
```
sshfs -o allow_other,nonempty user@ip.addr.of.server:/path/to/the/share /path/to/mountpoint
```
That works pretty reliably for me.

---

