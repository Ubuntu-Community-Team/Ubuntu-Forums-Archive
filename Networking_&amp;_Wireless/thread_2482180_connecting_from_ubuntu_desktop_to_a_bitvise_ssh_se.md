---
title: "connecting from ubuntu desktop to a bitvise ssh server with keys"
date: 2022-12-23
forum: Networking &amp; Wireless
---

### Post by matt18 on 2022-12-23
Ok, i have a windows box setup about 3 hours from my house at my parents. It is currently running bitvise ssh server with keys and only one account allowed. 

I have tried to connect and it fails due to no keys on the ubuntu desktop i just installed. This at least lets me know it has connectivity.

Where i am stuck, i have exported the private key from bitvise, but have no idea where i need to put it on my ubuntu desktop so when i use "other locations" in file manger, that it will use the actual private key. 

Ubuntu is running in a vmware player 17 machine. Its the newest version of ubuntu LTS.

Also, just in-case, what is a great GUI for sftp available in ubuntu?

Thanks.

---

### Post by TheFu on 2022-12-28
> **matt18 said:**
>  Also, just in-case, what is a great GUI for sftp available in ubuntu?

Almost any file manager supports the sftp:// URL type.  Some call it ssh:// or fish://, but if the ssh-client packages are installed, I think all the popular file managers support it.

I don't know anything about bitvise.

However, ssh keys are typically created on the client machine using 'ssh-keygen' then pushed to the remote server using 'ssh-copy-id'.
2 commands, that's it.  Sadly, when MSFT added sshd to their Win10 systems, they didn't implement ssh-copy-id, so Windows ssh clients need to manually push the public keys over.  I've helped a few people setup ssh keys on Windows as clients.  ssh-keygen is the same command, just use MS-Windows paths instead of Unix paths for the key output locations.
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
On the ssh client system:
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote

```
If you choose/need to use RSA keys, be certain to force 4Kb lengths or longer.  ED25519 is rumored to be easier to solve by quantum computers.  In 2017, I switched to ed25519 keys. Could make sense to switch back to long RSA keys. YMMV.

On Unix systems, ssh client stuff goes into ~/.ssh/ . There are different files for different purposes.  There's an O'Reily book about ssh, if you need more information or use [https://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols](https://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols) wikibook on ssh and ssh-based tools.

---

