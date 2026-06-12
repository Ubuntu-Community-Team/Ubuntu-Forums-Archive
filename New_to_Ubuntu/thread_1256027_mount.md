---
title: "mount"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Drenriza on 2009-09-02
im trying to mount a cd ower a network with ssh.

i have tryed the command mount -t iso9660 -o ro /dev/cdrom 
and it just keep saying no media found.
i've also tryed mount -t iso9660 -o ro /dev/cdrom /cdrom then it just says the same.

Is it me that is doing something wrong in the command?

Thanks on advance:KS

---

### Post by vanadium on 2009-09-02
To mount a CD over the network, make sure it is mounted in the remote file system (i.e. on the server) first. Then you can mount it over ssh in the local file system using sshfs.

---

### Post by fela on 2009-09-02
Or you could make an NFS or Samba share on the computer with the CD drive. Then on the client, when the CD is in the server, just mount that NFS or Samba share.

---

### Post by Drenriza on 2009-09-02
is it possible that you can come with an example of sshfs?

---

### Post by vanadium on 2009-09-02
For this to work, you must first of all be able to log in with ssh on the server. For this, the ssh server (openssh-server) must be installed on the server (remote machine). This is not by default on an Ubuntu desktop system. With synaptic, or using "sudo apt-get install ssh, you will install the server as well if that was not installed before.

Once the sshserver is installed, you should be able to log in on your remote machine, the server, using the "ssh" command (e.g. "ssh myserver.somewhere.com"). When prompted, provide your user name and passwoord corresponding to your account on that server.

For the sshfs part, this is where I took my wisdom a long time ago. [http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-mount-a-remote-folder-using-ssh-on-ubuntu/) I believe that the installation part of sshfs is not needed, because sshfs is installed by default with recent Ubuntu versions. Thus all you need is create the mount point and mount the server:

```

mkdir ~/remoteserv
sshfs <username>@<ipaddress>:/remotepath ~/remoteserv

```

The remotepath could be the pad directly to your cdrom.

---

### Post by Drenriza on 2009-09-07
is their a guide somewhere to see all sshfs functions and how they work?

---

