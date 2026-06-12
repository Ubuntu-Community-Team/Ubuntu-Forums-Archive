---
title: "How to access SAMBA (server: Ubuntu, client: Ubuntu)"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by g117 on 2011-07-03
Hi there!

I have a SAMBA server installed on my first PC and I need to mount this on my laptop.

My PC (where a SAMBA server is installed):
IP: 192.168.1.251
some username (say 'gabriel') and some password (say 'pass')
Ubuntu installed on it (10.10)

My laptop:
connected to the same network, can access the PC (tried through ping 192.168.1.251)
Ubuntu installed on it (11.04)

I tried this: 
```

sudo mount -t smbfs -o username=gabriel //192.168.1.251/ /mnt/

```

and I've got this:
```

Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

I would really appreciate some help. Thanks.

---

### Post by DutchLoki on 2011-07-03
Lets first look where it goes wrong. Try to list shares that are available from your Samba server, execute the following command:
$ smbclient -L yourhostname

You should see a list of shares available on your server. If you do not, then something is incorrectly configured.

If you see a list, try connecting to the service.
$ smbclient  //yourhostname/servicename

Now there should be an active connection. Please post you´re findings here so we can help you further. Also check the following links for troubleshooting.

[Samba troubleshooting checklist]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html")

[Analyzing and Solving Samba Problems]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/problems.html")

---

### Post by g117 on 2011-07-03
Should I run the command from my laptop? (where samba is not installed, samba is installed on my desktop PC). If yes, here's the output: 
```

...@g-laptop:~$ smbclient -L g-ubuntu
Enter ...'s password: 
Connection to g-ubuntu failed (Error NT_STATUS_UNSUCCESSFUL)
...@g-laptop:~$ 

```

---

### Post by DutchLoki on 2011-07-03
Hi, could you run the first command from your desktop pc? (this is your samba server).

Run the second command from your laptop (this is the samba client).

---

### Post by Morbius1 on 2011-07-03
I can reproduce your error in seconds:
```
sudo mount -t smbfs -o username=morbius //192.168.0.110/ /mnt
Password: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```That's because I'm trying to mount an entire remote machine. But if I add a specific share everything is fine:
> sudo mount -t smbfs -o username=morbius //192.168.0.110/Documents /mnt

---

### Post by DutchLoki on 2011-07-05
Hi g117, did this help you solve your problem?

---

