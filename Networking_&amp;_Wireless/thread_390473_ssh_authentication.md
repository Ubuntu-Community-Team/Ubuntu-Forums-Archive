---
title: "ssh authentication"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by Ephilei on 2007-03-22
Hi

I'm configuring my home server with ssh to access it from the Internet, so there are no other users on the machine that I don't trust. Is a passphrase still recommended or will a password suffice? Are passphrases safer from sniffers?

---

### Post by bloodniece on 2007-03-22
Personally, I use Firestarter to create a rule that only permits specific IP addresses from accessing port 22 (SSH) on my home network. then, I set my router to forward port 22 to the local IP of my Ubuntu server.  I still use a password though.

---

### Post by Ephilei on 2007-03-23
Good idea, but not for me. 

I didn't think this was a difficult question so I'm surprised no one's answered.

---

### Post by gradedcheese on 2007-03-23
ssh traffic is encrypted, sniffing it won't do much good.

Use public keys instead.  It works like this:

1) on the machine(s) from which you want to connect to that server, generate keys:
```

ssh-keygen

```
This creates a file named ~.ssh/id_rsa.pub

2) on the server, place the contents of your id_rsa.pub file(s) into a file named:
```

.ssh/authorized_keys

```
(one per line).  Now set the permissions for the .ssh directory like this:
```

chmod -R 600 .ssh
chmod +x .ssh

```

3) try connecting from one of your machines, you'll see the key used instead.  Once you're satisfied, disable 'password' as an allowed authentication method (so that 'key' is the only way in).  This way only people who have keys added to authorized_keys have access, and only from the machines where those keys came from.

---

