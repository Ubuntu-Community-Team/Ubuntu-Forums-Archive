---
title: "ssh key questions"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by flylehe on 2010-02-25
Hi,

I have some questions regarding generating keys for ssh access:

(1) Supposed there are two computers running ssh server service and I have generated a pair of key files on computer A and copy the public file to computer B. Is it true that this is only a one-way key: We only gave computer A permission to access computer B, not gave computer B permission to access computer A? If I now want to ssh from computer B to computer A, must I generat another pair of key files on computer B and copy the public file to computer A?

(2) If I would like to connect a single local computer to several remote servers, is it to generate a common pair of key files only once on the local and copy the same public file to the remote servers, or to generate different pair of key files on the local for different remote servers?

(3) If I would like to connect several local computers to a single remote server, when copying the public files from different local computers to the remote server, is it to combine them together into a single authorized_keys file or store them in different authorized_keys files?

(4) If there are several servers shared the same file system by, for example, NFS, how to generate keys and arrange the key files for accessing from one server to the other? Also how to still generate keys and arrange the key files for a local computer to access anyone of the servers?

All the machines above are Linux.Please provide examples and commands in your reply so that I can better understand how to solve the problems.

Thanks and regards!

---

### Post by Kakers on 2010-02-25
This link should help you:
[http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/](http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/)

When creating your ssh key it creates two parts, the public key and the private key. The best way to think of these two is: The public key is the lock and the private key is well... the key.

1) If you wanted A and B to be able to ssh to each other, you could create two sets of keys. However if this is permanent then why not have only the 1 set? the private and public key on both. This will allow both of them to ssh to each other.

2) You can post your public key to however many servers you want. So if you want your key to be able to gain entry to your 10 servers... then you simply have to copy your private key over to all 10.

3) Several computers connecting to the same server it would probably be best to create seperate keys for each computer so you have the ability to revoke access to a single computer, all of the private keys created for these computer can be copied into one authorised keys file.

4) Think this is answered above in the other entries, on that link I provided will go step by step how to generate and organise the keys.



Hope this helps.

---

### Post by Iowan on 2010-02-25
I'm still a bit green with SSH keys.  From what I've read:
1. Correct.
2. Also correct - one private/public key combination - public key on multiple servers.
3. I *think* the keys are appended in a single file
4. I haven't done NFS, so even speculation would be a coin-toss.

---

### Post by flylehe on 2010-02-25
Thanks!

In (2), do I need to specify in the local computer which key is for which server? How to?

in (3), how to do this: "all of the private keys created for these computer can be copied into one authorised keys file"? Examples please?
I also saw that sometimes people use multiple aurthorized-keys files: aurthorized-keys, aurthorized-keys2, aurthorized-keys3 and so on. What is that for?

> **Kakers said:**
> This link should help you:
[http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/](http://www.cyberciti.biz/faq/ssh-password-less-login-with-dsa-publickey-authentication/)

When creating your ssh key it creates two parts, the public key and the private key. The best way to think of these two is: The public key is the lock and the private key is well... the key.

1) If you wanted A and B to be able to ssh to each other, you could create two sets of keys. However if this is permanent then why not have only the 1 set? the private and public key on both. This will allow both of them to ssh to each other.

2) You can post your public key to however many servers you want. So if you want your key to be able to gain entry to your 10 servers... then you simply have to copy your private key over to all 10.

3) Several computers connecting to the same server it would probably be best to create seperate keys for each computer so you have the ability to revoke access to a single computer, all of the private keys created for these computer can be copied into one authorised keys file.

4) Think this is answered above in the other entries, on that link I provided will go step by step how to generate and organise the keys.



Hope this helps.

---

### Post by Iowan on 2010-02-25
Have you seen the SSH pages at [https://help.ubuntu.com/community/SSH]("https://help.ubuntu.com/community/SSH") ?

---

### Post by Kakers on 2010-02-26
sudo <vi or nano> ~/.ssh/authorized_keys

Will be where you edit your key in one file, have never used multiple files for the SSH keys, didn't know you could, so unfortunately I can't help you there. :o

---

