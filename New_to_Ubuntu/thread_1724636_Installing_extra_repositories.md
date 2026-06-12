---
title: "Installing extra repositories"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Onyx1 on 2011-04-08
I am trying to install the extra repositories by running the command sudo gedit /etc/apt/sources.list . I deleted the hash marks in front of the deb commands but when i run sudo apt-get update I get the error message.```

W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://packages.medibuntu.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

---

### Post by Enigmapond on 2011-04-08
What distro are you running?

---

### Post by Onyx1 on 2011-04-08
Oh sorry I'm using ubuntu 10.10

---

### Post by Onyx1 on 2011-04-08
I figured it out you have to install the .gpg key for medibuntu I followed the instructions on [http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by ajgreeny on 2011-04-08
For future reference, next time you can do everything with a single command which you can copy/paste from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

It's the long command in the box in the section "Adding the repository".  Nothing could be simpler!

---

### Post by Blasphemist on 2011-04-08
I know wonder if the question about version was something I should have paid more attention to. I am running natty and I ran the command described and got a couple key errors at the end of the command results. Could anyone tell me if there is something I should be doing now since I ran this in natty?

I've attached the command and its results.

---

### Post by wolfen69 on 2011-04-08
> **Blasphemist said:**
> I know wonder if the question about version was something I should have paid more attention to. I am running natty and I ran the command described and got a couple key errors at the end of the command results. Could anyone tell me if there is something I should be doing now since I ran this in natty?

I've attached the command and its results.

As far as I know,there is no key yet for natty. Wait until the official release.

---

