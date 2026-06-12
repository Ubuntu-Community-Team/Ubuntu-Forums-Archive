---
title: "Access SSH with public key using Putty"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by televisi on 2009-04-21
[COLOR="Blue"]EDIT: This issue resolved in [http://ubuntuforums.org/showthread.php?p=7125748#post7125748]("http://ubuntuforums.org/showthread.php?p=7125748#post7125748")[/COLOR]
I've setup SSH in my Ubuntu Server edition. It is working properly using normal **PasswordAuthentication yes**, I can connect using Putty from Windows.

Now, is anyone know how to setup the same scenario (connect using Putty) but with Public/Private Key?

I've followed steps from:
- [http://wiki.amahi.org/index.php/Key-based_SSH_Logins_With_Putty]("http://wiki.amahi.org/index.php/Key-based_SSH_Logins_With_Putty")
- [http://www.electrictoolbox.com/putty-rsa-dsa-keys/]("http://www.electrictoolbox.com/putty-rsa-dsa-keys/")

I still cannot get it works, the only screen it gives me is **my Banner**, and then error message **[COLOR="Red"]Disconnected: No supported authentication methods available[/COLOR]**

Below is my **/etc/ssh/sshd_config**:
```

PubKeyAuthentication no

**#Should I Add below option???**
AuthorizedKeysFile .ssh/authorized_keys

Port 22
AllowGroups A
AddressFamily any
AllowTcpForwarding no
Banner /etc/ssh/banner
ChallengeResponseAuthentication no
ciphers aes256-cbc
ClientAliveCountMax 2
ClientAliveInterval 2
Compression delayed
GSSAPIAuthentication no
HostbasedAuthentication no
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
IgnoreRhosts yes
IgnoreUserKnownHosts yes
KeyRegenerationInterval 3600
LoginGraceTime 20
LogLevel VERBOSE
MaxAuthTries 3
PasswordAuthentication no
PermitEmptyPasswords no
PermitRootLogin no
PrintMotd yes
Protocol 2
RhostsRSAAuthentication no
RSAAuthentication yes
ServerKeyBits 1024
StrictModes yes
SyslogFacility AUTH
UsePrivilegeSeparation yes
TCPKeepAlive yes
X11Forwarding no
MaxStartups 3:50:10

**#if user is A1, then use different banner**
Match User A1
AllowTcpForwarding yes
Banner /etc/ssh/A1-banner
Match
```

Steps I've taken:
- Generate key using **Putty Key Generator** software in client (Windows)
- Populate necessary **Comment **& **Key Passphrase** in that software
- Save private key(*id_rsa.ppk*) & public key (*id_rsa.pub*) in Desktop
- copy public key (*id_rsa.pub*) to SSH server
- **cat public key (*id_rsa.pub*) >> ~/.ssh/authorized_keys**
- restart server => **sudo /etc/ssh/ssh restart**

Should I copy *id_rsa.pub* to **~/.ssh/** folder too? 
Or by having **~/.ssh/authorized_keys** is enough?
Should I create **~/.ssh/authorized_keys2** instead of **~/.ssh/authorized_keys**?

Thanks heaps!!!

---

### Post by yeats on 2009-04-22
Okay - try this on your Ubuntu box:

```
cd ~/.ssh
mv authorized_keys authorized_keys2
```

Then try to login from PuTTY.

---

### Post by bodhi.zazen on 2009-04-22
You need to import your ssh key and save it as a putty key.

Then change > AuthorizedKeysFile .ssh/authorized_keys

to

```
AuthorizedKeysFile     %h/.ssh/authorized_keys
```

restart your ssh server.

I am not familiar with your Match User option at the bottom, it may nee dto be MatchUser (without a space), not sure.

---

### Post by televisi on 2009-04-22
Hi,
I've renamed my authorized_keys to authorized_keys2, still not allowing me login with public key
> cd ~/.ssh
mv authorized_keys authorized_keys2

And bodhi, what do you mean by > You need to import your ssh key and save it as a putty key.
As I've created the key from Putty Keygen software and also, I've imported my public key to ssh server using cat command below:

Steps I've taken:
- Generate key using Putty Key Generator software in client (Windows)
- Populate necessary Comment & Key Passphrase in that software
- Save private key(id_rsa.ppk) & public key (id_rsa.pub) in Desktop
- copy public key (id_rsa.pub) to SSH server
**- cat public key (id_rsa.pub) >> ~/.ssh/authorized_keys2**
- restart server => sudo /etc/ssh/ssh restart

I think this nothing to do with **Match User**, as this working find without the "public key method" ==> SSH show different welcome page if the person who logins are different

---

### Post by televisi on 2009-04-23
To summarize, this is what I've done so far:
- renamed file ~/.ssh/authorized_keys to **~/.ssh/authorized_keys2**
- changed **/etc/ssh/sshd_config**
From:
```
AuthorizedKeysFile .ssh/authorized_keys2
```
to:
```
AuthorizedKeysFile %h/.ssh/authorized_keys2
```

And field populated in Putty:
- Host Name and Port
- SSH => Auth => Private Key file for Authentication (which is referring to file **id_rsa.ppk** in Windows Desktop)

File permission:
```

[A1@SERVER:~] l .ssh/
drwx------ 2 A1   A1   4096 Apr 22 07:10 .
drwxr-xr-x 3 A1   A1   4096 Apr 21 01:42 ..
-rw------- 1 root root  226 Apr 22 06:46 authorized_keys2
-rw-r--r-- 1 A1   A1      0 Apr 22 06:35 known_hosts
```

Ps: should I tick/untick **Bypass Authentication Entirely(SSH2-Only)** option?

That's it...:(

---

### Post by yeats on 2009-04-23
```
-rw------- 1 root root  226 Apr 22 06:46 authorized_keys2

```

Doesn't look like your Al user has permission to read or write to the file (which almost certainly the problem).  Do this:

```
sudo chown *username:username* ~/.ssh/authorized_keys2
```

Where *username* is your login username.  Then try to login from PuTTY

---

### Post by apmcd47 on 2009-04-23
I know this is a very stupid question, but did you export your public key as ‘Public key for pasting into authorized_keys file’?

It looks from the putty web site documentation that the default public key format is the SSH.com multiple-line format, rather than the OpenSSH single-line format.

I'm only asking because nobody else has, and somebody has to look stupid :-)

Andrew

---

### Post by televisi on 2009-04-23
YAY!!! finally it works!!!
Apparently [COLOR="Red"][B]the original problem is the user A1 does not have permission to authorized_keys2 file...
[/B][/COLOR]

Now another question, how about the other file such us known_hosts, should it be owned by same user too?

Thanks!
> **chrissharp123 said:**
> ```
-rw------- 1 root root  226 Apr 22 06:46 authorized_keys2

```

Doesn't look like your Al user has permission to read or write to the file (which almost certainly the problem).  Do this:

```
sudo chown *username:username* ~/.ssh/authorized_keys2
```

Where *username* is your login username.  Then try to login from PuTTY

Yup, I didn't forget about this, thanks apmcd47!
> **apmcd47 said:**
> I know this is a very stupid question, but did you export your public key as &#8216;Public key for pasting into authorized_keys file&#8217;?

It looks from the putty web site documentation that the default public key format is the SSH.com multiple-line format, rather than the OpenSSH single-line format.

I'm only asking because nobody else has, and somebody has to look stupid :-)

Andrew

---

### Post by yeats on 2009-04-23
> 
Now another question, how about the other file such us known_hosts, should it be owned by same user too?

Yep - that's right!

---

