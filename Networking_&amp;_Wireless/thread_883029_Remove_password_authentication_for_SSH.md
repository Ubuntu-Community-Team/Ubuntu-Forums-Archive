---
title: "Remove password authentication for SSH?"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by PremiumAlex on 2008-08-07
Hi there!

I'm trying to get a SSH tunnel set up on my home computer so I can set up VNC through SSH on my work computer. I'm having troubles with public keys and password authentication, however. I want to disable passwords and strictly use public keys, but even with the configuration options set, I still get a password prompt. The keys also aren't working, as I removed the keys from the ~/.ssh/ folder. I also restarted ssh and the computer multiple times with no effect.

Anyone have any ideas?

Also, I've read the wiki on SSH and followed the instructions for setting up SSH w/ public keys on _[this thread.]("http://ubuntuforums.org/showthread.php?t=30709")_

The odd part is that I still get password prompts after I set 
```

#   PasswordAuthentication yes

Change to:
  
PasswordAuthentication no
UsePAM no
```

in /etc/ssh/sshd_config.

---

### Post by ilrudie on 2008-08-07
What version of Ubuntu are you using?  I have Hardy setup with key authenticated ssh and it works just fine.

---

### Post by PremiumAlex on 2008-08-07
I'm using 8.04 with the newest kernel version.

It's just so strange. Here is how I connect through SSH, if it helps:

Let's just assume both compters are on my local network for now, to get things set up.

I have my key created on the remote machine using 
```
ssh-keygen -t rsa
```

and then I manually copied the contents of id_rsa.pub to ~/.ssh/authorized_keys on my local machine (the one I want to connect to).

I then went to /etc/ssh/sshd_config on the local machine and turned password authentication and UsePAM to off. Restarted SSH and restarted the computer.

I then try to login to my system remotely:
```
ssh 192.168.1.xxx
```

and I still get a password prompt! it's craziness, I tell ya.

---

### Post by ilrudie on 2008-08-07
The keys should go in ~/.ssh/authorized_keys2

also ssh -v will show you what ssh is doing.  It should shed some light on what exactly is happening.

Also make sure you specify a user or you have the same username on both machines.

---

### Post by PremiumAlex on 2008-08-07
All right, I'll change the authorized_keys to authorized_keys2 when I get home from work and let you know how it goes.

---

### Post by xc3ll on 2008-08-07
Do you have a passphrase set for your keys (I'm not sure if ssh does it automatically) ?

If you don't, run:

$ssh-keygen -p

---

### Post by tortsto on 2008-12-09
moving ~/.ssh/authorized_keys to authorized_keys2 made it work for me!

Thanks a lot!

---

