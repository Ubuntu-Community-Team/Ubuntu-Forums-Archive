---
title: "untrusted packages"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2010-04-11
Recently I allowed Ubuntu to upgrade Openoffice and in doing so I ended up corrupting it!
After trying many things to get it back I managed only in removing it completely from my computer thinking that this step will allow me to install it from scratch and solve my problems.

I find that I cannot install Openoffice now. I get this 'untrused packages warning' (screenshot attached) and can get no further.
Is this because I do not have some repositories installed in my system or is there some other step I need to take?

Can someone help me please

Ubuntu 9.1
Linux kernel 2.6.31-20
GNOME 2.28.1
Openoffice upgrade from 3.1 to 3.2 (I think)

---

### Post by Flimm on 2010-04-14
Open the Update Manager (System, Administration) and click Check. If there are any errors, copy and paste them here.

---

### Post by steinzeitmensch on 2010-04-14
Yes there was an error.

[HTML]W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF[/HTML]

---

### Post by philinux on 2010-04-14
> **steinzeitmensch said:**
> Yes there was an error.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY **[COLOR="Red"]60D11217247D1CFF[/COLOR]**

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **[COLOR="Red"]KEYID[/COLOR]**

---

### Post by steinzeitmensch on 2010-04-14
Hi and thanks (I think)
Put this code into the terminal and this is what got spat out:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys KEYID
gpg: "KEYID" not a key ID: skipping

```

What does this mean?
Has something been fixed or changed
Still cannot install OO via the Ubuntu Sotware Center

---

### Post by steinzeitmensch on 2010-04-14
oops I think I acted before thinking.
Check this out for the output from the terminal now:
```
alex@alex-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 60D11217247D1CFF
gpg: requesting key 247D1CFF from hkp server keyserver.ubuntu.com
gpg: key 247D1CFF: "Launchpad PPA for OpenOffice.org Scribblers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
alex@alex-laptop:~$ 

```


Still no cigar with the install though

---

