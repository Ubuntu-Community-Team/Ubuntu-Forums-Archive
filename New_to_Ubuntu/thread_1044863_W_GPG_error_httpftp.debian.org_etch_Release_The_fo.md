---
title: "W: GPG error: http://ftp.debian.org etch Release: The following signatures couldn't"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ammk on 2009-01-19
Hi,

sorry if I wrong place to post..

I just add new repository. I follow from this **[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)**

The problem is, when I go to Software System>Administration>Software Sources .. then I reload it...

Suddenly, the message like this is appeared: 
*W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277*

I just google it to find the solutions.. I found one... here: [http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1](http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1)

But the problem is still there...

What should I do? 

Is it safe to run this command?: 
[I]gpg --keyserver wwwkeys.eu.pgp.net --recv-keys A70DAF536070D3A1 
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys B5D0C804ADB11277 
gpg --armor --export A70DAF536070D3A1 | apt-key add - 
gpg --armor --export B5D0C804ADB11277 | apt-key add -[/I]

*I get it from [http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1](http://osterman.com/wordpress/2007/09/08/debian-apt-get-update-fails-with-no_pubkey-a70daf536070d3a1)

Thank you..

---

### Post by zvacet on 2009-01-20
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys B5D0C804ADB11277  
gpg --export --armor B5D0C804ADB11277 | sudo apt-key add -
```

But it is not a good practice to have mixed repos.

---

### Post by seshomaru samma on 2009-01-20
the link you posted just gives you an example of a new repository
the example is from Debian etch and not Ubuntu
you are not supposed to add "deb [http://ftp.debian.org](http://ftp.debian.org) etch main"

what repos are you trying to add?

---

### Post by karim.rahim on 2010-06-19
I have the same problem and I managed to fix one issue. However I still get 
W: There is no public key available for the following key IDs:
9AA38DCD55BE302B

I added etch because I use g77.

It may not be good practice to mix repositories, but it is a good practice to not make g77 available in lucid?

---

### Post by Perfect Storm on 2010-06-19
> **karim.rahim said:**
> I have the same problem and I managed to fix one issue. However I still get 
W: There is no public key available for the following key IDs:
9AA38DCD55BE302B

I added etch because I use g77.

It may not be good practice to mix repositories, but it is a good practice to not make g77 available in lucid?

Get it here; [http://packages.ubuntu.com/hardy-updates/g77](http://packages.ubuntu.com/hardy-updates/g77)

---

