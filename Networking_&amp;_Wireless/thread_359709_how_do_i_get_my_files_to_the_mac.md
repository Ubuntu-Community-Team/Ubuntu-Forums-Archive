---
title: "how do i get my files to the mac?"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by fabbaz on 2007-02-12
i found several threads about how to get files from the mac to ubuntu, but my problem is:
i have a new macbook, and i would like to get all my stuff and music and pictures from ubuntu onto my new laptop. i have no idea how to setup such a network connection.
options are connecting via firewire 400 and ethernet cable, both have internet access via wlan.

help?

thank you

---

### Post by jshein on 2007-02-12
Use scp

# scp /path_to_files/filenames_or_wildcard user@destination:/path_to_destination_directory/

---

### Post by fabbaz on 2007-02-12
which i would enter where? in the gnome-terminal?
i am not familiar with scp. what will happen when i enter that?
thanks for your help!

---

### Post by jshein on 2007-02-12
You would enter this in your preferred terminal program. scp is used to copy files over ssh to or from a remote machine.

To find out more, type "man scp" in a terminal to see the manual pages.

---

### Post by das_syndrom on 2007-02-13
Hi!

The drawback of ssh/scp is that is is quite slow (because of the encryption/decryption it uses).

Maybe you should also have a look at NFS (network file system)
[NFS-Howto]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[NFS-Howto_in_german]("http://wiki.ubuntuusers.de/NFS?highlight=%28NFS%29")

Andi

---

### Post by geezerone on 2007-03-10
I am trying to scp a file from local host to Smoothwall but have tried this to no avail and get the following:

```
scp /home/john/Desktop/dansguardian-2.8.0.6.tgz root@192.168.1.3:222 /tmp/

ssh: connect to host 192.168.1.3 port 22: Connection refused
```

I can connect via gFTP using SSH2 but want to be able to use command line :) 

P.S. I have looked at the man pages but not clear what I need to type.

Thanks!

---

### Post by geezerone on 2007-03-10
scp -v -P222 /home/john/Desktop/dansguardian-2.8.0.6. tgz root@192.168.1.3:/tmp

This worked perfickly! Just had to login and certificates accepted ok.

---

