---
title: "Installing software in a unattended way"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by csrrmrzrn on 2008-11-17
hi everybody.

I'm really newbie in the ubuntu world and I need a application to install software in a network (many pcs) in a unattended way. Do you know? Like create an image and then puting it to install, so that I do not have to go into computer by computer to install the software.

So, the question is: Is there a software to do that?

---

### Post by forbjok on 2008-11-18
If the PCs are all running Ubuntu, then you could use SSH to do that, assuming you can get all the clients set up running OpenSSH.

Since SSH can use pubkey authentication, you could put your administrative pubkey in the authorized_keys files of all the machines, and use SSH to run apt-get commands on them.
(EDIT: You will probably also have to add NOPASSWD to that administrative user in the sudoers file on each machine)

Example: $ ssh adminuser@192.168.1.1

See the manpages for "ssh-keygen", "ssh-copy-id" and "ssh" for more info.

---

### Post by csrrmrzrn on 2008-11-18
but I think using SSH is not really unattended, cause there are softwares that requires some parameters to be installed. For example, when they need the answer "yes" to install the dependencies, where the DNS server is and so on...

---

### Post by forbjok on 2008-11-18
> **csrrmrzrn said:**
> but I think using SSH is not really unattended, cause there are softwares that requires some parameters to be installed. For example, when they need the answer "yes" to install the dependencies, where the DNS server is and so on...

Any yes/no queries could be avoided by specifying the "-y" option to apt-get.

If anything more than that needs to be specified during installation, then I can't think of any way to do it unattended, unless the Ubuntu package system has some sort of built-in feature to handle this.

---

