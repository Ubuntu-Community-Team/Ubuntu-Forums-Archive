---
title: "Problems with apt-get"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by LiaGalanodel on 2009-10-26
Hi! 
when I write: sudo apt-get update to update my system. It start getting files, but some files are ignored, I don't know why.

I'm sorry but I new in Linux and I try but I fail.

When I write : 

```
apt-get update
``````
Fetched 570B in 1s (399B/s)                               
W: GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```Here that's whath I have when I do a solution:

```
amelieathanassiadis@SorinLinux:~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpgkeys: key 437D05B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
amelieathanassiadis@SorinLinux:~$ gpg --export --armor 437D05B5 | sudo apt-key add -
[sudo] password for amelieathanassiadis: gpg: WARNING: nothing exported

gpg: no valid OpenPGP data found.

```Thanks,

Best regards.

---

### Post by MelDJ on 2009-10-26
try [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by LiaGalanodel on 2009-10-26
I will try tank you.

---

