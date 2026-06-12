---
title: "problem on updating"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by munna.cheyur on 2011-01-14
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8"

At each time when i'm trying to update this error report is coming. How to add this pub key help please.

---

### Post by plucky on 2011-01-14
> **munna.cheyur said:**
> "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8"

At each time when i'm trying to update this error report is coming. How to add this pub key help please.

Open a terminal and ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8771ADB0816950D8
``` should add the correct key.

Although the link you provided didn't actually point to a PPA,but pointed to the PPA index.

Good Luck

---

### Post by ztirffritz on 2011-09-23
I'm having the same problem.  I tried using the code that you suggested and it didn't find anything.  My error is:
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21

```

The results of running the code are:
> Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


---

### Post by plucky on 2011-09-23
> gpgkeys: HTTP fetch error 7: couldn't connect to host

Do you have an Internet connection?

Are you behind a proxy?

Have you got a Firewall?

From [Here](http://www.serenux.com/2009/07/howto-make-use-of-ubuntu-ppa-repositories/)

> It is because your firewall is blocking access to the Keyserver. Keyservers use port 11371 to communicate, not port 80 which is the normal HTTP port, so open 11371 as an outbound port on your firewall and re-run the command and it will work fine.

Good Luck

---

### Post by ztirffritz on 2011-09-23
Is there anyway to correct this without using that port?  I am behind a firewall, but I can't change that.

---

