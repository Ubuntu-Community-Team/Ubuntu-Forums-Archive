---
title: "Not able to connect to remote server using ssh and private key"
date: 2015-07-19
forum: Networking &amp; Wireless
---

### Post by tobias13 on 2015-07-19
Hello,
I just installed Ubuntu 14.04. LTS on my new laptop and was trying to connect to my remote server using ssh and the private key which I set up to log in to the server.
If I try to log in from my Windows PC using Putty and the key, everything works fine, but when using Ubuntu the passphrase for the private key gets rejected every time I enter it.

This is how my ~/.ssh/config looks
```
Host serverliste
  HostName xxx.xxx.xxx
  User root
  IdentityFile ~/path/to/private.ppk
```
So when I try to connect to the server using
```
ssh root@serverliste
```
I get prompted to enter the passphrase:
```
Enter passphrase for key '/home/tobias/path/to/private.ppk':
```
But if I then enter the passphrase correctly (100% sure) I get the same prompt again and again for 3 times and after that I get this error:
```
Permission denied (publickey).
```

Remember that the same key with the same passphrase worked flawlessly on Windows with Putty.
Has anybody had the same or similar problem or is able to offer some advice?

Greetings

---

### Post by Lars Noodén on 2015-07-19
I read that PuTTY uses a different format which would have to be converted using puttygen:

[http://stackoverflow.com/questions/2224066/how-to-convert-ssh-keypairs-generated-using-puttygenwindows-into-key-pairs-use](http://stackoverflow.com/questions/2224066/how-to-convert-ssh-keypairs-generated-using-puttygenwindows-into-key-pairs-use)

or ssh-keygen...

---

### Post by tobias13 on 2015-07-19
Thanks a lot!
Exporting the key in OpenSSH format using puttygen worked

---

