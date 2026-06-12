---
title: "NFS problem"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Kedster on 2009-10-25
Hey guys,

Alright so I am trying to sorta test out my skills and get an NFS server working so that i may switch over another computer over to linux

what  need it to do is share 2 folders to everyone. so what I have fallowed [this guide]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html") to set it up

My /etc/exports looks like this
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/ketterer/Downloads 192.168.1.105/255.255.255.0(rw)

```

the Ip and subnet mask is from the connection information of the linux box that i want to access the share from

when I try to mount it on a linux box I get the message 
```
$sudo mount XXX.XXX.X.XXX:/home/Ketterer/Downloads 
mount.nfs: access denied by server while mounting XXX.XXX.X.XXX:/homeKetterer/Downloads
```

I would like the server to be accessable by anyone i think but right now i just want to get it working

---

### Post by renkinjutsu on 2009-10-25
try this
```
192.168.1.0/24(rw)
```

if that doesn't work, your client might be trying to connect using a blocked port, in which case, you'd need to add insecure as an option in your exports file (there may be better alternatives)

---

### Post by Kedster on 2009-10-25
I tried that and the client still go the same message 
how would I change it to insecure mode

---

### Post by renkinjutsu on 2009-10-25
have you re-exported your directories or restarted nfs after editing your exports file?

---

### Post by Kedster on 2009-10-25
yes I have 
i ran 
```
ketterer@ketterer-laptop:~$ sudo gedit /etc/exports
[sudo] password for ketterer: 
ketterer@ketterer-laptop:~$ sudo exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.0/24:/home/ketterer/Downloads".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x


```

---

### Post by renkinjutsu on 2009-10-25
add the option no_subtreee_check

```
192.168.1.0/24(rw,no_subtree_check)
```
and to add insecure (if needed) just add insecure to the list of options like how we added "no_subtree_check"

---

### Post by Kedster on 2009-10-25
i added that insecure option and i still go the same output from the client

now my /etc/exports
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/home/ketterer/Downloads 192.168.1.0/24(rw,no_subtree_check,insecure)

```

---

### Post by renkinjutsu on 2009-10-25
did you remember to export the paths or restart nfs?

the clients are connecting on LAN with IP's 192.168.1.XXX right?

---

### Post by Kedster on 2009-10-25
well its wlan and is 192.168.1.105 
and the server is 192.168.1.100 also on wlan 
And i did reload using the comand
```
 sudo exportfs -a

```

---

### Post by renkinjutsu on 2009-10-25
```
 -a     Export or unexport all directories.
```

hmm.. doesn't seem like exportfs -a gives any indication on whether it exported or unexported the directories... So try running that more than once

also, how are you trying to mount the shares?
like this?
```
sudo mount 192.168.1.105:/home/ketterer/Downloads /mnt
```


edit: i see in your first post, you had ```
$sudo mount XXX.XXX.X.XXX:/home/Ketterer/Downloads 
```
you used the mount command without specifying a mountpoint, is that how you're trying to mount it right now?

---

### Post by fmartinez78228 on 2009-10-25
You can do this command from a client machine: 
```
showmount -e ServerName/ServerIPAddress
```
and this will give you what directories you are exporting using NFS from your server. 
FYI... everytime you make changes to your /etc/exports file restart nfs-kernel
```
sudo /etc/init.d/nfs-kernel-server restart
```
This will ensure your changes take effect
On you client machine it looks like your doing the right mount commands. This is a line from one dir I'm exporting using NFS on a Unbuntu server. I use my Mac to connect to this dir
/d0            192.168.1.0/24(rw,no_root_squash,async,no_subtree_check,insecure)

---

### Post by Kedster on 2009-10-25
server computer = 192.168.1.100
client computer = 192.168.1.105

```
 [showmount -e ketterer-laptop/192.168.1.100
showmount: can't get address for ketterer-laptop/192.168.1.100
```


```
Sudo mount 192.168.1.100:/home/ketterer/Downloads /mnt/download
```

---

### Post by renkinjutsu on 2009-10-25
```
showmount -e 192.168.1.100
```
would be enough

also, Sudo should not have a capital 'S', everything in linux is case sensitive

and you're using /mnt/download as your mountpoint, do you actually have a folder "download" in your /mnt directory?

---

