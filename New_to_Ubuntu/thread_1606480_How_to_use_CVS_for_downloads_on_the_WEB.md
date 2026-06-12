---
title: "How to use CVS for downloads on the WEB?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by seedpress on 2010-10-26
I can't figure out how to connect to a website to download some folders in a CVS repository. I have installed both Cervisia and tkcvs, but I can't figure out how to actually connect them to an internet based server. Maybe neither application is capable of this task? Years ago, I used TortoiseCVS (a Windows app)to access the same wesite to gets some files for a build. So I'm looking for a similar application that would work in Ubuntu.

Any tutorials would be helpful, too. All I want to do is download files; I'm not creating a CVS reposity, nor modifiying files within one.

---

### Post by bioterror on 2010-10-26
> **seedpress said:**
> I can't figure out how to connect to a website to download some folders in a CVS repository. I have installed both Cervisia and tkcvs, but I can't figure out how to actually connect them to an internet based server. Maybe neither application is capable of this task? Years ago, I used TortoiseCVS (a Windows app)to access the same wesite to gets some files for a build. So I'm looking for a similar application that would work in Ubuntu.

Any tutorials would be helpful, too. All I want to do is download files; I'm not creating a CVS reposity, nor modifiying files within one.

You didnt specify what you want to download, but I've been CVS'n one IRC client and script for it for years.

This is a good example:

```

Downloading EPIC5 with CVS the more traditional way.
Most people know that EPIC is available by way of ftp, but how many know that you can also download EPIC via CVS? Since December 15, 2000, EPIC4 and EPIC5 habe been available for download with anoncvs CVS at the following root:

CVSROOT=:pserver:anoncvs@epicsol.org:/home/cvs/repository
The password is "anoncvs" and the module names are "epic4" and "epic5".
Here is a complete example to download epic5 by way of CVS

bash$ setenv CVSROOT=:pserver:anoncvs@epicsol.org:/home/cvs/repository
bash$ cvs login
(Logging in to anoncvs@epicsol.org)
CVS password: anoncvs
bash$ cvs checkout epic5
<lots of output here>
bash$ cd epic5
bash$ ./configure
<lots of output here>
bash$ make
<lots of output here>
bash$ make install
<lots of output here>

```

And then there's GIT, which is also kinda easy, you just apt-get install git and then you say in terminal "git http://url.to.org/something.git" and it will leech you the sources.

---

