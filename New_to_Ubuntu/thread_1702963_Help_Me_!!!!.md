---
title: "Help Me !!!!"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by aspiannur41 on 2011-03-08
If I get update my Ubuntu,I always get this
> 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E24BF68FCE0C058
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AA2BB78B7AE26941
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 41FDF8A2B455BEF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 15A8576D6E46FCAD
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D8D75E403EBCE749
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7816E908AA71CF6C

Please help me !!!
I can't update my Ubuntu perfectly,if always get those statements,Thank You!

---

### Post by aspiannur41 on 2011-03-08
If I Update my Ubuntu,I always get notification like this
> 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E24BF68FCE0C058
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AA2BB78B7AE26941
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 41FDF8A2B455BEF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2836CB0A8AC93F7A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 15A8576D6E46FCAD
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D8D75E403EBCE749
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7816E908AA71CF6C

I need your help,cause I can't solve this problem,so I can't update my Ubuntu perfectly.

---

### Post by overdrank on 2011-03-08
Hi and welcome, please do not create multiple threads on the same issue. Threads merged :)

---

### Post by oldos2er on 2011-03-08
Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
``` and replace KEYID with the number shown in the error message.

---

### Post by aspiannur41 on 2011-03-09
```
sudo apt-key --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
Thank you but it's not work,I get these attention
> root@elsangkulirangi-laptop:/home/elsangkulirangi# sudo apt-key --keyserver.ubuntu.com --recv-keys 7816E908AA71CF6C
Usage: apt-key [--keyring file] [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key export <keyid>      - output the key <keyid>
  apt-key exportall           - output all trusted keys
  apt-key update              - update keys using the keyring package
  apt-key net-update          - update keys using the network
  apt-key list                - list keys
  apt-key finger              - list fingerprints
  apt-key adv                 - pass advanced options to gpg (download key)

If no specific keyring file is given the command applies to all keyring files.

Please can you help me ???

---

### Post by twinscythe12332 on 2011-03-09
you missed the --keyserver bit. the quote you gave goes straight into --keyserver.ubuntu.com

---

### Post by aspiannur41 on 2011-03-09
> root@elsangkulirangi-laptop:/home/elsangkulirangi# sudo apt-key --keyserver keyserver.ubuntu.com --recv-keys 7816E908AA71CF6C
Usage: apt-key [--keyring file] [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key export <keyid>      - output the key <keyid>
  apt-key exportall           - output all trusted keys
  apt-key update              - update keys using the keyring package
  apt-key net-update          - update keys using the network
  apt-key list                - list keys
  apt-key finger              - list fingerprints
  apt-key adv                 - pass advanced options to gpg (download key)

If no specific keyring file is given the command applies to all keyring files.

It's still not work.

---

### Post by wilee-nilee on 2011-03-09
Try this .
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

---

### Post by oldos2er on 2011-03-09
> **aspiannur41 said:**
> ```
sudo apt-key --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
Thank you but it's not work,I get these attention

Please can you help me ???

My apologies, I left out "adv" in the command I gave you. I've fixed it. Thanks wilee-nilee.

---

### Post by rvchari on 2011-03-09
> **wilee-nilee said:**
> Try this .
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

sorry for crossing over in this thread. i too had similar key probs and was trying to figure out how to fix it. thanks buddy, ur command line helped me too...
after fixing it, i ran sudo apt-get update to check out. i got the last 2 lines error like this... is it ok if i ignore or is there a fix for it too ?


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by aspiannur41 on 2011-03-09
I did your code,like this :
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E091672E206FF0

```
but, I get notification 
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 61E091672E206FF0
gpg: requesting key 2E206FF0 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

So,what is this mean ? I hope you can help me more.

---

### Post by oldos2er on 2011-03-09
> **aspiannur41 said:**
> gpg: keyserver timed out

It means the keyserver is offline or not responding, which seems to happen frequently. Try it again in a day or two.

---

### Post by ritn on 2011-07-08
Hey guys, I've been having similar problems. I tried

```

sudo aptitude update

```and I also got this back...

> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444 
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21 
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0 
 I tried your suggestion (for example for the last keyid)

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0 
 
```and got back...

[QUOTE]
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0 
 gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com 
 gpgkeys: HTTP fetch error 7: couldn't connect to host 
 gpg: no valid OpenPGP data found. 
 gpg: Total number processed: 0 
 [\QUOTE]

Can you guys tell me what this means, or why this has happened, and if there are any solutions? Thanks!

---

### Post by oldos2er on 2011-07-08
> **ritn said:**
> gpgkeys: HTTP fetch error 7: couldn't connect to host

If your internet connection is up and running, then it's likely a problem with the server.

---

