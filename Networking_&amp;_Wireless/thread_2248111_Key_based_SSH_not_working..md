---
title: "Key based SSH not working."
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by kaspar_silas on 2014-10-12
I'm having a bit of an issue with key based ssh. Normal (password) ssh is fine but every time I switch to keys it fails. I assume its something obvious and daft I'm forgetting. Could someone knowledgeable glance down this and enlighten me.

```


[USERNAME]@[HOSTNAME]:~$ ls .ssh/
known_hosts

[USERNAME]@[HOSTNAME]:~$ ssh-keygen 
Generating public/private rsa key pair.
Enter file in which to save the key (/home/[USERNAME]/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
##NO PASSWORDS ENTERED##
Your identification has been saved in /home/[USERNAME]/.ssh/id_rsa.
Your public key has been saved in /home/[USERNAME]/.ssh/id_rsa.pub.
The key fingerprint is:
fc:82:49:e2:5a:b8:15:97:b3:c1:e2:50:f1:4a:bd:f8 [USERNAME]@[HOSTNAME]
The key's randomart image is:
+--[ RSA 2048]----+

 ...
 
+-----------------+

[USERNAME]@[HOSTNAME]:~$ ssh localhost -i ~/.ssh/id_rsa.pub 
Permission denied (publickey).

[USERNAME]@[HOSTNAME]:~$ sudo nano /etc/ssh/sshd_config
[sudo] password for [USERNAME]: 
##I REENABLED PASSWORDS HERE##

[USERNAME]@[HOSTNAME]:~$ sudo service ssh reload

[USERNAME]@[HOSTNAME]:~$ ssh localhost 
[USERNAME]@localhost's password: 
Last login: Sat Oct 11 06:19:58 2014 from localhost


```

---

### Post by steeldriver on 2014-10-12
The ssh **client** needs the **private** key

```

ssh localhost -i ~/.ssh/id_rsa

```

---

### Post by kaspar_silas on 2014-10-12
Ah cheers, that was a silly mistake all right. But alas its not the problem as both keys give the same response.

---

### Post by steeldriver on 2014-10-12
I'm not sure that it's sufficient to have the id_rsa.pub file in your ~/.ssh directory even if you are just looping back to localhost - afaik you still need to append the key to your ~/.ssh/authorized_keys file - either using ssh-copy-id (as you would to copy the key to a remote host)

```

ssh-copy-id localhost

```

or simply using 'cat'

```

cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

```

If you haven't already done so, make sure that the ~/.ssh directory has permissions drwx------ (octal 700) and the authorized_keys file -rw------- (octal 600)

FWIW it shouldn't be necessary to use the -i option since ~/.ssh/id_rsa is the default ID file location

---

### Post by kaspar_silas on 2014-10-12
Ah cheers thats it. I thought it checked .ssh as well as authorized keys but it makes sense in retrospect given the naming.

Thanks again.

---

