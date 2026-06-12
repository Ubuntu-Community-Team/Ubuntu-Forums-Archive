---
title: "SSH to unmounted partition?"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by Ray_Jones on 2015-04-24
A family member only occasionally uses her computer, but she has a lot of unused drive space on her new machine. I partitioned her disk to a primary partition (logical) that mounts at root. Then I created a second partition that I would like to use for storage space from my box via OpenSSH. Does her machine need to mount the second partition before my system can access it via SSH? Or can my machine mount the unmounted partition directly? Both of us are running Kubuntu 14.04.

---

### Post by papibe on 2015-04-24
Hi Ray_Jones. Welcome to the forum ):P

Yes. It needs to be mounted first.

This can be set so that it is automatically mounted when the system boots, or mounted manually over ssh (you would need admin permissions).

The easiest way to access it remotely using either [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html"), or [samba]("https://help.ubuntu.com/community/Samba"). That way it would appears "as if" it were a local partition.

Another alternatives would be to use several protocols over ssh, like rsync, sftp or scp.

Does that help? Let us know how that goes, and if you have more questions.
Regards.

---

### Post by Ray_Jones on 2015-04-24
> **papibe said:**
> Hi Ray_Jones. Welcome to the forum ):P  Yes. It needs to be mounted first.  This can be set so that it is automatically mounted when the system boots, or mounted manually over ssh (you would need admin permissions).  The easiest way to access it remotely using either [NFS]("https://help.ubuntu.com/lts/serverguide/network-file-system.html"), or [samba]("https://help.ubuntu.com/community/Samba"). That way it would appears "as if" it were a local partition.   And please allow me to add one more level of complexity. What if that partition is encrypted using dm-crypt or something similar? What does that do to my ability to mount and decrypt that partition once I have mounted the raw partition locally?

---

### Post by Ray_Jones on 2015-04-27
Update....
I was able to find a solution by encrypting the storage partition on the family member's machine, auto mounting the raw partition on its local machine, and decrypting it there as well. I can then mount the decrypted partition over the network on my machine using sshfs.

Clear as mud??? ;)

---

