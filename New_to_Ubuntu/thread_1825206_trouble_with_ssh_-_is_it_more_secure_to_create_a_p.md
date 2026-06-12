---
title: "trouble with ssh - is it more secure to create a passphrase for the ssh key?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-14
I created a ssh key with passphrase.

ssh doesnt work when I set the sshd_config file to
PasswordAuthentication no

How come it doesnt work when I do 'PasswordAuthentication no'?
Also, how come it is asking for the user's password, and not the passphrase.


Here are the steps I took...
I created a key.  I also created a passphrase for the key.

I uploaded the key from my computer to the server.
> 
[email]user@puter:~/.ssh[/email]$ ssh-copy-id -i id_rsa [email]mainuser@www.server.com[/email]

[email]mainuser@www.server.com[/email]'s password: 
Now try logging into the machine, with "ssh 'mainuser@www.server.com'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

it worked.  I checked the permissions on the server, they were correct.

chmod go-w ~/
chmod 700 ~/.ssh

$HOME drwxr-xr-x
$HOME/.ssh drwx------

and the files contained in $HOME/.ssh :

authorized_keys and id_rsa -rw-------
known_hosts -rw-r--r--

the user and the group was set to mainuser:mainuser - not root:root by default.
-rw------- 1 mainuser mainuser 1675 Apr 26 12:45 id_rsa
-rw-r--r-- 1 mainuser mainuser 400 Apr 26 12:45 id_rsa.pub



I figured I will take each step one at a time.

So, I changed the port number.  
/etc/init.d/ssh restart

It worked.

Then, I decided to make it secure.
PermitRootLogin no
/etc/init.d/ssh restart

It worked.

Then, I wanted to make PasswordAuthentication to no on sshd_config
PasswordAuthentication no

/etc/init.d/ssh restart

try to login again to the server from the terminal.  It gave me
Permission denied (publickey).

????

How come it doesnt work when I do 'PasswordAuthentication no'?

Also, when I disable the 'PasswordAuthentication no'; how come it is asking for password, and not the passphrase.

I figured by using a passphrase, the ssh is more secure.  Even if they read the password on the connection level, they still need the key on their end.  Right?

Isnt it more secure to create a passphrase for the ssh key?

Thank you.

---

### Post by 007casper on 2011-08-15
bump

---

### Post by androssofer on 2011-08-15
> **007casper said:**
> I created a ssh key with passphrase.

ssh doesnt work when I set the sshd_config file to
PasswordAuthentication no

How come it doesnt work when I do 'PasswordAuthentication no'?
Also, how come it is asking for the user's password, and not the passphrase.


Here are the steps I took...
I created a key.  I also created a passphrase for the key.

I uploaded the key from my computer to the server.

it worked.  I checked the permissions on the server, they were correct.

chmod go-w ~/
chmod 700 ~/.ssh

$HOME drwxr-xr-x
$HOME/.ssh drwx------

and the files contained in $HOME/.ssh :

authorized_keys and id_rsa -rw-------
known_hosts -rw-r--r--

the user and the group was set to mainuser:mainuser - not root:root by default.
-rw------- 1 mainuser mainuser 1675 Apr 26 12:45 id_rsa
-rw-r--r-- 1 mainuser mainuser 400 Apr 26 12:45 id_rsa.pub



I figured I will take each step one at a time.

So, I changed the port number.  
/etc/init.d/ssh restart

It worked.

Then, I decided to make it secure.
PermitRootLogin no
/etc/init.d/ssh restart

It worked.

Then, I wanted to make PasswordAuthentication to no on sshd_config
PasswordAuthentication no

/etc/init.d/ssh restart

try to login again to the server from the terminal.  It gave me
Permission denied (publickey).

????

How come it doesnt work when I do 'PasswordAuthentication no'?

Also, when I disable the 'PasswordAuthentication no'; how come it is asking for password, and not the passphrase.

