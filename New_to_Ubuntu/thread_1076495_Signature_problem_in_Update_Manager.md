---
title: "Signature problem in Update Manager"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by the8thstar on 2009-02-21
Hello there, I was running System Update and I ran into this interesting problem :

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

What caused it? Can it be corrected? If so, how?

Thanks a lot for your help.

---

### Post by drs305 on 2009-02-21
Launchpad and others are starting to sign their repositories and you need the key. Here is one way to import it:
```

gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220     
gpg --export --armor 6AF0E1940624A220  | sudo apt-key add -
sudo apt-get update

```

---

### Post by the8thstar on 2009-02-21
Here is what I got :

> the8thstar@the8thstar-laptop:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
[sudo] password for the8thstar: 
gpg: WARNING: unsafe ownership on configuration file `/home/the8thstar/.gnupg/gpg.conf'
gpg: keyring `/home/the8thstar/.gnupg/secring.gpg' created
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
the8thstar@the8thstar-laptop:~$ gpg --export --armor 6AF0E1940624A220  | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

---

### Post by drs305 on 2009-02-21
The permissions on your gpg.conf file may be too open. Run this to set the permissions on the file only for yourself:
```
chmod 600 $HOME/.gnupg/gpg.conf
```

---

### Post by the8thstar on 2009-02-21
Hmm, no, nothing changed. **gpg.conf** is empty by the way, apart from this:

> # FILE CREATED BY SEAHORSE

---

### Post by drs305 on 2009-02-21
Perhaps you will have better luck importing the key in the traditional manner. Here is the link to the Launchpad page on how to add the keys:
[https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys]("https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys")

Read the section: Installing Software from a PPA

---

### Post by the8thstar on 2009-02-21
I don't think I'll try that simply because I don't even know what app is causing the message to show up in the first place.

---

### Post by forger on 2009-02-22
Use this:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

By the way, you **SHOULD NOT** use sudo and gpg as you did, that's why you got that error and that warning.

---

### Post by the8thstar on 2009-02-24
Excellent how-to. It saved my "lists"! Thanks a lot.

---

### Post by ukblacknight on 2009-02-28
Oops I posted in the wrong topic, was meant to say thanks in a different thread!  The link forger supplied fixed my authentication errors anyways, thanks :).

---

