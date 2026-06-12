---
title: "error when trying apt-get update?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by insanity99 on 2009-01-27
it updates a lot then this shows up:
```

W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035
W: Duplicate sources.list entry http://ppa.launchpad.net intrepid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_spring_ubuntu_dists_intrepid_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by eaidoido on 2009-01-27
getting something similar in 8.04

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7

---

### Post by Elfy on 2009-01-27
Both of you can check for the GPG sig at wherever you have got the ppa from 

insanity99 - your second error Duplicate sources.list - backup and then open the file for editing

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.2701
gksu gedit /etc/apt/sources.list
```

You should find the same line in there twice - delete one of them and save, then run

```
sudo apt-get update
```

---

### Post by sisco311 on 2009-01-27
Open a terminal (Applications -> Accessories -> Terminal)
and:

> **insanity99 said:**
> ...

```
gpg --keyserver keyserver.ubuntu.com --recv 8670a035
```
```
gpg --export --armor 8670a035 | sudo apt-key add -
```


> **eaidoido said:**
> ...

```
gpg --keyserver keyserver.ubuntu.com --recv 6e80c6b7
```
```
gpg --export --armor 6e80c6b7 | sudo apt-key add -
```


Both of you: 
```
sudo apt-get update
```

---

### Post by Elfy on 2009-01-27
aaah is that how you do it sisco311 

FC66403D_8670A035_

learnt a thing then :)

---

### Post by ciscosurfer on 2009-01-27
I thought PPA's couldn't be GPG signed, or at least they couldn't when I last checked. When did this change?

---

### Post by insanity99 on 2009-01-27
thanks guys seems to be resolved.

---

### Post by sisco311 on 2009-01-27
> **forestpixie said:**
> aaah is that how you do it sisco311 

FC66403D_8670A035_

learnt a thing then :)

Yes. I don't know why, but this is a quiet common warning.

I've found the solution here: [http://ubuntuforums.org/showthread.php?p=6616484]("http://ubuntuforums.org/showthread.php?p=6616484") (post #2, thanks to [taavikko]("http://ubuntuforums.org/member.php?u=286985"))

It would be nice to write a little howto for future reference,
but I'm lazy :).

---

### Post by Elfy on 2009-01-27
As it's gone for the moment

:thanks: :)

---

### Post by SinrG202 on 2009-05-24
Solution is good. Worked for me. Ditto on above... Always good to learn something new thats handy like this

---

