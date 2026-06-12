---
title: "[SOLVED] Failed to fetch"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ibbill on 2008-12-17
Having a problem updating  here is the error I get. Here's my sources.list file

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by Bucky Ball on 2008-12-17
You could try:

System->Administration->Software Sources

... and change the server/mirror in there to 'Main' if it isn't already. If it is, change it to another server/mirror.

Do you get an error when you attempt to run this in a terminal:

```
sudo apt-get update
```? It looks like what you are after is actually missing from the repository, but see how you go after the update command.

---

### Post by taurus on 2008-12-17
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the . (period) at the end of the third to last entry.  Then, remove the . (period) from the last two entries, after main and before universe.  Save it and close down gedit window.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2008-12-17
> **taurus said:**
> remove the . (period) from the last two entries, after main and before universe.  Save it and close down gedit window.

Nicely spotted. :) That should work.

---

### Post by ibbill on 2008-12-17
> **taurus said:**
> Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the . (period) at the end of the third to last entry.  Then, remove the . (period) from the last two entries, after main and before universe.  Save it and close down gedit window.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

Thanks for the help you two are awesome After running the above in the terminal I get the following.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Here is my new source list also have been looking all over for this problem and did see something about  removing partner and adding something but not sure if that is right. Thanks again for your help.

---

### Post by unutbu on 2008-12-17
ibbill, would you please post the output of 
```

cat /etc/apt/sources.list
```
in code tags ([http://ubuntuforums.org/showpost.php?p=5490091&postcount=43](http://ubuntuforums.org/showpost.php?p=5490091&postcount=43))

It will help us figure out what is going on.

Also, once your sources.list is fixed, you may want to go to System>Admin>Software Sources, select "Other" for your server, and click the "Best server" button. This will search for the mirror with the best ping rate for you. You may be able to increase your download speed considerably by doing this.

See
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
(Go to the "Download Server" section).

---

### Post by thomasgilling on 2008-12-17
There is something wrong with your Repo's then! Make sure you use valid repo's and download the latest software by "apt-get update" if you are not root add "sudo" to that.

---

### Post by ibbill on 2008-12-17
[QUOTE=unutbu;6387658]ibbill, would you please post the output of 
```

cat /etc/apt/sources.list
```
in code tags ([http://ubuntuforums.org/showpost.php?p=5490091&postcount=43](http://ubuntuforums.org/showpost.php?p=5490091&postcount=43))

It will help us figure out what is going on.

Also, once your sources.list is fixed, you may want to go to System>Admin>Software Sources, select "Other" for your server, and click the "Best server" button. This will search for the mirror with the best ping rate for you. You may be able to increase your download speed considerably by doing this.

Is there something wrong with these 2 lines.## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

I tried to up load the new list would not let me says error. so pasting in here



[CODE]deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse

deb http://ppa.launchpad.net/gkulyk/ubuntu intrepid main

deb http://dl.google.com/linux/deb/ testing non-free
deb http://archive.ubuntu.com/ubuntu/ intrepid main
deb http://security.ubuntu.com/ubuntu/ intrepid-security restricted main multiverse main universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-backports restricted main multiverse main universe
ibbill@ibbill-desktop:~$

---

### Post by ibbill on 2008-12-17
I ran sudo apt-get update still getting the following. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ibbill on 2008-12-17
I ran sudo apt-get update still getting the following. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ibbill on 2008-12-17
> **ibbill said:**
> I ran sudo apt-get update still getting the following. 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main./binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

copy of my software source.

---

### Post by ibbill on 2008-12-17
why does it show cd rom  Xubuntu when I have only ubuntu 8.10 installed.

---

### Post by unutbu on 2008-12-17
I've posted my /etc/apt/sources.list here:
wget [http://paste.ubuntu.com/87266/](http://paste.ubuntu.com/87266/)

It is essentially the default intrepid sources.list, except that server has been changed to gpl.savoirfairelinux.net, a mirror in Quebec. I've also added your 3rd-party software sources to the bottom.

If you would like to try it, first back up your current sources.list:
```

cd /etc/apt
sudo mv sources.list sources.list_20081217
sudo wget http://paste.ubuntu.com/87266/plain/ -O /etc/apt/sources.list
sudo apt-get update

```

---

### Post by ibbill on 2008-12-17
That did it  whooooooosh thank you thank you oh my.Marking it solved .

Bil

---

