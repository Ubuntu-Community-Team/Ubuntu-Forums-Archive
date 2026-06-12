---
title: "How to create local repository for the intranet?"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by a.raja on 2010-06-03
hi,

This is Raja.

I need someone's favour.

How to create a local repository for the intranet so that everyone in the local intranet can install directly from my local repository instead of communicating to the internet?

Can any one help with this regard?

Thanks in advance.

---

### Post by Frogs Hair on 2010-06-03
Do you mean a repository on a  local network ?  Remember there are 32,000 + packages in the repository
 and that increases all the time. First, you would need a lot of storage for all those packages.

---

### Post by bodhi.zazen on 2010-06-03
> **a.raja said:**
> hi,

This is Raja.

I need someone's favour.

How to create a local repository for the intranet so that everyone in the local intranet can install directly from my local repository instead of communicating to the internet?

Can any one help with this regard?

Thanks in advance.

[http://wiki.debian.org/HowToSetupADebianRepository](http://wiki.debian.org/HowToSetupADebianRepository)
		[http://www.debian-administration.org/articles/174](http://www.debian-administration.org/articles/174)

[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)

[http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/](http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/)

[http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/](http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/)

---

### Post by a.raja on 2010-06-03
> **bodhi.zazen said:**
> [http://wiki.debian.org/HowToSetupADebianRepository](http://wiki.debian.org/HowToSetupADebianRepository)
        [http://www.debian-administration.org/articles/174](http://www.debian-administration.org/articles/174)

[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)

[http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/](http://popey.com/blog/2006/10/24/Creating_an_Ubuntu_repository_mirror_with_apt-mirror/)

[http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/](http://keystoneit.wordpress.com/2006/08/25/local-network-ubuntu-repository/)


:P

Hey!  Thank you for your valuable time. Your links are useful for me. I have tried apt-cacher so far. I have a confusion here.  After configuring apt-cacher server, how do my clients access it? according to your 3rd link it says that we need to mention proxy address in apt conf directory. cool....! Now, Do i need to change anything in /etc/apt/sources.list  file. I m bit confused. can you clarify?

Thanks in advance.

---

### Post by a.raja on 2010-06-03
Not complete repository! I just want to create local repository for Ubuntu 9.04. I am used work with RHEL5. It is pretty simple for me to create repository in local in redhat or in fedora. But in ubuntu i m really facing problem. Bcoz in redhat, in DVD itself we find lot of packages. but in ubuntu CD, i found hardly 30 packages. ...please let me know..!how to configure repository for ubuntu 9.04! 

apt-cacher or apt-mirror .........?

---

### Post by bodhi.zazen on 2010-06-04
Perhaps this is what you want :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

There is also an Ubuntu DVD , but I am not sure there are more then language packs on the DVD :

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#dvd)

---

