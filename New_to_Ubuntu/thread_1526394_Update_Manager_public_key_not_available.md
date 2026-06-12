---
title: "Update Manager: public key not available"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by phubert28 on 2010-07-08
I tried a solution listed in another thread but it made no difference.

How can I tell which packages are causing the problem and how do I correct it??

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release:
The following signatures couldn't be verified because the public key is not available:

NO_PUBKEY D739676F7613768D
NO_PUBKEY 9BDB3D89CE49EC21
NO_PUBKEY A6DCF7707EBC211F

---

### Post by sadaruwan12 on 2010-07-08
Did you add any new repositories to the sources.list ?

Please post your sources.list so we could help you.

---

### Post by Elfy on 2010-07-08
Try this - [http://ubuntuforums.org/showpost.php?p=6626153&postcount=4](http://ubuntuforums.org/showpost.php?p=6626153&postcount=4)

Change the key to suit your needs

---

### Post by jtarin on 2010-07-08
Open Synaptic in the left side at the bottom you will see a button marked "Origin". Click it an it will bring up all your repositories in the above column window. You will see at least one marked "LP-PPA", click it and then you will see the packages available from that repo. Scroll down the list and the packages you have installed from that repo will be marked green in the box.You'll then have to determine by going to [http://ppa.launchpad.net/](http://ppa.launchpad.net/) which is the offender. Hopefully you only have one or two.There could be another method but I dont know.

---

### Post by phubert28 on 2010-07-08
64 bit Ubuntu 10.4

My sources are the following (omitting the [http://)](http://))

archive.canonical.com/ubuntu lucid (Source code)
download.virtualbox.org/virtualbox/debian lucid non-free
ppa.paunchpad.net/directhex/ppa/ubuntu intrepid main
ppa.launchpad.net/nilarimogard/webupd8/ubuntu lucid main
archive.canonical.com/ubuntu lucid partner
ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu lucid main
ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main
dl.google.com/linux/deb/ stable main
ppa.launchpad.net/c-korn/vlc/ubuntu lucid main
ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu lucid main

---

### Post by Linye on 2010-07-08
This worked for me.

[http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html]("http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html")

Read the comments for the correct command.

---

### Post by phubert28 on 2010-07-08
> **forestpiskie said:**
> Try this - [http://ubuntuforums.org/showpost.php?p=6626153&postcount=4](http://ubuntuforums.org/showpost.php?p=6626153&postcount=4)

Change the key to suit your needs

Looks like THIS _worked_ for two of the keys. Got a keyserver error then a HTTP fetch error 7: couldn't connect to host

On this key: 9BDB3D89CE49EC21

Trying again.
Getting timeouts.

---

### Post by phubert28 on 2010-07-08
> **Linye said:**
> This worked for me.

[http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html](http://www.omgubuntu.co.uk/2009/09/automatically-install-missing-ppa-gpg.html)

Read the comments for the correct command.

THIS one WORKED!

Thanks!

---

