---
title: "Can't run updates"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by wc4r on 2009-02-08
It has been some time since I've seen the "updates available" icon so I launched Update Manager manually. It tries to download 59 updates and on the last one it come back with this error-

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Any ideas how to clear this?

---

### Post by tom56 on 2009-02-08
The problem is one of your repositories, probably an unofficial one, doesn't have an up to date authorisation key. What repos do you have enabled?

---

### Post by drs305 on 2009-02-08
Launchpad has introduced security keys to access its repositories. You have to import the key. To do this, run the following:
```

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

```

---

### Post by Temposs on 2009-02-08
EDIT: try what drs305 says first

Go to System->Administration->Software Sources

Then click "Third Party Sources"

Uncheck the entry/entries relating to "ppa.launchpad.net"

You shouldn't receive an error after that. Also, that repository will be disabled. If you want to enable it, you need to find the GPG key for that repository and how to apply it on your machine.

---

### Post by linux_tech on 2009-02-08
If there is a missing GPG key, then in the terminal type-
```

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF

gpg --export --armor 60D11217247D1CFF | sudo apt-key add -

```
This should add the key to the list.

---

### Post by wc4r on 2009-02-08
Worked exactly as you all stated. No more errors.
Thanks!!
:p

---

