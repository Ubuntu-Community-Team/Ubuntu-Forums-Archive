---
title: "help with remote access using sshd"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by shutupchuck on 2005-09-11
I have two desktop computers, one running ubuntu 5.04 and one running WinXP. I would like to be able to remote access my linux bux from my XP box so I tried installing sshd on my linux box. At first I used the tar.gz file from ssh.com and did a make command and a configure command and a make install command but these didn't seems to work and I'm not well-versed enough in linux to be able to correct my mistakes so I just left everything the way it was after the failed install. Then I read on the ubuntu wiki al i had to do was run sudo apt-get install openssh-server so i did and then I used the install updates application to install them. So I thought. I can't figure out how to check if the sshd is running or not (which im pretty sure it isnt because I can't ssh into it) and I can't figure out if it was installed properly or if my old install messed everything up. Please help.

---

### Post by nemin on 2005-09-11
[QUOTE=shutupchuck]I have two desktop computers, one running ubuntu 5.04 and one running WinXP. I would like to be able to remote access my linux bux from my XP box so I tried installing sshd on my linux box. At first I used the tar.gz file from ssh.com and did a make command and a configure command and a make install command but these didn't seems to work and I'm not well-versed enough in linux to be able to correct my mistakes so I just left everything the way it was after the failed install. Then I read on the ubuntu wiki al i had to do was run sudo apt-get install openssh-server so i did and then I used the install updates application to install them. So I thought. I can't figure out how to check if the sshd is running or not (which im pretty sure it isnt because I can't ssh into it) and I can't figure out if it was installed properly or if my old install messed everything up. Please help.[/QUOTE]I believe this should be enough at this point:
```
sudo /etc/init.d/sshd start
```

---

### Post by heimo on 2005-09-11
If sshd is running,
```
ps ax | grep sshd | grep -v grep
``` 
should return one line with sshd and its process number.

```
netstat -n | grep 22
``` 
should show you that it's listening on port 22

Running:
 ```
telnet localhost 22
``` 
on localhost (the computer ssh server is running on) should show you something lkie this:
 > SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu1

---

### Post by shutupchuck on 2005-09-11
[QUOTE=nemin]I believe this should be enough at this point:
```
sudo /etc/init.d/sshd start
```[/QUOTE]
 it says there's so such command, i don't think i fully installed it

---

### Post by heimo on 2005-09-11
It's without d
 ```
sudo /etc/init.d/ssh start

```

---

### Post by shutupchuck on 2005-09-11
[QUOTE=heimo]If sshd is running,
```
ps ax | grep sshd | grep -v grep
``` 
should return one line with sshd and its process number.

```
netstat -n | grep 22
``` 
should show you that it's listening on port 22

Running:
 ```
telnet localhost 22
``` 
on localhost (the computer ssh server is running on) should show you something lkie this:[/QUOTE]
 sshd is not running.

when i run netstat -n | grep 22
it comes back 
unix  3      [ ]         STREAM     CONNECTED     10622    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10522
unix  3      [ ]         STREAM     CONNECTED     10322    /tmp/orbit-chuck/linc-1931-0-5c8c7106aa7e4

and when i run telnet localhost 22
it tells me i cannot connect to the remote host

---

### Post by shutupchuck on 2005-09-11
[QUOTE=heimo]It's without d
 ```
sudo /etc/init.d/ssh start

```[/QUOTE]
 that doesn't work either. :(

---

### Post by heimo on 2005-09-11
Yeah, it's definitely not running.
 ```

sudo apt-get install ssh
sudo /etc/init.d/ssh start

```

---

### Post by shutupchuck on 2005-09-11
it said it couldn't load the local keys

---

### Post by heimo on 2005-09-11
Hmm... Anyway you could clean up the failed, earlier install?

I'd probably just try to
```

sudo apt-get --purge remove openssh-server
sudo apt-get install openssh-server
``` 

(not able to post for next ~10-12 hours)

---

### Post by shutupchuck on 2005-09-11
well it seemed like the purge worked but when i tried to do the [sudo apt-get install openssh-server] it said 
E: Sub-process /usr/bin/dpkg returned an error code (1)
It looks like it's having trouble running the ssh-keygen command so I tried to run [ssh-keygen -b 1024 -t RSA -V -p (my password) key1] and it seemed to work but when i ran [sudo apt-get install openssh-server] again it came back with the same message. 

Here is the entire readout:

chuck@mothership:~$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up openssh-server (3.9p1-1ubuntu2) ...
Creating SSH2 RSA key; this may take some time ...illegal option -- f
Usage: ssh-keygen [options] [key1 key2 ...]

Where `options' are:
 -b nnn         Specify key strength in bits (e.g. 1024)
 -t dsa | rsa   Choose the key type.
 -c comment     Provide the comment.
 -e file        Edit the comment/passphrase of the key.
 -p passphrase  Provide passphrase.
 -P             Assume empty passphrase.
 -?
 -h             Print this help text.
 -q             Suppress the progress indicator.
 -1 file        Convert a SSH 1.x key.
 -i file        Load and display information on `file'.
 -D file        Derive the public key from the private key 'file'.
 -B number      The number base for displaying key information (default 10).
 -V             Print ssh-keygen version number.
 -r file        Stir data from file to random pool.
 -F file        Dump fingerprint of file.


Creating SSH2 DSA key; this may take some time ...illegal option -- f
Usage: ssh-keygen [options] [key1 key2 ...]

Where `options' are:
 -b nnn         Specify key strength in bits (e.g. 1024)
 -t dsa | rsa   Choose the key type.
 -c comment     Provide the comment.
 -e file        Edit the comment/passphrase of the key.
 -p passphrase  Provide passphrase.
 -P             Assume empty passphrase.
 -?
 -h             Print this help text.
 -q             Suppress the progress indicator.
 -1 file        Convert a SSH 1.x key.
 -i file        Load and display information on `file'.
 -D file        Derive the public key from the private key 'file'.
 -B number      The number base for displaying key information (default 10).
 -V             Print ssh-keygen version number.
 -r file        Stir data from file to random pool.
 -F file        Dump fingerprint of file.


 * Restarting OpenBSD Secure Shell server...
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 openssh-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

