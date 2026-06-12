---
title: "an error occurred during signature verification..."
date: 2010-08-11
forum: New to Ubuntu
---

### Post by al.adab on 2010-08-11
on a *sudo apt-get update* I get the following error message: 

[I][I]Fetched 1,501B in 1s (973B/s)
Reading package lists... Done
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
xxxxx@xxxxx:~$ [/I]

I tried a *sudo apt-get upgrade* but it didn't help...can you help?

---

### Post by kingtaurus on 2010-08-11
I'm getting the same error. I think google has updated their signing key, but forgot to put the public key online (i.e. we are still using the old public key).

---

### Post by phillw on 2010-08-11
Hi,

I'm thinking possibly the key-server was overloaded with requests. It's something that happens from time to time. [Key Servers](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Key Servers) has my notes on when this occurs, in your case, you'd be wanting to add **A040830F7FAC5991**

Regards,

Phill.

---

### Post by kingtaurus on 2010-08-11
> **phillw said:**
> Hi,

I'm thinking possibly the key-server was overloaded with requests. It's something that happens from time to time. [Key Servers](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Key Servers) has my notes on when this occurs, in your case, you'd be wanting to add **A040830F7FAC5991**

Regards,

Phill.

Thanks for the information. I'm just curious why it reports BADSIG as the error.

---

### Post by orange-wedge on 2010-08-11
I'm having the same issue when I update my repositories...

I tried running the apt-key command as well, but couldn't resolve the recommended server pgp.mit.edu:

```
root@desktop:~# apt-key adv --keyserver pgp.mit.edu  --recv-keys A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver pgp.mit.edu --recv-keys A040830F7FAC5991
gpg: requesting key 7FAC5991 from hkp server pgp.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'pgp.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@desktop:~#

```

---

### Post by al.adab on 2010-08-11
same here. I tried 
*sudo apt-key adv --keyserver pgp.mit.edu  --recv-keys A040830F7FAC5991* (hope I got it right) but still get exactly the same error message.

---

### Post by kingtaurus on 2010-08-11
It looks like the mit keyserver is being swapped with requests. Try using the ubuntu keyserver instead.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991
```

---

### Post by al.adab on 2010-08-12
Seems to be working now :) thanks everyone for their help!

---

