---
title: "nfs and fstab"
date: 2015-08-13
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2015-08-13
what am I doing wrong?

server /etc/exports
```

/home/tor 192.168.2.0/255.255.255.0(rw,sync,root_squash)

```

client /etc/fstab
```

# nfs
192.168.2.4:/home/torrent /home/lance/bermudezl nfs rsize=8192,wsize=8192,timeo=14,intr

```

error
$ sudo mount -a
mount.nfs: Connection timed out

---

### Post by papibe on 2015-08-13
Hi lance bermudez.

A couple of observations:
[LIST]
[*]It looks you are exporting 'tor', but trying to mount 'torrent'
[*]You are missing a couple of options on the fstab. Typical values would be a zero and a two:
```
192.168.2.4:/home/torrent /home/lance/bermudezl nfs rsize=8192,wsize=8192,timeo=14,intr  **0  2**
```[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lance bermudez on 2015-08-13
added the 0 2 to the end and I still get 

$ sudo mount -a
mount.nfs: Connection timed out

also made sure that my firewalld was open
$ sudo firewall-cmd --permanent --zone=public --add-service=nfs
Warning: ALREADY_ENABLED: nfs

---

### Post by papibe on 2015-08-14
Did you restart the nfs service on the server after modifying the exports file?
```
sudo service nfs-kernel-server restart
```
Could you run this command on the client:
```
showmount -d 192.168.2.4
```
Regards.

---

### Post by SeijiSensei on 2015-08-14
> **papibe said:**
> **It looks you are exporting 'tor', but trying to mount 'torrent'**

Did you fix this?

---

### Post by lance bermudez on 2015-08-18
Yes I got it working with making sure the nfs port was open on all machines

ufw allow in log-all from 192.168.2.0/24 to any port 2049
sudo firewall-cmd --permanent --zone=public --add-service=nfs

and using this in the /etc/fstab
192.168.2.4:/home/tor /home/tor nfs rsize=8192,wsize=8192,timeo=14,intr

I think I focused to much on the /etc/fstab config then firewalls but after I recheck the firewalls and the config things just seemed to work. Thank you all for your help.

---

