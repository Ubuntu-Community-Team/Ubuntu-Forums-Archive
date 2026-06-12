---
title: "How to mount a remote ubuntu system"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by jonno on 2008-01-13
This is probably a fairly basic question.

I want to use grsync to backup data to another drive in my home network. The remote drive is running mythbuntu 7.10.

What is the simplest way to do this? I don't need any capability other than for the drive to just be accessible to grsync whenever it needs it. I'd rather not be putting in passwords all the time as I'd like to be able to set up the profile in grsync and then run grsync whenever I'd like.

The remote drive is on my home network via a wireless connection via dhcp if that matters.

---

### Post by schallstrom on 2008-01-13
If you want to sync directorys on different computers you should consider using unison instead of rsync.

To answer your question: I'm using samba and sshfs to mount remote filesystems. sshfs is probably most easy to use. Just install the package:
```

sudo aptitude install sshfs

```
Then you have to add your user to the 'fuse' group:
```

gpasswd -a username fuse

```
After that, restart Gnome, so the new group membership gets active.
Then you can mount a directory on the remote machine like this:
```

sshfs user@remotemachine:/path/to/dir /local/mount/point

```
If your local and remote usernames are the same you may omit the "user@" part, just like when you make a ssh connection.

If you don't want to put in your password all the time, just add your ssh key to the authorized_keys at the remote machine.
Therefor create a ssh key on the local machine (if you don't have one already):
```

ssh-keygen

```
Don't enter a passphrase for the key (the private key will be placed in ~/.ssh, make sure nobody will get access to it! If somebody gets access to your ssh private key, she will be able to get access to all machines where you put the public key without a password!).
Then put the public key to your remote machine like this:
```

ssh user@remotemachine "mkdir ~/.ssh"
cat .ssh/id_rsa.pub | ssh user@remotemachine "cat - >> .ssh/authorized_keys"

```

---

### Post by jonno on 2008-01-13
Thanks. I will look into sshfs and Unison also. The only thing I haven't set up yet in grsync is  to automate running the thing. Maybe you can let me know what other differences you know of between the two.

As for sshfs do  I need to install this on the remote machine also?

---

### Post by schallstrom on 2008-01-13
I just know that unison is much newer and therefor probably more advanced. And that me and rsync never got friends. I never managed to get it to do exactly what I want it to do. I read about unison in the Ubuntu wiki and that it is the recommended solution for syncing two directories, so I tried it and it worked immediately. It has a graphical front end like grsync and a command line front end for automation and 1337 users.

You don't have to install sshfs on the remote machine, but there must be a ssh server installed and running:
```

sudo aptitude install openssh-server
sudo /etc/init.d/ssh start

```

---

### Post by jonno on 2008-01-13
Well I have managed to ssh or sshfs into the remote machine using the ip address but since I'm using dhcp I'd rather use the computer name. However I've tried user@computername and I get either:
ssh: jonno-mythbuntu: Name or service not known
or
read: Connection reset by peer when I try the sshfs directory mapping.

What am I missing? I guess somehow I need something that associates the computername with the ip address.

---

### Post by jonno on 2008-01-14
Well somehow I got it working using samba. Also figured out what to put in etc/fstab to get the directories to mount automatically on boot (I think). Now I can run grsync any time.

Now I just need to figure out how to get the remote wireless system to connect without prompting me for passwords.

---

### Post by schallstrom on 2008-01-15
1) There are several ways to map an IP address to a host name. But the precondition for being able to do it is, that the affected machine always has the same IP address! That is not the case automatically when using DHCP. The DHCP server always gives the client a random IP address when not explicitly instructed otherwise. So first you would have to configure the DHCP server to map the MAC address of the affected client to a fixed IP address. You can find out the MAC address of your Ethernet device with 'ifconfig':
```

root@shuriken:~# ifconfig 
eth1      Link encap:Ethernet  HWaddr [COLOR="Red"]00:19:D2:08:00:1C[/COLOR]  
          inet addr:87.77.200.190  Bcast:87.77.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:d2ff:fe08:1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1441 errors:0 dropped:5124 overruns:0 frame:0
          TX packets:1515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16744869 (15.9 MB)  TX bytes:2213859 (2.1 MB)
          Interrupt:21 Base address:0x4000 Memory:edf00000-edf00fff 

```
When you have configured your DHCP server and now know that the host always has the same IP address, you could enter the host to you /etc/hosts file:
```

root@shuriken:~# cat /etc/hosts
192.168.5.23 foo
192.168.5.64 bar

```
But now, only the host with the /etc/hosts file knows about this IP/name mapping. If you want to make the mapping available to the whole network, you need a DNS server. Most easy way to achieve this: Install dnsmasq. dnsmasq is a very easy DNS server for small networks which needs almost no configuration because it uses the information from the /etc/hosts file.

2) For not having to enter you samba password all the time, do something like this:
```

mount -t cifs //remotehost/dir /mnt/mountpoint -o credentials=~/.smbcredentials

```
The credentials file has to look like this:
```

username=foo
password=bar

```

Hope that helps.

---

### Post by jonno on 2008-01-15
Ok I have the credentials set up like you said and that works fine.

As for fixing the ip address of the remote machine I'll look for the mac address tonight. I'm guessing I need to give that info to the DNS server settings on my router somewhere (WRT54G).

Since samba seems to have made the link from that remote ip to the remote computername I think I'm sorted with the rest of it.

---

