---
title: "GPG error?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-26
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8AD328D8A58BCAE3
W: You may want to run apt-get update to correct these problems

```

I get the above error when updating after adding the SMPlayer repo:confused:

---

### Post by gandaran on 2009-04-26
> **kamitsukai said:**
> ```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8AD328D8A58BCAE3
W: You may want to run apt-get update to correct these problems

```

I get the above error when updating after adding the SMPlayer repo:confused:
run sudo apt-get update in terminal and ignore the message or get the key and install it from the same site you used to add the repository.

---

### Post by unutbu on 2009-04-26
Open a terminal and type
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8AD328D8A58BCAE3
```
See [https://help.launchpad.net/Packaging/PPA#Adding the keys in the terminal](https://help.launchpad.net/Packaging/PPA#Adding the keys in the terminal)

---

### Post by Sealbhach on 2009-04-26
Ok, do this in the terminal 
```

gpg --keyserver keyserver.ubuntu.com --recv 8AD328D8A58BCAE3
``````
gpg --export --armor 8AD328D8A58BCAE3 | sudo apt-key add -             
```That should add the key you are missing.  That happened to me today as well, although I don't think it was the same key.


.

---

### Post by kamitsukai on 2009-04-26
Thansk everyone!

---

### Post by juanbretti on 2009-04-28
> **unutbu said:**
> Open a terminal and type
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8AD328D8A58BCAE3
```
See [https://help.launchpad.net/Packaging/PPA#Adding the keys in the terminal](https://help.launchpad.net/Packaging/PPA#Adding the keys in the terminal)
Cool, thanks!

---

