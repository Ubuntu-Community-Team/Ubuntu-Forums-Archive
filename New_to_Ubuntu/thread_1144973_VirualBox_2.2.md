---
title: "VirualBox 2.2"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by kemo0o on 2009-05-01
Hello Everybody , 

I 'm trying to install VBox 2.2 on My UBUNTU 8.04 but while installing it after Double-Clicking on .deb the message Appear 

[PHP]Error: Dependency is not satisfiable: libqt4-network[/PHP]

i tried to install it from Terminal - 

```
sudo apt-get install libqt4-network
```

But Useless 

i tried 
```
$ sudo apt-get install -f

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Now am really confused about this . 

Any help from You ?!

---

### Post by Cypher on 2009-05-01
What was the output of "sudo apt-get install libqt4-network"??

---

### Post by y_garti on 2009-05-01
i don't know this problem but i think that libqt4-network already install on your machine
i suggest that you enter to synaptic and see if its already install if it already install and nobody give you a 
beater solution i suggest that you reinstall the package and try install Virtual box again

---

### Post by kemo0o on 2009-05-01
> **Cypher said:**
> What was the output of "sudo apt-get install libqt4-network"??

[COLOR="Red"]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded[/COLOR].

> **y_garti said:**
> i don't know this problem but i think that libqt4-network already install on your machine
i suggest that you enter to synaptic and see if its already install if it already install and nobody give you a 
beater solution i suggest that you reinstall the package and try install Virtual box again

i completely Removed the Package also when try to install it again 
```
$ sudo apt-get install libqt4-network
```

this is the result 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libqt4-network is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqt4-network has no installation candidate
```


???????? Help  :(

---

### Post by amingv on 2009-05-01
Check here:
[http://packages.ubuntu.com/hardy-backports/i386/libqt4-network/download](http://packages.ubuntu.com/hardy-backports/i386/libqt4-network/download)

I'd much rather add the repository entry for VirtualBox though.

---

### Post by kemo0o on 2009-05-01
> **amingv said:**
> Check here:
[http://packages.ubuntu.com/hardy-backports/i386/libqt4-network/download](http://packages.ubuntu.com/hardy-backports/i386/libqt4-network/download)

I'd much rather add the repository entry for VirtualBox though.

I installed it again but VBOX has the same trouble

---

### Post by anewguy on 2009-05-01
Searching the net for this turns up many entries -most say to enable hardy backports in your software sources, then use synaptic to install it.

If you are using apt instead of the gui front end, try:

sudo apt-get build-dep <name of your virtualbox package here>

Dave :)

---

### Post by kemo0o on 2009-05-02
NO WAY ?!!! 

I can'y install it 
the same Error Appear

---

### Post by kemo0o on 2009-05-02
Hello ... Any body wanna help me?? 
Plz i wanna it so much

---

### Post by lkraemer on 2009-05-02
Why don't you try adding the proper line in your /etc/apt/sources.list

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) gutsy non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) dapper non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lenny non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) etch non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) sarge non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xandros4.0-xn non-free

from:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Then use Synaptic to install it.  I've always had good luck doing that.
Also, be sure to install the Guest Additions for Windows, after Windows
is installed.  And make your VDI larger than 10Gig on the initial size.
Windows will eat up around half of that.

lkraemer

---

### Post by kemo0o on 2009-05-02
I added this one to the THIRD PARTY SOFTWARE 

But when i reload it it gives me ERROR 

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/hardy/non-free/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/hardy/non-free/binary-i386/Packages.gz)  302 Moved Temporarily
Some index files failed to download, they have been ignored, or old ones used instead.



---

### Post by amingv on 2009-05-02
Which one did you try?

Virtualbox' repositories weren't working some time during this day (neither was the download page, though they seem to be working now), maybe try again?

---

### Post by kemo0o on 2009-05-03
I added this one 
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free

see ... this is what happen with me 

[IMG]http://i44.tinypic.com/ml2fck.jpg[/IMG]

---

### Post by amingv on 2009-05-03
Can you please post the output of

```
cat /etc/apt/sources.list
```

I have the same VB repo you mention, and it works fine.

---

### Post by kemo0o on 2009-05-04
This is 

> 

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) hardy non-free




---

### Post by amingv on 2009-05-04
I copied your sources.list verbatim into my computer and it works fine (except for the deb cdrom: line, of course, you should comment that one out). I honestly can't imagine it not working on yours...

---

### Post by tchoklat on 2009-05-04
I gave up on VBox and find VMWare better as it fully supports usb in the workstation variant!

Tony

---

### Post by kemo0o on 2009-05-04
> **amingv said:**
> I copied your sources.list verbatim into my computer and it works fine (except for the deb cdrom: line, of course, you should comment that one out). I honestly can't imagine it not working on yours...

It worked Now :lolflag: !!

---

### Post by amingv on 2009-05-04
> **kemo0o said:**
> It worked Now :lolflag: !!

Good. :)
Guess it was a server downtime or something of the sort...

---

