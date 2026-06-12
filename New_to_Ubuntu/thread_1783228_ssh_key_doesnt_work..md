---
title: "ssh key doesnt work."
date: 2011-06-15
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-15
I have trouble with ssh key.

auth.log is stating that authorized_keys arent regular file.

???

I have created the keys on the linux client
ssh-keygen -t rsa -b 4096 -f key_name

transfer the files to the remote box
scp -P xxxx file user@server:/home/user/file

it didnt work.  

on the remote box I chmod ~/.ssh 711, and for authorized_keys 600.  I still had problems.  I chmod ~/.700 ssh, it still didnt work.
 
It is still asking me for a password, instead of the passphrase.  

I figured maybe the problem is due to my encrypted drive.  I have put the keys under /etc/ssh/<username>/authorized_keys so it is described on the help sections, it still didnt work.

I have checked the auth.log file at both times.  It states it is not regular file.

I have also tried ssh-keygen and created 2048 key, instead of 4096 and I still have the same problem.
> 
Jun 14 17:34:10 moie sshd[19766]: User hiya authorized keys /home/hiya/.ssh/authorized_keys is not a regular file
Jun 14 17:34:17 moie sshd[19766]: last message repeated 3 times
Jun 14 17:34:17 moie sshd[19766]: pam_sm_authenticate: Called
Jun 14 17:34:17 moie sshd[19766]: pam_sm_authenticate: username = [hiya]
Jun 14 17:34:17 moie sshd[19770]: Passphrase file wrapped
Jun 14 17:34:18 moie sshd[19770]: Error attempting to add filename encryption key to user session keyring; rc = [1]
Jun 14 17:34:18 moie sshd[19766]: Accepted password for hiya from 192.168.1.3 port 57645 ssh2
Jun 14 17:34:18 moie sshd[19766]: pam_unix(sshd:session): session opened for user hiya by (uid=0)
Jun 14 17:34:22 moie sshd[19844]: Received disconnect from 192.168.1.3: 11: disconnected by user
Jun 14 17:34:22 moie sshd[19766]: pam_unix(sshd:session): session closed for user hiya

Jun 14 17:40:43 moie sshd[20028]: User hiya authorized keys /etc/ssh/hiya/authorized_keys is not a regular file
Jun 14 17:40:50 moie sshd[20028]: last message repeated 3 times
Jun 14 17:40:50 moie sshd[20028]: pam_sm_authenticate: Called
Jun 14 17:40:50 moie sshd[20028]: pam_sm_authenticate: username = [hiya]
Jun 14 17:40:50 moie sshd[20031]: Passphrase file wrapped
Jun 14 17:40:50 moie sshd[20031]: Error attempting to add filename encryption key to user session keyring; rc = [1]
Jun 14 17:40:50 moie sshd[20028]: Accepted password for hiya from 192.168.1.3 port 52599 ssh2
Jun 14 17:40:50 moie sshd[20028]: pam_unix(sshd:session): session opened for user hiya by (uid=0)
Jun 14 17:40:51 moie sshd[20105]: Received disconnect from 192.168.1.3: 11: disconnected by user
Jun 14 17:40:51 moie sshd[20028]: pam_unix(sshd:session): session closed for user hiya

---

### Post by 007casper on 2011-06-15
any ideas???

---

### Post by lkraemer on 2011-06-15
I haven't a clue as to what your server is.....but in FreeNAS I have to
use a DSA Key for ssh.  And it is a Version 2 DSA Key whose default file
names are id_dsa & id_dsa.pub.  Is this what you are using for your Server?

If not what type file is your Server looking for?  RSA or DSA?  Version 1 or Version 2?  

lk

---

### Post by collisionystm on 2011-06-15
Keys should be placed in

/home/user/.ssh/authorized_keys

You need the RSA pub key not the private.

---

### Post by 007casper on 2011-06-15
The server is ubuntu (tomcat version) 10.04 LTS Lucid Lynx.  It has an encrypted hard drive.

I was able to ssh from laptop to the server on LAN.  After I was able to login, I created the keys on the server while connected through the laptop.

Then, I saw the instructions that indicated the keys should be created on the client and copy the pub key to authorized_keys.  So, I deleted the keys I created on the server, and recreated the keys on the laptop(client), and copied to the server.

no passphrase shows up, it goes to default password prompt and I am able to ssh.

However, I cant make it read the keys.

---

### Post by 007casper on 2011-06-15
> If not what type file is your Server looking for? RSA or DSA? Version 1 or Version 2? 

I dont know. How can I find out?  I am using rsa key set up so far.

---

### Post by bodhi.zazen on 2011-06-15
The easiest method , by far, of tranfering the key is with ssh-copy-id

```
ssh-copy-id user@server
```

Once the key works, disable passwords.

---

### Post by 007casper on 2011-06-16
ok.  I am going to try
ssh-copy-id user@server

how do I define the port number?
```
ssh-copy-id user@server:xxx
```

xxx is the port number - would that work? 

and what is the difference between ssh-copy-id user@server and 
ssh-copy-id -i ~/.ssh/key_name.pub user@server

thank you.

---

### Post by yeats on 2011-06-16
> Jun 14 17:34:10 moie sshd[19766]: User hiya authorized keys /home/hiya/.ssh/authorized_keys is not a regular file

On the server, can you please execute the following?:

```
ls -l /home/hiya/.ssh/authorized_keys
file /home/hiya/.ssh/authorized_keys
```

and post the output?

You might also open it in nano or vi just to see what's in there (don't post that here ;-)).

---

### Post by bodhi.zazen on 2011-06-16
> **007casper said:**
> ok.  I am going to try
ssh-copy-id user@server

how do I define the port number?
```
ssh-copy-id user@server:xxx
```xxx is the port number - would that work? 

and what is the difference between ssh-copy-id user@server and 
ssh-copy-id -i ~/.ssh/key_name.pub user@server

thank you.

I did not see a way of assigning a port with ssh-copy-id

Change the port back to port 22, use ssh-copy-id, then once the keys are working you can disable passwords.

You can change the port if you wish, but it does not add much to security. If you are using keys the script kiddies can not access the server on port 22 as you will have disabled passwords and anyone more determined then the script kiddies will find your port easily enough.

---

### Post by 007casper on 2011-06-16
> ls -l /home/hiya/.ssh/authorized_keys
file /home/hiya/.ssh/authorized_keys

as soon as I get the output I will post it.

> Due to this bug, [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=99785](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=99785)

you cannot specify a port other than the standard port 22. You can work around this by issuing the command like this: ssh-copy-id "<username>@<host> -p <port_nr>". If you are using the standard port 22, you can ignore this tip. 

I will revert to port 22, and maybe change it after I transfered the keys.

I had the right permissions on the folder /.ssh and the authorized_keys, but found out that the permissions on .pub file wasnt right.

I am going to set these permissions thoughout the files.

$HOME drwxr-xr-x
$HOME/.ssh drwx------

and the files contained in $HOME/.ssh :

authorized_keys and id_rsa -rw-------
known_hosts -rw-r--r--
-rw------- 1 root root 1675 Apr 26 12:45 id_rsa
-rw-r--r-- 1 root root 400 Apr 26 12:45 id_rsa.pub

can anyone confirm on the permissions?  Because I found contradicting information on permissions through out the net.

I wonder if 'user' and 'group' matters.  I am thinking of setting it to root.

I also have a 64 bit server, and the laptop is 32 bit.  Does that matter?

I will disable the password on sshd_config under /etc/ssh and restart ssh.

Thank you.

---

