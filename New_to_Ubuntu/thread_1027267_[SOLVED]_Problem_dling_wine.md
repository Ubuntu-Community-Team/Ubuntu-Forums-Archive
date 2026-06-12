---
title: "[SOLVED] Problem d/ling wine"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by shearer_007 on 2009-01-01
Hi. I've tried both latest version of ubuntu. For both cases, i kept having problem d/ling wine. 

The error i get is this:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by Delever on 2009-01-01
Make sure your wine repository is correct:

Remove your wine repository from System -> Administration -> Software Sources, then follow *Command Line Instructions for Installing Wine* on this page:

[http://winehq.org/download/deb](http://winehq.org/download/deb)

---

### Post by Captain_tux on 2009-01-01
Isn't Wine available in the repos?

---

### Post by Delever on 2009-01-01
> **Captain_tux said:**
> Isn't Wine available in the repos?

Yes, and it is much more stable, but if you want development - latest version, you can use wine repository.

---

### Post by shearer_007 on 2009-01-01
Thanks for the url, actually i know about this link and did my download based on this link previously as well

I just noticed there are several command lines available for ubuntu. Which is the correct one?

1. Adding the WineHQ APT Repository ( i tried this, but some components fail to d/l)


2. Command Line Instructions for Installing Wine (im trying this one now)

---

### Post by Delever on 2009-01-01
> **shearer_007 said:**
> Thanks for the url, actually i know about this link and did my download based on this link previously as well

I just noticed there are several command lines available for ubuntu. Which is the correct one?

1. Adding the WineHQ APT Repository ( i tried this, but some components fail to d/l)

2. Command Line Instructions for Installing Wine (im trying this one now)

Both methods are for same thing, however doing it in command line is easier (and I think less space for mistake).

For 8.10 (from that page), two commands:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
and then
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list

```

After that, you can run update manager in two ways, either running update manager and checking for updates, or using command "sudo apt-get update".

---

