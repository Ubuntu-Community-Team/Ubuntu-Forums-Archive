---
title: "gpg error   no pub key"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by gridd on 2010-11-29
hello am getting this error message whilst trying to update a new install

A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 

and then a number which may be specific to me I dont know. how do I find and make this public key available

Amd 64 maverick 10.10 alternate Acer laptop.

---

### Post by Angelo Maldito on 2010-11-29
Hi, I have just solved the same problem.

Open the terminal and put this command line, but with the key that your system says is missing in the place of this one in red colour, if it is not the same one:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR="Red"]DB141E2302FDF932[/COLOR]
```

For me it worked, it should work for you as well.

Good luck !

---

### Post by gridd on 2010-11-29
> **Angelo Maldito said:**
> Hi, I have just solved the same problem.

Open the terminal and put this command line, but with the key that your system says is missing in the place of this one in red colour, if it is not the same one:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [COLOR="Red"]DB141E2302FDF932[/COLOR]
```

For me it worked, it should work for you as well.

Good luck !
 
Hi thanks very much Angelo that worked a treat.

---

