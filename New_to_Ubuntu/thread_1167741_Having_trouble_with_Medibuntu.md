---
title: "Having trouble with Medibuntu"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-05-23
I have installed medibuntu on my V9.04 I even have a checked indicater in System> administration> software sources.  But when I try to run my update manager (nothing happens the first time, finds no updates-so I hit 'check') I get the following error message

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Can anyone help me to resolve this issue

Thanks

---

### Post by Tibuda on 2009-05-23
install the [medibuntu-keyring]("apt:medibuntu-keyring") package

---

### Post by Theo148 on 2009-05-23
The problem is that you don't have the PGP keys needed to authenticate packages from the Medibuntu repos. You should be able to resolve this by installing the package medibuntu-keyring (if it's already installed, you'll need to reinstall it).

```
sudo apt-get install --reinstall medibuntu-keyring
```

It'll probably complain that the package couldn't be authenticated, but that's only to be expected since the package itself holds the keys. :)

Edit: Got beaten to it :lolflag:

---

### Post by Norman Thom on 2009-05-23
Thanks Theo:

The error message no longer appears in the Update manager so I assume everything is OK

Thanks again

---

### Post by Norman Thom on 2009-05-23
Thanks daniel:

The error message no longer appears in the Update manager so I assume everything is OK

Thanks again

---

### Post by snoggeruk on 2009-05-25
I had this problem and I followed the above mentioned advice, which resolved part of the problem, in that I no longer get the public key error; however, I still get an error that I suspect relates to the fact that I use the 64bit version.  I now continue to get the following message:

[I]Failed to fetch [http://packages.medibuntu.org/jaunty/dists/free/non-free/binary-amd64/Packages](http://packages.medibuntu.org/jaunty/dists/free/non-free/binary-amd64/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/I]

Any advice appreciated, as my system has not updated for 10 days.
Thanks in advance.

---

### Post by Theo148 on 2009-05-25
Well for some reason one of the index files apt is looking for isn't there. It might just be a problem on Medibuntu's end, or a problem in your sources file (but unless you edited your sources file manually, that probably isn't the case).

You should be able to check for and apply updates just fine though - it's just stuff under that particular index that apt won't be able to find.

---

