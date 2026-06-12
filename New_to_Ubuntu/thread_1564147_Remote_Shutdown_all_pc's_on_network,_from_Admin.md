---
title: "Remote Shutdown all pc's on network, from Admin"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by Linuxson25 on 2010-08-30
Hi

I will be running a network of +- 35 Ubuntu pc's from next year on. I have already started setting up remote desktop viewing utilities, but I now need a way to remotely shut down all the pc's at the same time, with a simple command as Admin. Setting up scripts to execute at a certain time is not gonna help, as the online time wont be the same all the time. I want to avoid having to remotely shut down each and every pc, as this will take quite a lot of time. Any help will be greatly appreciated

Thanx

---

### Post by birumak on 2010-12-09
hey i have the same issue, anyone with a solution? plizz

---

### Post by misterbiskits on 2011-01-07
I would also like to know how to use my ubuntu pc to remotely shut down another ubuntu pc.  So far I've got,

```
$ net rpc shutdown -f -I 192.168.0.103 -U Mike
Enter Mike's password:

Shutdown of remote machine failed

result was: WERR_ACCESS_DENIED
```

---

### Post by nm_geo on 2011-01-07
> **misterbiskits said:**
> I would also like to know how to use my ubuntu pc to remotely shut down another ubuntu pc. So far I've got,
 
```
$ net rpc shutdown -f -I 192.168.0.103 -U Mike
Enter Mike's password:
 
Shutdown of remote machine failed
 
result was: WERR_ACCESS_DENIED
```
 
I would recommend looking into ssh.
 
Here is a link to start with:
[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

---

### Post by psusi on 2011-01-07
Yea, use ssh.

```

ssh host shutdown -r now
```

Should do the trick.  If you want to repeat it for several machines then:

```

for host in host1 host2 host2 ; do ssh $host shutdown -r now ; done

```

---

### Post by nm_geo on 2011-01-07
I believe the option -r is shutdown reboot and that might be okay for some uses.  I generally use 
```
sudo shutdown -h -P now
```or some amount of time instead of now if others need to be notified. Typically not as I am the only user on my laptop.

---

### Post by misterbiskits on 2011-01-07
OK I will figure out this ssh you speak of.
Thanks the link and for the tips, folks.

---

### Post by psusi on 2011-01-07
> **nm_geo said:**
> I believe the option -r is shutdown reboot and that might be okay for some uses.

Heh, right... old habit ;)

---

### Post by misterbiskits on 2011-01-09
I followed this guide, [https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html), but got password errors and was unable to copy my key over from the client to the server.  I don't know what password it is looking for, I have tried every password I use on both computers, including empty (enter key).  The password for Mike on the client is the same as the password for Mike on the server...

```
mike@mike-linux:~$ ssh-copy-id Mike@192.168.0.103
Mike@192.168.0.103's password: 
Permission denied, please try again.
Mike@192.168.0.103's password: 
Permission denied, please try again.
Mike@192.168.0.103's password: 
Permission denied (publickey,password).
mike@mike-linux:~$ 
```

It just won't let me copy the key over.
Anyway, I am sometimes able to ssh into the remote computer, and then perform a shutdown as below, so I think I kind of got it working, but in a roundabout way using a password instead of a key.

```
mike@mike-linux:~$ ssh mike@192.168.0.103
mike@192.168.0.103's password: 
Linux hannah-pc 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Sun Jan  9 15:30:58 2011 from mike-linux.local
mike@hannah-pc:~$ sudo shutdown -h -P now
[sudo] password for mike: 
mike@hannah-pc:~$ 
Broadcast message from mike@hannah-pc
    (/dev/pts/0) at 15:36 ...

The system is going down for power off NOW!
Connection to 192.168.0.103 closed by remote host.
Connection to 192.168.0.103 closed.
mike@mike-linux:~$ 
```

I'd really like to figure out how to copy the key over, as that seems to be a cooler way of doing it, no password required.

---

### Post by psusi on 2011-01-09
It looks like your normal user name is "mike" but you specified "Mike" when trying to copy, which is not the same thing.

---

### Post by misterbiskits on 2011-01-09
all that confusion over a darn capital M!!

```
mike@mike-linux:~$ ssh-copy-id mike@192.168.0.103
mike@192.168.0.103's password: 
Now try logging into the machine, with "ssh 'mike@192.168.0.103'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

```Thanks psusi!!!  I'll be more careful with capitals in the future!

A few more problems with this to work out but I'll explore and post again if I am still stuck.

---

### Post by misterbiskits on 2011-01-09
For anyone else who might be reading this, the server failed to authenticate using the key, and prompted me for a password.  By typing 

```
ssh-add
```

Into a terminal on the client machine I am now able to log in without password.  Huzzah!

---

### Post by psusi on 2011-01-10
> **misterbiskits said:**
> For anyone else who might be reading this, the server failed to authenticate using the key, and prompted me for a password.  By typing 

