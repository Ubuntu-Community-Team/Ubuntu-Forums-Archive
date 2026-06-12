---
title: "NFS doesnt work both ways"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-05-10
Hi i can mount my network drives from computer A to computer B but not from computer B to computer A. I get  

```
$ sudo mount -a
mount.nfs: access denied by server while mounting 192.168.1.102:/mnt/sda
mount.nfs: access denied by server while mounting 192.168.1.102:/mnt/sdb
mount.nfs: access denied by server while mounting 192.168.1.102:/mnt/sdc

```

the firewall is off. I have nfs configured correctly(atleast i think i do). 

heres my fstab for the computer that doesn't mount drives

```
192.168.1.102:/mnt/sda /mnt/sdamain nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.102:/mnt/sdb /mnt/sdbmain nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.102:/mnt/sdc /mnt/sdcmain nfs rsize=8192,wsize=8192,timeo=14,intr
```

heres my export for the computer that doesnt mount drives
```
/mnt/sda 192.168.1.1/24(rw,no_root_squash,async)
/mnt/sdc 192.168.1.1/24(rw,no_root_squash,async)
/mnt/sdd 192.168.1.1/24(rw,no_root_squash,async)
/mnt/sdc 192.168.1.1/24(rw,no_root_squash,async)
```


anyone have any clue why this is happening?

---

### Post by leandromartinez98 on 2009-05-10
In order to do that, you have to have installed the client and server nfs services in both machines. The packages are "nfs-common" and "nfs-kernel-server". Probably the server is not installed on one of them. Otherwise, show us the output of "showmount -e" in both machines here and the IP of both machines.

---

### Post by Archer Troy on 2009-05-10
i have both client and server installed on both machines

heres the showmount output for both computers
IP: 192.168.1.101                                                
```
$ sudo showmount -e
Export list for roman-desktop:
/mnt/sdd    192.168.1.1/24
/mnt/sdc    192.168.1.1/24
/mnt/sda    192.168.1.1/24
/media/disk 192.168.1.1/24
```

IP: 192.168.1.102
```
Export list for roman-htpc                                 
/var/lib/mythtv/music        *
/var/lib/mythtv/videos       *
/var/lib/mythtv/pictures     *
/var/lib/mythtv/recordings   *
/files                   192.168.1.1/24
```

---

### Post by leandromartinez98 on 2009-05-11
In the nfs shares I have, the export line is like this:

/home 192.168.0.0/255.0.0.0(rw,no_subtree_check,async)

That is, I'm exporting to the whole 192.168.0.XXX network. I think
you should put, in your case, "192.168.1.0" instead of "192.168.1.1",
that is, it should end with a zero. Otherwise, you can export
directly to the IP of the other machine (if these machines are
the only ones you will be working on):

/mnt/sda 192.168.1.102/24(rw,no_root_squash,async)

(on /etc/exports, to export from 101 to 102)

I suggest changing that, it may help.

---

