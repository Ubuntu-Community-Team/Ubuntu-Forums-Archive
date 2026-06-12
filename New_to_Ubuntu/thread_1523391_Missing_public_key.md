---
title: "Missing public key"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-07-03
For the last week or so I've been getting the following error message whenever I try and get updates.  Message occurs both in Update Manager and in Terminal.
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89

Should I be concerned?

---

### Post by warfacegod on 2010-07-03
It depends on what the key is for. Have you tried to install any apps from a PPA?

---

### Post by danielgrosvenor on 2010-07-03
> **warfacegod said:**
> It depends on what the key is for. Have you tried to install any apps from a PPA?

I'm not 100% sure what is defined as a PPA in this case. :S  But I've not installed anything overly fancy - just Adobe AIR, TweetDeck, and a few things like Ubuntu Tweak.

---

### Post by warfacegod on 2010-07-03
Go to: System> Admin.> Software Sources

Compare the "Other Software" tab and the "Authentication" tab to see which key, if any, is missing.

---

### Post by warfacegod on 2010-07-03
A very basic PPA explanation and instructions on adding them if a package you install doesn't do it automatically: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20PPAs)

---

### Post by danielgrosvenor on 2010-07-04
Thanks.

I'll be honest... I'm not really too sure what I'm looking at  here. :S  I've attached a screenshot in case anyone can help.

---

### Post by warfacegod on 2010-07-04
I don't see a key for the launchpad.compiz... PPA (could be wrong). Try unchecking it in the Other Software tab. You'll need to Reload afterward. Then do an Update.

---

### Post by sandyd on 2010-07-04
> **danielgrosvenor said:**
> For the last week or so I've been getting the following error message whenever I try and get updates.  Message occurs both in Update Manager and in Terminal.


Should I be concerned?
```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2ED6BB6042C24D89
gpg --export --armor 2ED6BB6042C24D89 | sudo apt-key add -
```
none of my famous typos this time I hope.

---

### Post by danielgrosvenor on 2010-07-12
Just wanted to say thanks for all the help.  That last command sorted it. :)

---

