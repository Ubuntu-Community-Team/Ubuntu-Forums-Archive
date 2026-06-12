---
title: "FreeNX SSHD issues"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by scribbles on 2009-02-09
I'm trying to go from a windows freenx client to a kubuntu machine. SSHD is fully up and running and works fine with putty. Per information I've found online, I went ahead and ran ssh-keygen and generated a pub/priv dsa keypair. I moved the pub dsa key to /var/lib/nxserver/home/.ssh/authorized_keys2 and then imported the pub key into my windows nx client.

When I go to connect it says connected to machine and then:
```
DSA key is corrupted or has been protected with a passphrase.
```

I made sure not to enter a password when using ssh-keygen... this is the new error when before I was getting pubkey auth failed...

There doesn't seem to be much documentation on resolving errors with this, can anyone shed some light?:confused:

---

