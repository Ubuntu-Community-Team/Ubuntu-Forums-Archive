---
title: "How to See Who is connected via SSH"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Beuntje on 2007-05-17
Is there a way to see who is connected to my pc via SSH.

I know there is the auth.log but i'm want to see those who are connected to my machine in conky

like
SSH Connections
user `admin` is connected from `123.x.x.x` since `12.00pm`

Is this possible???

---

### Post by thelinuxguy on 2007-05-17
```

users

```
shows the users logged in when I login remotely using XDMCP. Should show the same for ssh. Does it?
Can't say anything about the IP and session time though.

---

### Post by Beuntje on 2007-05-18
I see indeed the users connected, but no info on IP and/or how long connected.
And that's what i wanted to see. 

can it be done with an shell script?

---

### Post by thelinuxguy on 2007-05-18
Try this command:
```

w

```

It has a from field. According to the manual, it should be the remote hostname. But since I issued this when there were no remote users, I just get a - against my login. What is your output?

---

### Post by rich.bradshaw on 2007-05-18
```
w
```

or

```
who
```

or

```
finger
```

all show you different info about who is connected.

---

### Post by carlosqueso on 2007-05-18
w does give you hostnames, but not ip's, so I don't know if that helps you. who, gives you hostname and login time, with which you can calculate how long they've been on.

---

### Post by Beuntje on 2007-05-19
w seems like a nice solution.....

lets see what i can make of it after some grep & cut :)

---

### Post by k3nz0 on 2007-05-24
any of those options don't seem to work for me.
w, who, users, fingers all show only me when I know there is another user connected.
if I do a netstat -tap | grep ssh I see two connection. mine and my friends.
any ideas? when I look in the /var/log/auth.log file I see both entries.
when I look in the /var/log/wtmp I don't see him....I don't know what I'm doing wrong.

---

### Post by thelinuxguy on 2007-05-24
> **k3nz0 said:**
> 
w, who, users, fingers all show only me when I know there is another user connected.


Strange! I connected from my virtual XP box (Bitvise Tunnelier ssh client) and the output I got is shown below:
```

thelinuxguy@LinuxGuysMachine:~$ w
 01:14:04 up  3:02,  2 users,  load average: 1.04, 0.92, 0.51
USER       TTY      FROM             LOGIN@  IDLE   JCPU   PCPU 	WHAT
thelinuxguy :0       -                22:12   ?xdm?  10:14m  0.93s 	x-session-manager
thelinuxguy pts/2    192.168.1.101    01:13   57.00s  0.28s  0.28s 	-bash

thelinuxguy@LinuxGuysMachine:~$ who
thelinuxguy :0           2007-05-24 22:12
thelinuxguy pts/2        2007-05-25 01:13 (192.168.1.101)

thelinuxguy@LinuxGuysMachine:~$ finger
Login        Name       	Tty      Idle  Login Time   Office     Office Phone
thelinuxguy  thelinuxguy  	*:0            May 24 22:12
thelinuxguy  thelinuxguy   	pts/2       3  May 25 01:13 (192.168.1.101)

thelinuxguy@LinuxGuysMachine:~$ sudo netstat -tap | grep ssh
Password:
tcp6       0      0 *:ssh                   *:*                     LISTEN     4361/sshd
tcp6       0      0 ::ffff:192.168.1.2%:ssh ::ffff:192.168.1.1:3779 ESTABLISHED12696/sshd: thelinu

```

My router is 192.168.1.1
My Ubuntu box is 192.168.1.2
My Virtual XP box (VMware, bridged network) is 192.168.1.101

---

### Post by NickD-NLUG on 2007-05-24
> **k3nz0 said:**
> any of those options don't seem to work for me.
w, who, users, fingers all show only me when I know there is another user connected.
if I do a netstat -tap | grep ssh I see two connection. mine and my friends.
any ideas? when I look in the /var/log/auth.log file I see both entries.
when I look in the /var/log/wtmp I don't see him....I don't know what I'm doing wrong.

The output isn't as pretty as I'd like, but try:

lsof | grep sshd | grep TCP | cut -c18-28,70-

Similar playing with the output of "lsof" might give you exactly what you're after.

---

