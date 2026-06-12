---
title: "nxserver under 8.04 stopped working"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by thehemi on 2008-05-15
Yesterday my nxserver has stopped allowing my connection.
I suppose it has something to do with the OpenSSH update?

$ sudo /usr/NX/bin/nxserver --usercheck scott
NX> 900 Verifying public key authentication for NX user: scott.
NX> 900 Adding public key for user: scott to the authorized keys file.
NX> 716 Public key added to: /home/scott/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: scott.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: scott
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.

I re-created the NX keys, scott's keys and removed any/all
known_hosts files from the system.  I'm not sure why it is
still not working?  I disabled StrictModes, even though my
permissions are fine, but that didn't help either.

Any ideas?

---

### Post by svenbertil on 2008-05-15
I had the very same problem, this is what I did.

First tried generating new keys with nxserver --keygen. However these keys did not work, in my /var/log/auth i got this: (among other things)
ssh_dss_verify: signature incorrect

So I generated a new rsa key with ssh-keygen. The tricky bit was figuring out the places to put this key..

private key went in:
/usr/NX/etc/keys/node.localhost.id_dsa (doubt if this one is necessary)
and in the client

public key went in:
/usr/NX/home/nx/.ssh/authorized_keys2 (the 2 might not apply to your system)
/home/<username>/.ssh/authorized_keys2 (make sure you don't just throw the key in there but replace your current key after "no-port-forwarding,no-agent-forwarding,command="/usr/NX/bin/nxnode"". Otherwise this key would authorize a normal login which is probably not what you want.)


you probably also want to put the key in /usr/NX/share/keys/whatever-the-filename-is since I think that this is from where it reads the keys when you do a nxserver --adduser.


I've been messing with this since I got home from work so the above might not be totally comprehensible... good luck. If it doesn't work, turn on all debug messages in both nx and sshd and you'll get some clues.

---

### Post by thehemi on 2008-05-15
Thanks for the tips.  I actually ran ssh-keygen, leaving the
default locations, and fired up NX again w/o doing anything
else -- and it works!  How weird is that.  Whatever happened
with OpenSSH, it sure seemed to cause a bunch of problems for
people, and several different solutions.

But I'm back into my box now, so all is well again!  :mrgreen:

---

