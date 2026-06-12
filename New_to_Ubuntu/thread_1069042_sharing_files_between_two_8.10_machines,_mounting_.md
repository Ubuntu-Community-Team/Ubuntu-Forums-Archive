---
title: "sharing files between two 8.10 machines, mounting the share using /etc/fstab"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by PaganBlasphemy on 2009-02-13
does anyone have a link to a simple guide to share files between two 8.10 machines?  specifically one where you mount the shares via /etc/fstab?

I'm having nothing but problems, and it seems like every guide I find is different, and mostly dealing with older versions of ubuntu.

I'm having a problem now that the files I'm trying to read and write to are owned by different people depending upon which machine I'm sitting at.  Locally they're owned by the local user, and the permissions are 777.  Remotely, they're owned by a remote user, and the permissions are 777.  My remote user can't write to the files even though everything looks right with regards to the file permissions, although the files are not owned by the local user (how is that even possible?!?!).

I've tried a lot of different /etc/fstab options, and none of them seem to make any difference.  This is what I am currently using:

```
//192.168.8.30/shared /home/lan cifs credentials=/root/.smbcredentials,defaults 0 0

```

It seems ridiculous to me how hard this is, and how complicated.  I cannot believe there isn't a GUI for accomplishing these things in a standard manner.  Mounting network shares between two 8.10 boxes ought to be beyond effortless, and instead it is unfathomable.  Worse yet is that everything I find via google seems contradictory or out of date.  And don't even get me started on the state of this forum.  Instead of useful threads being cataloged and the information added to a central repository, they're "archived" where I can no longer add my question to a thread that is a couple years old, even though it is still entirely relevant to even the latest edition of Ubuntu.  (fail)

I'm ready to take a chainsaw to this network.:confused:  I'd probably start laughing maniacally and be unable to stop.

---

### Post by fraser_m on 2009-02-13
```
shares-admin
```

Install Samba, use the GUI to sort.

---

### Post by PaganBlasphemy on 2009-02-17
samba is a collection of tools required to share data between linux and windows machines.  I am working with two ubuntu desktops.

I finally found this, after beating my head off my desk for days, it was literally two minutes of CLI work and no reboots: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

It was perfect for my installation, where I have a controlled network that has multiple machines I want to have access to one machine's shared directory.  Very simple, very fast, very easy.  

Literally:

On the server

Install the software
```
sudo aptitude -P install nfs-kernel-server nfs-common portmap
```

Configure the shared directory
```
sudo nano /etc/exports
```
```
/home/share 192.168.8.1/24(rw,no_root_squash,sync,no_subtree_check)
```

Propagate the config changes
```
sudo exportfs -ra
```

On the clients

Install the software
```
sudo aptitude -P install nfs-kernel-server nfs-common portmap
```

Configure fstab to import the directory on startup
```
192.168.8.30:/home/share /home/lan nfs defaults 0 0
```

Propagate the config changes
```
sudo mount -a
```

This was so straightforward, it was absurd.  Apparently you can set it up to use user authentication and complicate things a bit, but this worked perfectly for me.  Very little mention of NFS in the various HOWTOs and guides.

As someone working through a lot of this for the first time, allow me to repeat what I'm sure countless others have already said: "the state of ubuntu documentation is atrocious".

---

