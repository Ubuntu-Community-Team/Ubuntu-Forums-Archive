---
title: "problem with update manager"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by amitpokhrel on 2010-11-03
since a week my update manager does not check for updates automatically.. when I manually try to check for the updates i get error.It says "failed to download repository information"...what can I do??

---

### Post by Peter09 on 2010-11-03
Can you provide more detail of the error message.
 
Also try
 
```
sudo apt-get update
```
 
in a terminal and watch for any error messages.

---

### Post by amitpokhrel on 2010-11-03
This was the error message when I tried- sudo apt- get update

Fetched 3,812B in 51s (75B/s)
W: Failed to fetch [http://ppa.launchpad.net/bean123/burg/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/bean123/burg/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bean123/burg/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/bean123/burg/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Elfy on 2010-11-03
Seems to have gone and been replaced by bean123ch.

I'd check sources.list to see if the ppa is referenced there - ```
gedit /etc/apt/sources.list
```

If it is - then open for editing and put a # in front of the bean123 lines

```
gksudo gedit /etc/apt/sources.list
```

If it is not referenced there - look in /etc/apt/sources.list.d/ for a PPA for bean123 and remove it.

If you are not sure then run 

```
ls /etc/apt/sources.list.d
``` and post the result for someone to check.

To reacquire the correct PPA 

```
sudo add-apt-repository ppa:bean123ch/burg
```

[https://launchpad.net/~bean123ch/+archive/burg](https://launchpad.net/~bean123ch/+archive/burg)

---

### Post by amitpokhrel on 2010-11-03
I tried-gedit /etc/apt/sources.list, source,list file opened but i could not find bean123 lines..
the list of files from the command ls /etc/apt/sources.list.d are:

am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
bean123-burg-maverick.list
bean123-burg-maverick.list.save
bean123ch-burg-maverick.list
bean123ch-burg-maverick.list.save
bisigi-ppa-maverick.list
bisigi-ppa-maverick.list.save
google-chrome.list
google-chrome.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.save
ubuntu-tweak-testing-ppa-maverick.list
ubuntu-tweak-testing-ppa-maverick.list.save
voria-ppa-maverick.list
voria-ppa-maverick.list.save


for command:sudo add-apt-repository ppa:bean123ch/burg, i got this message:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A267D98DF71B10F601CFAC1B55708F1EE06803C5
gpg: requesting key E06803C5 from hkp server keyserver.ubuntu.com
gpg: key E06803C5: "Launchpad burg" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

### Post by Peter09 on 2010-11-03
Sorry but what are
 
> am-monkeyd-nautilus-elementary-ppa-maverick.list
am-monkeyd-nautilus-elementary-ppa-maverick.list.save
[COLOR=red]bean123-burg-maverick.list[/COLOR]
[COLOR=red]bean123-burg-maverick.list.save[/COLOR]
[COLOR=red]bean123ch-burg-maverick.list[/COLOR]
[COLOR=red]bean123ch-burg-maverick.list.save[/COLOR]
[COLOR=black]bisigi-ppa-maverick.list[/COLOR]
bisigi-ppa-maverick.list.save
google-chrome.list
google-chrome.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.save
ubuntu-tweak-testing-ppa-maverick.list
ubuntu-tweak-testing-ppa-maverick.list.save
voria-ppa-maverick.list
voria-ppa-maverick.list.save
 

these lines?

---

### Post by Elfy on 2010-11-03
You already have the bean123ch ppa.

Open nautilus as root ```
gksudo nautilus /etc/apt/sources.list.d
``` and remove the two bean123 lists 

bean123-burg-maverick.list
bean123-burg-maverick.list.save

An update now should lose the errors.

---

### Post by Elfy on 2010-11-03
> **Peter09 said:**
> Sorry but what are
 

these lines?

2 are the out of date ppa - 2 are current

---

### Post by amitpokhrel on 2010-11-03
thanks it worked..

---

### Post by jdforsythe on 2010-11-13
i had this problem. Two questions:

1) this happened to me with PPAs that don't have maverick directories - they stopped with karmic. But why did apt-add-repository work, and allow me to download and update the software, and only weeks later stop working?

2) is it safe to just edit the .list file in /etc/apt/sources.list.d/*.list and change maverick to karmic?

---

### Post by jdforsythe on 2010-11-13
BTW - the two repositories that did this to me were: qbzr-dev and gdm2setup

Another thing - maybe this should be a bug report... when the update manager would come up, it would claim that my sources hadn't been updated in 12 days (even if I manually refreshed via the GUI or terminal) even though it would show daily updates to Chromium (and whatever other updates there were). Just because a repository or two fails doesn't mean the sources haven't been updated in 12 days...

---

