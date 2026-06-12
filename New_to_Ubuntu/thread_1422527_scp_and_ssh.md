---
title: "scp and ssh"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-03-05
what i&#7743; i dong wrong? i have moved the public key to both boxes

lance@bermudezl:~/MyDownloads$ scp avast4workstation_1.3.0-2_i386.deb 192.168.2.103:
The authenticity of host '192.168.2.103 (192.168.2.103)' can't be established.
RSA key fingerprint is 5e:0e:26:bc:26:dd:64:a5:ab:ee:56:31:5f:50:70:58.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.2.103' (RSA) to the list of known hosts.
lance@192.168.2.103's password: 
Permission denied, please try again.
lance@192.168.2.103's password: 
Permission denied, please try again.
lance@192.168.2.103's password: 
Permission denied (publickey,password).
lost connection


lance@bermudezl:~/MyDownloads$ ssh -C -X pete@192.168.2.103 
Linux wanda 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

Last login: Fri Mar  5 10:42:35 2010 from 192.168.2.105
pete@wanda:~$ 

i&#7743; also having a similar issue with [http://ubuntuforums.org/showthread.php?p=8920853#post8920853](http://ubuntuforums.org/showthread.php?p=8920853#post8920853) posting.

---

### Post by yeats on 2010-03-05
You have to name the "pete" user and name a target directory in your command:

```
scp avast4workstation_1.3.0-2_i386.deb **pete@**192.168.2.103:**/home/pete**
```

Then it will work.  As you're currently trying it, 192.168.2.103 thinks you're trying to log in as "lance"

---

### Post by falconindy on 2010-03-05
I recommend setting up an ~.ssh/config file so that all this is defined once and forgotten. In this case, You'd create an entry similar to the following:
```
Host 192.168.2.103
  User pete
  ForwardX11 yes
  Compression yes

```
both ssh and scp will honor these settings.

> You have to name the "pete" user and name a target directory in your command:
Without specifying a path, you're defaulted to the login user's home directory. In other words, [email]pete@192.168.2.103:.bashrc[/email] refers to /home/pete/.bashrc on 192.168.2.103.

---

### Post by yeats on 2010-03-05
> Without specifying a path, you're defaulted to the login user's home directory. In other words, [email]pete@192.168.2.103:.bashrc[/email] refers to /home/pete/.bashrc on 192.168.2.103.

Thanks for the tip!  I've always explicitly named directories so this is news :-).

---

