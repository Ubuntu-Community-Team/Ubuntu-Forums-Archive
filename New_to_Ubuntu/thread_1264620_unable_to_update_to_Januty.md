---
title: "unable to update to Januty"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by listerdl on 2009-09-12
Hi, if I do this:

Systems > Administration > Update Manager (check for updates) this message appears:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BCD80C6A6E3C0CE5

Any ideas?

I am definitely using Intrepid....

Thanks!!

---

### Post by bacardiandwatermelon on 2009-09-12
```
*sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys *BCD80C6A6E3C0CE5
```

I think should do it..

---

### Post by listerdl on 2009-09-12
Great!! That solved that error problem - but I am not given the option to update to Januty - is there a terminal command that I can simply instruct the OS to update itself to the latest?

Thanks v much!

Is this the best way?

sudo aptitude update
sudo aptitude upgrade

---

### Post by JOHNNYG713 on 2009-09-12
Hi check software sources in system > administration > software sources  And make sure you have all the appropriate box's checked , such as updates (at the bottom) "Release upgrades" should read normal releases, Hope this helps !

---

### Post by wojox on 2009-09-12
Run your update manager again and make sure your fully updated. Then the button should show up.

---

