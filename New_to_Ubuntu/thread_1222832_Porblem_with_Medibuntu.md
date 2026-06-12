---
title: "Porblem with Medibuntu"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by maqtanim on 2009-07-25
I've added medibuntu to my repositories and also added the key. Then when I updated my Ubuntu 9.04 it shows the following message:

[INDENT]*W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>*

*W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/Release](http://packages.medibuntu.org/dists/jaunty/Release) *

[/INDENT]What should I do now? Can any please help me??

---

### Post by Paddy Landau on 2009-07-25
Go to a terminal and enter the following comands:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
sudo apt-get update
```You'll notice that 0C5A2783 is the last eight characters of the missing key in your post.

Let us know if you hit a problem.

---

### Post by synapsys on 2009-07-25
> To enable the Medibuntu repository, please do the following:
 Import the repository:
 ```
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
```
 Import the gpg-key and update your package-list:
 ```
sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
```
 Then run
 ```
sudo update-apt-xapian-index
```
 to make Synaptic display packages from third-party repositories.  
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04-p2](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04-p2)

---

### Post by Paddy Landau on 2009-07-25
@synapsys: Yes, that's a better way. Thanks.

---

### Post by maqtanim on 2009-07-25
Thanks every one it really worked for me!! :D

---

