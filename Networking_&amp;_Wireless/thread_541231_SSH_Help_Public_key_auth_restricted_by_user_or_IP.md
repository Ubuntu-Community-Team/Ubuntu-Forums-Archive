---
title: "SSH Help: Public key auth restricted by user or IP"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by wallacetheweasel on 2007-09-02
I have an SSH server running on an old PC around my house which I use for various things.  I would like to automate some things (like backup, X-forwarding programs) on various computers on my network, for myself and the rest of the family.  To do so, I want to enable password-less SSH connections using Public/Private key authentication, but only for local IPs or only for certain users.  Maybe both, to be on the safe side.

I've searched around and I haven't found much documentation on this.  Any sshd_config gurus out there who can point me in the right direction?

---

### Post by kevdog on 2007-09-02
Not sure how to do this on a user basis (since your users need to have an account on the server), but setting up your Firewall to only allow local IPs would be one was to limit to a certain IP addresses.  Also the authentication mechanism reads the /etc/hosts.all and etc/hosts.deny files, so you could further limit certain IP addresses in these files.

---

### Post by wallacetheweasel on 2007-09-02
Ah, I didn't explain myself clearly enough. I can easily look up how to limit the whole ssh server by user (using AllowUsers) or by IP.  My tricky problem is that I would like to allow ssh access to all users from all IPs when using passwords and pub key, but allow password-less login (using Pub/Priv key auth) for only either:

a) Specific users
b) Connections from local IPs

I'm sure this is possible, but it's slightly tricky and I can't figure out how.

---

### Post by Bachstelze on 2007-09-02
I think I don't understand your problem... SSH keys must be put in the home SSH folder of a user (~/.ssh/authorized_keys). How is that not "for certain users" ?

---

### Post by kevdog on 2007-09-02
I understand what you want to do, however Im not well versed enough to tell you how to do this.  You would have to find out how to fine tune your authentication process.  I dont think its possible to fine tune either the sshd_config or hosts.allow file to do what you want.  Im sure there is a way to modify the source code to allow you to first detect whether a key is being used or not, and then default to the appropriate authentication process, however this would require at the minimum some scripting and likely some coding.  Sorry I cant help you.  I have never delved into the ssh server source code.

---

