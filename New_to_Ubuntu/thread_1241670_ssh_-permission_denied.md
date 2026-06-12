---
title: "ssh -permission denied"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by hellomoto on 2009-08-16
hi guys, i am trying to get a couple of computers on my local wireless network, talking to each other with ssh.

i can connect via ssh from my desktop to my server. 
however i can't connect from my server to my desktop.

I get the following error when trying connecting from server to desktop:
```
 Permission denied (publickey,password). 
```

please let me know if you need me to post my sshd_config file, also please let me know which config file u need to see, (the one on the desktop or the one on the server) 

thankyou!

---

### Post by Bachstelze on 2009-08-16
Do you have the OpenSSH server installed?

```
sudo apt-get install openssh-server
```

---

### Post by Bachstelze on 2009-08-16
Did you edit your config files in any way? What happens *exactly* when you're trying to login?

---

### Post by hellomoto on 2009-08-16
it is installed on both machines

server:
```
 server@server:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded 
```


desktop:
```
 openssh-server is already the newest version 
```

---

### Post by hellomoto on 2009-08-16
i haven't edited the config files at all.

I can ssh into the server from the desktop.  But when I try it the other way (from server to desktop) I get the following error:


```
server@server:~$ ssh mark-desktop@192.168.1.3
mark-desktop@192.168.1.3's password: 
Permission denied, please try again.
mark-desktop@192.168.1.3's password: 

```

---

### Post by mhgsys on 2009-08-16
Make sure your firewall (in case you have a firewall) isn't refusing the connection.

If so; Assign permission.

edit;  you should login with ssh yourusername@192.168.1.3

---

### Post by wojox on 2009-08-16
Do you login with your user name from current machine:
```
ssh wojox@192.168.1.104
```

---

### Post by hellomoto on 2009-08-16
i have no firewall on the machines

I tried login in from my desktop to itself using ssh and this is what happened:

```


mark@mark-desktop:~$ ssh mark-desktop@192.168.1.3
Warning: Permanently added '192.168.1.3' (RSA) to the list of known hosts.
mark-desktop@192.168.1.3's password: 
Permission denied, please try again.


```

---

### Post by hellomoto on 2009-08-16
oh dear... iv'e just realised what i have done.

my user name for my desktop is mark not "mark-desktop" 

i just put in from my server mark@ ip address and it worked

i've been trying for 3 days... im such an idot.. thanks for your help guys!

---

### Post by berthiggins on 2009-08-16
Maybe a stupid question but are you using only certificates and do you have the servers public key in the other machines .ssh/authorized_keys file?

Edit was posting as you posted your soultion!

---

### Post by mhgsys on 2009-08-16
> **hellomoto said:**
> oh dear... iv'e just realised what i have done.

my user name for my desktop is mark not "mark-desktop" 

i just put in from my server mark@ ip address and it worked

i've been trying for 3 days... im such an idot.. thanks for your help guys!

> 
mhgsys.

Make sure your firewall (in case you have a firewall) isn't refusing the connection.

If so; Assign permission.

edit; you should login with ssh yourusername@192.168.1.3 


> WOJOX> Do you login with your user name from current machine:
Code:

```
ssh wojox@192.168.1.104
```


Good you got it working my friend, :P
your not an idiot. lol

We're all here to learn from each other

---

