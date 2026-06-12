---
title: "Need repositories - Not sure where to post"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by wootlands on 2006-07-24
I'm not sure as to the best place to post this, but I'm trying to get my wireless NIC to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=185174") but when it asks me to install bcm43xx-fwcutter, I get a [bunch of messages]("http://www.wootlands.com/myk/missingrepos.jpg") telling me "No such file or directory" on a few repositories. I believe I've upgraded to the latest and greatest Ubuntu as of about 5 or 6 weeks ago. Since it's my wireless NIC I'm trying to set up, I decided to post in here. If there's a better place, let me know. I think all I need is the repos' listed but I don't know how to get them downloaded. Using a non-wireless connection is not an option at the moment. Where can I get the repos'?

---

### Post by Fac51 on 2006-07-24
try this link

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

just read through it and when you get to the bottom you'll be able to generate new content for your /etc/apt/sources.list

just copy, paste, save, and apt-get update and you're good to go

---

### Post by wootlands on 2006-07-24
will this require me to download something on the linux side? because i have no internet connection from there at the moment...

---

### Post by Fac51 on 2006-07-24
ok then.... what version of ubuntu are you running?

---

### Post by Fac51 on 2006-07-24
i'll just assume you use 6.06


replace /etc/apt/sources.list with the following

```
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://users.lichtsnel.nl/~seveas dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror.ubuntulinux.nl dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./
```

be sure to run the commands....

```
sudo -i
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -


```replace "KEY" with the gpg key provided in each section

---

### Post by wootlands on 2006-07-25
I think I might have 5.10. I checked the Help option and the manual was for 5.10. Either way, I can't edit sources.list. The owner is "root" and I can't change the permissions.

---

### Post by Fac51 on 2006-07-25
in that case, use the example above, but change all occurrences of "dapper" to "breezy"

---

### Post by wootlands on 2006-07-26
how do i get ubuntu to let me edit the file?

---

### Post by bluenova on 2006-07-26
sudo gedit /etc/apt/sources.list

---