```
ssh-add
```

Into a terminal on the client machine I am now able to log in without password.  Huzzah!

No, the server did not prompt you for your password on the server; your ssh client prompted you for the password that your private key is encrypted with.  ssh-add also prompts you for that password, decrypts your private key, and then caches it for future ssh invocations to use without having to ask you for the key pass again.

Your private key is encrypted with a password to prevent someone else from being able to use it, should they gain access the key file.  This has nothing to do with the login password.  You can even have a disabled login password on the remote machine and still be able to connect with your key.  This comes in handy since the root account is locked by default, and so has no password, but if you copy your authorized_keys file to root's home directory, then you can ssh in as root instead of having to use sudo and enter your password on the remote machine.

---

### Post by perspectoff on 2011-01-10
Running a big network of computers might have other tasks needed, as well.

LTSP might be in your future, or one of the other network monitors and mangement systems (Nagios, etc.) WebCafe software also has a lot of the same functions.

You might want to check out some recommendations:

Ubuntuguide.org:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#LTSP_.28Thin_client_support.29](http://ubuntuguide.org/wiki/Ubuntu:Maverick#LTSP_.28Thin_client_support.29)

or Kubuntuguide.org:

[http://kubuntuguide.org/Maverick#LTSP_.28Thin_client_support.29](http://kubuntuguide.org/Maverick#LTSP_.28Thin_client_support.29)

---

### Post by misterbiskits on 2011-01-12
> **psusi said:**
> your ssh client prompted you for the password that your private key is encrypted with.  ssh-add also prompts you for that password, decrypts your private key, and then caches it for future ssh invocations to use without having to ask you for the key pass again.

Thanks again, I'm sure you're right.  I wish I had copied the terminal output when I did it, but ssh-add asked me for a password and copied the keys over.  Then when I tried to ssh mike@192.168.0.103 it reported something like "Server admits failure to validate using key, please enter password".
So I googled and found the ssh-add and all is well now.   ssh mike@192.168.0.103 now connects and validates using the key and no pwd is required.

Thanks, perspectoff, I am learning and this ssh stuff was a bit of a sidetrack to the project I am working on.  It'll be required later and when I get back to it I will look into this LTSP.

---

### Post by aphinar on 2012-01-12
Hi,

I am administrating dozens of Windows servers ( 2008 ) and i want to shutdown/restart/start remotely from my Ubuntu 11.10 machine. 

I can shutdown any server i want with:

sudo net rpc -I "IP of remote server" -U administrator@domain%password.

So remote shutdown is OK without needing SSH.

Starting a server is a etherwake/WOL issue, so it is not related to this topic.

However, when i try to restart my remote servers with the same method (like: net rpc shutdown -r "IP of remote server" -U administrator@domain%password), i got the error message:

result was: WERR_ACCESS_DENIED

I have been searching almost a week and tried many solution suggestions, but none worked.

Any help will be appreciated. Thanks in advance.

---

### Post by aphinar on 2012-01-15
Anyway, after 10 days effort, i could not achieve to do remote reboot.

Instead of that, i started to develop a complete admin tool (hardware diagnostics, remote shutdown/restart/start/logoff, change domain/hostname, bulk copy, bulk install, TCP/UDP port scan etc.).

After i finished, i will share with the community.

---

### Post by androssofer on 2012-01-15
> **misterbiskits said:**
> Thanks again, I'm sure you're right.  I wish I had copied the terminal output when I did it, but ssh-add asked me for a password and copied the keys over.  Then when I tried to ssh mike@192.168.0.103 it reported something like "Server admits failure to validate using key, please enter password".
So I googled and found the ssh-add and all is well now.   ssh mike@192.168.0.103 now connects and validates using the key and no pwd is required.

Thanks, perspectoff, I am learning and this ssh stuff was a bit of a sidetrack to the project I am working on.  It'll be required later and when I get back to it I will look into this LTSP.

not sure if your still wanting this info.. but is good incase others are reading... 

[http://www.petefreitag.com/item/532.cfm](http://www.petefreitag.com/item/532.cfm)

that is a great guide to public key ssh encription. 

what i would do is set up the ssh server on each machine you need to shutdown. and have it with public key encription that doesnt require passwords. ie: the keys themselves dont have associated passwords.

then make a script that goes through each ip and sends a shutdown command. eg:

```

#!/bin/bash

ssh adminUsername@ipOfComputer 'shutdown -h now'

ssh adminUsername@ipOfNextComputer 'shutdown -h now'

ssh adminUsername@ipOfAnotherComputer 'shutdown -h now'
```

then just run this script and it will send the shutdown commands for you, securely. 

***note***: this script IS NOT tested, it is an example to show the theory

---

### Post by Old_Grey_Wolf on 2012-01-15
If someone is wanting to send the same command to multiple server at the same time try "clusterssh". It is in the software center.

---

