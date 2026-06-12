---
title: "ssh to get to system files"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by merlinus on 2015-09-24
I have logged in to a remote computer on my network using ssh and that machine's ip address.  But I can only get to directories and files in my /home, and not to system files and other partitions.

Any way to do this?

---

### Post by ian-weisser on 2015-09-24
Hmmm. It should be *exactly* the same way you navigate your local machine...if you are using shell. 'cd',  etc.

How are you trying? Shell commands? GUI? Something else?
What kind of failure do you get? Error message? Nothing? Redirection?

---

### Post by merlinus on 2015-09-24
It logs into my /home directory on the remote computer, and I cannot get to anything else, e.g. system files and other named partitions.  This is true whether I use the terminal or Places/Connect to Server.

I have all permissions on that machine.

---

### Post by steeldriver on 2015-09-24
it sounds like your account is restricted to an SSH chroot "jail" on the remote machine... ?

---

### Post by merlinus on 2015-09-24
> **steeldriver said:**
> it sounds like your account is restricted to an SSH chroot "jail" on the remote machine... ?

So how can this be changed?  It was not set up that way, as I can log into another machine on the LAN with my account on it and get to anywhere.

ALso, when I use ssh://ip  it changes to sftp://ip.

---

