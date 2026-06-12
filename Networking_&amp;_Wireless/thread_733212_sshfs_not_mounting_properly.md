---
title: "sshfs not mounting properly"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by Tiny Grasshopper on 2008-03-23
Hello,

I'm setting up a file server. I want to use sshfs to access the files from outside the LAN. The machine is running proftpd on gentoo on a non standard port. I can ssh into the machine from both inside the lan with its internal ip and outside the lan with the external ip and port forwarding.

I tried to setup sshfs on two machines, one inside the lan and one outside and i get the same thing happening:

First I installed the sshfs package

```
sudo apt-get install sshfs
```

Then I added myself to the fuse group

```
usermod -a -G fuse chris
```

Then I tried to mount it with sshfs
```

sudo sshfs -p 12321 [email]chris@192.168.xxx.xxx[/email]:/home/chris testfolder
```

It appears to work. It asks me for the password, i put it in, it gives me no error but i cd into the folder and i get

```
$ cd test
bash: cd: test: Permission denied
```

and ls -l tells me this
```

$ ls -l
...
?---------  ? ?           ?                ?                ? test
...
```

This was attempted with both the internal ip from another machine in the lan and the external ip from outside and the same thing happens.

I thought i read somewhere that I need the openssh server installed on the machine accessing the ssh mount, so I
```

$ sudo apt-get install openssh-server
```

and tried it again and the same thing happened.

Does anyone have any insight on this?

---

### Post by Tiny Grasshopper on 2008-03-23
Well I think I may have figured it out, Someone verify if this was the right thing:

I uncommented the line

```
user_allow_other
```

from /etc/fuse.conf

and when I mounted it it was with the following options
```

sudo sshfs -p 12321 -oallow_other [email]chris@192.168.xxx.xxx[/email]:/home/chris testfolder
```

This seems to have worked. Hopefully I didn't do anything that was not necessary.

---

