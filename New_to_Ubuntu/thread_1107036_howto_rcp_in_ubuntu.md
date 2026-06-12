---
title: "howto rcp in ubuntu?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by empardopo on 2009-03-26
Hi,

we have two computers with ubuntu.

I need to copy a file from computer1 to computer2 but I'dont want to put root passwords.

I use the next command :"[COLOR="Blue"]rcp -pr filetocopy computer2:/root/[/COLOR]"

Please, What is my problem?

Thanks

---

### Post by cariboo on 2009-03-26
Why not install openssh-server on your computers and use sftp to transfer files back and forth. to use sftp open nuatilus and in the address bar type:

```
sftp://username@computer
```

Jim

---

### Post by albandy on 2009-03-26
use ssh with public and private keys authorization

---

### Post by empardopo on 2009-03-27
I've created a shell with this command: "rcp -pr ..."
With cron I call to my shell.

How can i use ssh? I cannot configure it.

Thanks

Note: I'm sorry for my bad english

---

### Post by albandy on 2009-03-27
> **empardopo said:**
> I've created a shell with this command: "rcp -pr ..."
With cron I call to my shell.

How can i use ssh? I cannot configure it.

Thanks

Note: I'm sorry for my bad english

well first install ssh in both machines
sudo apt-get install ssh

when installed tell us.

---

