---
title: "Cant do updates"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by concerto on 2009-02-22
When I try to update through update manager I get this.....



Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.




[COLOR="Red"]and when I try it from the command line I get this...[/COLOR]




concerto@concerto:~$ sudo apt-get install update
[sudo] password for concerto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
concerto@concerto:~$ 



any suggestions?

Thanks

---

### Post by hansdown on 2009-02-22
Hi concerto.

Gutsy is nearing the end of it's support, so updates may not be available.

Have you considered 8.04 or 8.10?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by Panzor on 2009-02-22
> concerto@concerto:~$ sudo apt-get install update
[sudo] password for concerto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
concerto@concerto:~$ 



any suggestions?

Thanks

I *almost* missed the error in that command =P. You want to run:
```
$sudo apt-get update
$sudo apt-get upgrade
```To do the equivalent of what the gui does for updating. I'm not sure if you'll do this successfully, but that's the correct way to do it in the terminal. What do you get?

---

### Post by concerto on 2009-02-23
Here's the main problem...
I can't upgrade to a newer version because I get an error.

When I try to update to 8.10 I get this...


[COLOR="Red"]
Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 113M free space on disk '/boot'. Please free at least an additional 75.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/COLOR]

When I try "sudo apt-get clean" Nothing happens and the update still dosent work.


What should I do?


Thank you.

---

### Post by taurus on 2009-02-23
How's your disk space situation?

```
df -h
```

---

### Post by concerto on 2009-02-23
concerto@concerto:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             290G   22G  254G   8% /
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
/dev/sda3             193M  148M   36M  81% /boot
tmpfs                 1.5G   39M  1.5G   3% /lib/modules/2.6.24-23-generic/volatile
concerto@concerto:~$

---

### Post by avtolle on 2009-02-23
As stated in the error message, your boot partition doesn't have enough space. Either enlarge the partition, or delete some old kernels to free up that partition. 

As to your other issue, the repos you are trying to access are for Feisty, which reached its EOL in October, 2008, and the repos were taken down.

---

### Post by matey3 on 2009-02-23
edit your sources.list in /etc/apt/ and put these lines in it;

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

the errors is 404 i dont think its space problem? may be both?

---

### Post by concerto on 2009-02-23
ok. thank you.

so how do I enlarge my boot partition?

---

### Post by concerto on 2009-02-23
should I start a new thread on this?

---

