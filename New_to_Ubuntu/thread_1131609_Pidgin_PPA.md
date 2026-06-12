---
title: "Pidgin PPA?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by CheetahDC on 2009-04-21
The version of Ubuntu I'm using, 8.10, ships with version 2.5.2 of Pidgin.  There's a 2.5.5 version out now.  Their website for downloading for Ubuntu is here: [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)  I copied and pasted the command into terminal, and nothing seems to happen. I get this message in Terminal: 
[COLOR="DarkSlateBlue"]Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: "Launchpad PPA for Pidgin Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1[/COLOR]


 I checked /etc/apt/sources.list.d and nothing is there.  So uh...it doesn't seem to have downloaded.  What am I doing wrong?

---

### Post by Anthon on 2009-04-21
There are two commands on that  page: one to add the public key of the keypair they use to sign their packages (this you installed), the other (the echo ... command) to add the repository to /etc/apt/sources.list.d
You seem not to have executed the second command. I tried it and it works for me, so you might have missed it. On my (8.10) system it echos:
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) main
you could also put that line directly in 
/etc/apt/sources.list.d/pidgin-ppa.list

---

### Post by Anthon on 2009-04-21
Actually you probably want to make that line:
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) intrepid main

---

### Post by theozzlives on 2009-04-21
> **Anthon said:**
> Actually you probably want to make that line:
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) intrepid main

worked for me, but I changed intrepid to jaunty

---

### Post by CheetahDC on 2009-04-21
It's two different commands?  Haha, my bad.  Thanks.

---

### Post by gandaran on 2009-04-21
> **CheetahDC said:**
> It's two different commands?  Haha, my bad.  Thanks.
don't  use the pidgin site guide!!!
use this one [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by CheetahDC on 2009-04-21
Yeah, I noticed, that gave me an error in the update manager I had to fix... ...how do I use this site you just gave me?

---

### Post by chriswyatt on 2009-05-20
Here's what I did:

Add these two lines to your third-party software sources (System, Administration, Software Sources) and replace jaunty with your distro if you need to:

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main

Then open up a terminal:

```
gpg --keyserver keyserver.ubuntu.com --recv 0x7fb8bee0a1f196a8

gpg --export --armor 0x7fb8bee0a1f196a8 | sudo apt-key add -
```

Sorted ):P

---

