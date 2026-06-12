---
title: "Canceled upgrade half way through and can't install anything now."
date: 2010-11-06
forum: New to Ubuntu
---

### Post by BigSears on 2010-11-06
I was upgrading from 10.04 to 10.10 and decided that I didn't want to finish it, so I canceled it. Now it's not letting me install any of the more common upgrades or open synaptic.

---

### Post by bioterror on 2010-11-06
> **BigSears said:**
> I was upgrading from 10.04 to 10.10 and decided that I didn't want to finish it, so I canceled it. Now it's not letting me install any of the more common upgrades or open synaptic.

What says what? Cannot help if you dont provide us some error messages.

---

### Post by Hippytaff on 2010-11-06
How far through the install did you go? was it a fresh install or upgrade?

---

### Post by BigSears on 2010-11-06
> **bioterror said:**
> What says what? Cannot help if you dont provide us some error messages.


It says nothing. There are no error messages that pop up. I click on synaptic and it doesn't show up. I try to install updates and it just does nothing.

---

### Post by BigSears on 2010-11-06
> **Hippytaff said:**
> How far through the install did you go? was it a fresh install or upgrade?

I don't remember xD it was a while ago and I just now decided to try and see what the problem is.

---

### Post by sikander3786 on 2010-11-06
Try from terminal (Applications > Accessories > Terminal) and post the output of

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by BigSears on 2010-11-06
> **sikander3786 said:**
> Try from terminal (Applications > Accessories > Terminal) and post the output of

```
sudo apt-get update
``````
sudo apt-get upgrade
```

> W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: Failed to fetch [http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
that's what comes up at the end

---

### Post by sikander3786 on 2010-11-06
> **BigSears said:**
> that's what comes up at the end
Ok, but we also need the output of the second command i.e,

```
sudo apt-get upgrade
```

---

### Post by BigSears on 2010-11-06
> **sikander3786 said:**
> Ok, but we also need the output of the second command i.e,

```
sudo apt-get upgrade
```

Oh my bad, I thought you reposted the same code twice. But yeah, that one worked. Then it had me run
```
apt-get -f install
```and now it finally works. Thanks for the help.

---

### Post by Hippytaff on 2010-11-06
Excellent - mark the thread as solved in the forum tools at the top of the page so others can benefit from what you did :-)

---

### Post by BigSears on 2010-11-06
> **Hippytaff said:**
> Excellent - mark the thread as solved in the forum tools at the top of the page so others can benefit from what you did :-)

I was looking for something to do just that. xD

---

