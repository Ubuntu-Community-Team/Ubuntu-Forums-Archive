---
title: "Samba vs NFS"
date: 2005-08-01
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-08-01
As I understand Samba is used to access network drives either on Windows or Linux machines, while NFS is for Linux machines only. I heard that NFS is better for using to access one Linux machine from another. However, it looks to me more complicated to setup NFS than Samba. What is the advantages of using NFS vs. Samba?

---

### Post by morecoffee on 2005-08-01
NFS seem to me easier to set up than SMB, and if you are using linux to linux I would reccomend NFS. All you have to do is edit your /etc/export file, and then mount it with your other machine.

Sharing - open your /etc/expors file, if it is not there create it and add the following. The folder you would like to share, the ip of the machine/machines you are connecting with and the privelages, (rw) read/write (ro) read only.
/home 192.168.1.x(rw) 

Starting - NFS from a command line.
sudo /etc/init.d/nfs start

Mounting - Create a directory for your nfs share, then the following from a command line, where the ip is the share machine, the share folder, and the locally created folder.
sudo mount -t nfs 192.168.1.x:/Share /Local/Share/Dir

Good luck hope this helps :smile: 

Coffee

---

### Post by traemccombs on 2006-07-10
> **morecoffee said:**
> NFS seem to me easier to set up than SMB, and if you are using linux to linux I would reccomend NFS. All you have to do is edit your /etc/export file, and then mount it with your other machine.

Sharing - open your /etc/expors file, if it is not there create it and add the following. The folder you would like to share, the ip of the machine/machines you are connecting with and the privelages, (rw) read/write (ro) read only.
/home 192.168.1.x(rw) 

Starting - NFS from a command line.
sudo /etc/init.d/nfs start

Mounting - Create a directory for your nfs share, then the following from a command line, where the ip is the share machine, the share folder, and the locally created folder.
sudo mount -t nfs 192.168.1.x:/Share /Local/Share/Dir

Good luck hope this helps :smile: 

Coffee


I have all of the above in place, and can nfs mount the remote drive, and access its files.  The only problem is, when I press enter on the mount command: mount -t nfs ip:dir mount_dir   it just sits there and hangs.  And hangs.... for about 2 minutes, and then FINALLY, it goes thorugh.

I thought it might be ipv6 causing the problem so I turned it off via a howto I found here on the forums.  Nope that's not it.

I thought it might be no entries in the hosts file... I added those.  Nope, that's not it.

I was running strace on it, and I'm seeing some of these:

```

open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)

```

Here is where it hangs:

```

socket(PF_INET, SOCK_STREAM, IPPROTO_TCP) = 3
bind(3, {sa_family=AF_INET, sin_port=htons(784), sin_addr=inet_addr("0.0.0.0")}, 16) = 0
uname({sys="Linux", node="cigars", ...}) = 0
rt_sigprocmask(SIG_BLOCK, ~[TRAP SEGV RTMIN RT_1], NULL, 8) = 0
mount("bighair:/home/october/myFiles", "myFiles", "nfs", MS_POSIXACL|MS_ACTIVE|MS_NOUSER|0xec0000, 0x805bd40

```

{heh, as far as the host names go, I'm a U2 fan, go look up the song "Miami"}

Any ideas?  This is working, it's just the looong timeout that is bugging me.

Thanks tons in advance,
Trae

---

### Post by traemccombs on 2006-07-10
OK, this might help someone.

On the machine that was hanging, I simply did the following:

apt-get install portmap nfs-common

and poof, it is mounting just fine and peachy now.  Not sure if it was a combination of all of the foo I did, or if it simply needed portmap and nfs stuff on the local box.  Whew. 

Hope this helps.

Trae

---

