---
title: "Medibuntu gpg error"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by cjnkns on 2010-04-08
Last night I installed Medibuntu for Lucid. Everything worked fine and I was able to get the downloads I needed.

This morning I am getting the following error when I try to do an update.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Any idea what's going on here?

Thanks for you help.

---

### Post by Didius Falco on 2010-04-08
a GPG key is a Gnu Privacy Guard key. It allows you to encrypt and sign files that are transfered. In this case, it's to make sure that the files you get from Medibuntu are actually from Medibuntu. Run the following command in a terminal window:

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This command will install the Medibuntu key to your keyring and update your package lists to reflect that. Then you won't get that warning message any more.

Read this for more information:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Regards,

Didius

---

### Post by tom.swartz07 on 2010-04-08
> **cjnkns said:**
> Last night I installed Medibuntu for Lucid. Everything worked fine and I was able to get the downloads I needed.

This morning I am getting the following error when I try to do an update.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Any idea what's going on here?

Thanks for you help.

You could always do what the guy above me said, but generally, a GPG error simply means that the repo (the site you are getting package lists and updates from) has a key that you need to use to encrypt your connection with the server.

99.9% of the time you could fix this error with
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 12345678
```

where 12345678 is the LAST 8 digits in that error message you got

so, for your case, you would run
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```

and youre all set!

---

### Post by cjnkns on 2010-04-08
Thanks very much - that worked perfectly!

Guess I don't understand how it worked yesterday but this morning started complaining..

---

### Post by PhenixRising on 2011-02-22
> **tom.swartz07 said:**
> You could always do what the guy above me said, but generally, a GPG error simply means that the repo (the site you are getting package lists and updates from) has a key that you need to use to encrypt your connection with the server.

99.9% of the time you could fix this error with
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 12345678
```

where 12345678 is the LAST 8 digits in that error message you got

so, for your case, you would run
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```

and youre all set!

I've been having gpg errors with medibuntu too.  I've recently installed lucid onto an old PS3.  I don't know if that is the real problem or not.

W: Failed to fetch [http://packages.medibuntu.org/dists/lucid/Release](http://packages.medibuntu.org/dists/lucid/Release)  Unable to find expected entry  free/binary-powerpc/Packages in Meta-index file (malformed Release file?)

Sorry if its bad form to bump this but this thread has been the most useful.

---

