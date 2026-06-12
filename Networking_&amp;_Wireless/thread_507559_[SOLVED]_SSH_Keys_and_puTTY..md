---
title: "[SOLVED] SSH Keys and puTTY."
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-07-23
I am having problems using public/private keys in SSH.

I have created a ppk key in puTTY and have uploaded the public key to the desktopn machine that I ssh into, the key has been added to the authorized_keys2 file.

When using the corresponding private key in puTTY I get the following error when logging in, ```
Server refused our key.
```
Do I need the publc key in a different format I am using openssh-server.

Is there anything else I need to do.

---

### Post by bernied on 2007-07-23
> **ushills said:**
> ... the key has been added to the authorized_keys2 file. ...
Are you sure that's right? What's with the 2?

Check the permissions on the files in ~/.ssh on the server, particularly authorized_keys and the id_rsa (private key) files - the owner of these files should be the user (the user who's home directory it is), and they should be readable only by the owner. Maybe the directory should only be accessible by the owner as well. Mine look like this:
```
bernie@vserver:~/.ssh$ ls -al
total 36
drwx------  2 bernie users 4096 Jul  8 17:30 .
drwxr-xr-x 18 bernie users 4096 Jul 12 17:47 ..
-rwx------  1 bernie users 3860 Jul  8 17:30 authorized_keys
-rw-------  1 bernie users 1675 Jul  8 17:30 id_rsa
-rw-r--r--  1 bernie users  396 Mar 27 19:49 id_rsa.pub
-rw-r--r--  1 bernie users 2652 Jul  8 16:50 known_hosts
```(that authorized_keys file probably doesn't need to be executable)

In my authorized_keys file I always have each public key on one line only. Don't know if that makes a difference.  Each key looks like this:
```
cat authorized_keys
...blahblah...
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAzLydXX4TeO...blahblah...SpdSe8E2gZfv+Ew== bernie@slugger
...blahblah...

```

Another tip - you can keep an ssh session running when you restart the sshd on the server - this way if you've messed things up you still have a connection where you can fix it again. You need to restart the server if you make any changes to sshd_config.

Hope something here can help.

---

### Post by ushills on 2007-07-23
From the guide I read the use of auhorized_keys2 was for protocol 2 connections.

I have now tried it with authorized_keys and authorized_keys2 and both but it still does'nt work.

I have recreated both private & public keys in putty, uploaded by public key to the server and added it to the authorized_keys file but it still will not work.

This is my private key

```
PuTTY-User-Key-File-2: ssh-dss
Encryption: aes256-cbc
Comment: ushills
Public-Lines: 10
AAAAB3NzaC1kc3MAAACBAMBe/C1z/im7cMsTAaO83ljvBN/Tt+YOoWTSj18WMd8I
rePycwA09n4B2X4FbQTCVq+xdh3y4aUsIKySC/xilf0LrEnMjdBKnoO7VuTSM7GR
ulAes/lmxinvu3iA/unTui4UDgeM3401eKlPEJBYkjumKz1N1iGDEgMgEQVA0tRL
K+9h/G4sQvotNOUKiKlEEW+UIjgdvDTKDRkkHHkZvva2/yQHztimB+BsyieQEfYu
Yw7H/W9YQHh3AAq9NgAAAIEAmruYcMzdiJ2FXtOfxrxcVKjAWqB/U+IUj4/0Ew2p
EvBBS8YdF0gh5QSZzDLTmFxn0TDOhtmWglZ7Jk3J9N45avCe6Gxcgy+RC3K2A/KK
wGE7E+Lq80U2InBpJFzugbTA3vQPGbe9LzKwCwr+TNPRufST/+BgW/czWZF+noBp
6UQ=
Private-Lines: 1
Mf/WuB5luK7jjh3zLFi+birQdk383wliVL34u1jOO2I=
Private-MAC: b43b613e957d8cff192e7d17e9925d810cf6fd12

```

and this is my public key

```
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "ushills"
AAAAB3NzaC1kc3MAAACBAMBe/C1z/im7cMsTAaO83ljvBN/Tt+YOoWTSj18WMd8I
rePycwA09n4B2X4FbQTCVq+xdh3y4aUsIKySC/xilf0LrEnMjdBKnoO7VuTSM7GR
ulAes/lmxinvu3iA/unTui4UDgeM3401eKlPEJBYkjumKz1N1iGDEgMgEQVA0tRL
K+9h/G4sQvotNOUKiKlEEW+UIjgdvDTKDRkkHHkZvva2/yQHztimB+BsyieQEfYu
Yw7H/W9YQHh3AAq9NgAAAIEAmruYcMzdiJ2FXtOfxrxcVKjAWqB/U+IUj4/0Ew2p
EvBBS8YdF0gh5QSZzDLTmFxn0TDOhtmWglZ7Jk3J9N45avCe6Gxcgy+RC3K2A/KK
wGE7E+Lq80U2InBpJFzugbTA3vQPGbe9LzKwCwr+TNPRufST/+BgW/czWZF+noBp
6UQ=
---- END SSH2 PUBLIC KEY ----

```

both partially obscured.  I have all of the below in my authorized_keys file on one line

```
ssh-dss AAAAB3NzaC1kc3MAAACBAMBe/C1z/im7cMsTAaO83ljvBN/Tt+YOoWTSj18WMd8IrePycwA09n4B2X4FbQTCVq+xdh3y4aUsIKySC/xilf0LrEnMjdBKnoO7VuTSM7GRulAes/lmxinvu3iA/unTui4UDgeM3401eKlPEJBYkjumKz1N1iGDEgMgEQVA0tRLAAAAFQDLfMoqxRPhQFLnzwLAMl9mQXpsGwAAAIBTK+W9YQHh3AAq9NgAAAIEAmruYcMzdiJ2FXtOfxrxcVKjAWqB/U+IUj4/0Ew2pEvBBS8YdF0gh5QSZzDLTmFxn0TDOhtmWglZ7Jk3J9N45avCe6Gxcgy+RC3K2A/KKwGE7E+Lq80U2InBpJFzugbTA3vQPGbe9LzKwCwr+TNPRufST/+BgW/czWZF+noBp6UQ= ushills
```

and the public key in the .ssh/ folder saved as ushills.pub.

Any ideas?

---

### Post by kevdog on 2007-07-23
Try creating the pub/priv keys on the Ubuntu server, and then try importing the private key into putty on the Windows box.  Putty will complain about that the private key is not in Putty but OpenSSH format, but should do the conversion for you.  Save this file and then use this converted file as your private key with putty.

I believe the file for the public keys is the authorized_keys file.  To verify this, look at your /etc/ssh/sshd_config file.  It will tell you in this file where the authorized keys are supposed to be stored.  Something like this:
```

AuthorizedKeysFile %h/.ssh/authorized_keys
```

---

### Post by ushills on 2007-07-24
Thanks for your help, solved this last night, I needed to un comment the correct the authorized_keys and change usestrict to no.

Now working, thanks guys

---

