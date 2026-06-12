---
title: "X2go client"
date: 2019-06-24
forum: Networking &amp; Wireless
---

### Post by chpnp on 2019-06-24
Hi all

I discovered x2go recently and configured it on a first, then o =n a second machine

On the second machine, when i try to connect to the server, i get the following in the terminal which originated the x2go command:

x2go-INFO-8> "Démarrage de la connexion au serveur : xx.xxx.xxx.xxx:nnn"
Enter PEM pass phrase:
Generating public/private rsa key pair.
Your identification has been saved in /home/NAME/.x2go/ssh/gen/key.Lh2370.
Your public key has been saved in /home/NAME/.x2go/ssh/gen/key.Lh2370.pub.
The key fingerprint is:
SHA256:ABunchOFCaractersdJkp4 X2Go Client RSA user key
The key's randomart image is:
(and the image)

I have to enter something as a PEM Passphrase (or carriage return)
on the first machine, i do not have that question nor the few lines afterwards. I get directly the question for the passphrase which is in the key i have prepared for ssh (which question I also get on the second machine, after this prior exchange)

Anyone please can explain me what is happening here which is not happening on the other machine ??
Where am I missing anything ?
thanks !

---

### Post by TheFu on 2019-06-25
IDK, but it sounds like one machine has ssh keys setup PRIOR to x2go and the other one didn't.

x2go uses the NX protocol.  That protocol includes using ssh to tunnel all connections between the client and server, hence the reason that ssh is used.

If you always manually create the keys and push the public key to the remote x2go server PRIOR to setting up x2go between the 2 systems, I don't think you'll see this. 2 commands on the client:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```

---

### Post by chpnp on 2019-06-25
nice try, i generated a new key but still have this message.

Giving it a second thought however, for the first machine, i copied the key with a usb
for the second machine however, i used ssh-copy-id.
Can you see any reason for this behavior ?

[For the avoidance of doubts, I am totally new to using ssh, so my concern is that I do not want to compromise security.
I have disabled login through ssh, so when I tried the copy-id, i found it requested the password of another key which was already created...]


Any other idea anyone ?

---

### Post by TheFu on 2019-06-26
ssh is picky about directory and file permissions.
Basically, all the files need to be 600 except the .pub key files on the remote server, which can be 644. The ~/.ssh/ directory on both systems must be 700.

This assumes that the ~/.ssh/authorized_keys file was properly edited/appended with additional keys.  Each key is a single line. That is a common mistake when people copy/paste. The process often inserts newlines.

---

### Post by jdtilley on 2019-09-12
I know this is a couple months old, but I found a solution to the problem here. [http://www.procmind.com/blog/2015/11/21/x2go-and-ssh-ecdsa-keys/](http://www.procmind.com/blog/2015/11/21/x2go-and-ssh-ecdsa-keys/) It seems the problem is that newer versions of openssh actually produce a ECDSA key when the following is executed.

```
ssh-keygen -t rsa
```

The solution is to create an old-style rsa key like this.

```
ssh-keygen -m PEM -t rsa -b 4096
```

So apparently, the new ECDSA keys aren't supported by x2go. Also, I believe the old dsa keys are no longer supported due to security flaws.

---