I figured by using a passphrase, the ssh is more secure.  Even if they read the password on the connection level, they still need the key on their end.  Right?

Isnt it more secure to create a passphrase for the ssh key?

Thank you.

humm... i'd make sure you did the keygen part right...(the awl turn it off and on again trick)

set the passwordAuth to yes.

then delete the key in .ssh/authorized_keys2 on your server

then on your client do:

```
ssh-keygen -t rsa
```

hit enter for file to save, then select your passphrase.

then

```
scp ~/.ssh/id_rsa.pub username@remote.server.com:.ssh/authorized_keys2
```(replacing username and remote.server.com with your details) and it should allow you to ssh on asking for passphrase. then turn off password auth and it shud work.

---

### Post by 007casper on 2011-08-15
you know I had this similar problem before.  I named the key so I can identify it for myself.  However, whenever I name the key. It doesnt work.

previously, I did
> ssh-keygen -t rsa -b 4096 -f keyname

ssh-copy-id -i keyname user@server

it didnt work.

I even deleted the public key on the server.  Then, tried it again. > 
scp ~/.ssh/keyname.pub [email]user@domain.com:/home/user/.ssh/keyname.pub[/email]
ssh [email]user@domain.com[/email] "echo `cat ~/.ssh/keyname.pub` >> ~/.ssh/authorized_keys"

that didnt work either.

so, I deleted that key on the client, and on the server.  Recreate the key without naming it 
> ssh-keygen -t rsa -b 4096

then, it worked.

Since naming the key is giving me issues, and I have several keys for the server.  What is the easiest way to identify the keys?

---

### Post by 007casper on 2011-08-16
Since naming the key is giving me issues, and I have several keys for the server. What is the easiest way to identify the keys?

---

### Post by Bachstelze on 2011-08-16
> **007casper said:**
> Since naming the key is giving me issues, and I have several keys for the server. What is the easiest way to identify the keys?

IdentityFile in .ssh/config.

---

### Post by 007casper on 2011-08-16
> IdentityFile in .ssh/config.

I am sorry I am not clear on that... what do you mean?

in .ssh directory on the client side, I would have id_rsa and id_rsa.pub

Then, I would copy id_rsa.pub to the server.

Lets say I want to have naming conventions.  

Instead of id_rsa, and id_rsa.pub, I would prefer to have something like server1, server1.pub, then server2, server2.pub etc... so the keys can be identified.  I wouldnt want to upload the same public key to all the servers I am managing. How would you go about that?

---

### Post by Seq on 2011-08-16
> **007casper said:**
> I am sorry I am not clear on that... what do you mean?

in .ssh directory on the client side, I would have id_rsa and id_rsa.pub

Then, I would copy id_rsa.pub to the server.

Lets say I want to have naming conventions.  

Instead of id_rsa, and id_rsa.pub, I would prefer to have something like server1, server1.pub, then server2, server2.pub etc... so the keys can be identified.  I wouldnt want to upload the same public key to all the servers I am managing. How would you go about that?

Create a 'config' file in your client-side .ssh directory. In it set:

```
IdentityFile ~/.ssh/your_named_key_file
```

For more information on what you can set, read `man ssh_config`

---

### Post by Seq on 2011-08-16
> **007casper said:**
> Instead of id_rsa, and id_rsa.pub, I would prefer to have something like server1, server1.pub, then server2, server2.pub etc... so the keys can be identified.  I wouldnt want to upload the same public key to all the servers I am managing. How would you go about that?

Also, there isn't a problem sending your public key to multiple servers.

I also use multiple ssh keys, but I have one key pair per client (so my laptop has it's own private, my desktop it's own, etc). My authorized_keys files have all of my public keys in them. If my laptop were to be stolen, I'd just pull that public key, and I still have ssh access from my other host.

In your case, if your client machine were to be stolen, you're invalidating all of your keys anyway. You might as well just use one in that case.

---

