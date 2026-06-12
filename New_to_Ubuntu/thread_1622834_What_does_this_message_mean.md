---
title: "What does this message mean ?"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by ericstrom on 2010-11-15
Running Lucid and trying to add a repository through Synaptic. The line I put in is :

deb [http://cran.opensourceresources.org/bin/linux/ubuntu](http://cran.opensourceresources.org/bin/linux/ubuntu) lucid/

I also tried:

deb [http://cran.r-project.org/bin/linux/debian](http://cran.r-project.org/bin/linux/debian) etch/


It seems to add ok but then I get a message saying I have to hit the reload button. So I hit that, it downloads some files and then I get the following message:

Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Release.gpg  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/en_US.bz2  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Packages.gz  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch [http://cran.r-project.org/bin/linux/debian/etch/Packages.gz](http://cran.r-project.org/bin/linux/debian/etch/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

What do I do ? I seem to going round in circles with the same basic error.

---

### Post by s3MA00RRNY on 2010-11-16
I have no clue why the Ubuntu one doesn't work, but if you follow the Debian one it says etch-cran and lenny-cran. try entering either of those instead of just "etch".

---

### Post by ericstrom on 2010-11-16
Same basic story when I use etch-cran instead of etch

GPG error: [http://cran.r-project.org](http://cran.r-project.org) etch-cran/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06F90DE5381BA480Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Release.gpg  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/en_US.bz2  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Packages.gz  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas of what to try next ?

---

### Post by plucky on 2010-11-16
Open a terminal and ```
cat /etc/apt/sources.list
``` and post the output.

Added this line ```
deb http://cran.opensourceresources.org/bin/linux/ubuntu lucid/
``` to my sources.list in maverick and this is what I got
> 
Get:3 [http://cran.opensourceresources.org](http://cran.opensourceresources.org) lucid/ Packages [13.7kB]
Fetched 15.2kB in 1s (9,040B/s)
Reading package lists... Done
W: GPG error: [http://cran.opensourceresources.org](http://cran.opensourceresources.org) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821

which just means you have to add the key with
```
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -
```

Good Luck

---

### Post by ericstrom on 2010-11-16
When you say...which just means you have to add the key with
Code:
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -t means you have to add the key ...

Ad the key where ? Add the key how ?

---

### Post by plucky on 2010-11-17
> **ericstrom said:**
> When you say...which just means you have to add the key with
Code:
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg -a --export E2A11821 | sudo apt-key add -t means you have to add the key ...

Ad the key where ? Add the key how ?

Open a  terminal **(Applications > Accessories > Terminal)**

Then either copy and paste or type in these commands ```
gpg --keyserver subkeys.pgp.net --recv-key E2A11821
``` and ```
gpg -a --export E2A11821 | sudo apt-key add -
```

If it replies **OK** then you should be good to go.

Good Luck

---

### Post by ericstrom on 2010-11-17
Still driving me crazy ! In the latest, I followed the instructions by Plucky and saw the OK message. BUT ...when update manager runs, I get the following:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct


Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Release.gpg  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/en_US.bz2  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Packages.gz  Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

What do I do to fix this ? I pulled all references to cran out of the apt repository list (at least I think I did). I have no idea why this is happening or what to do. Please help.

---

### Post by plucky on 2010-11-18
> Failed to fetch http://<my.favorite.cran.mirror>/bin/linux/ubuntu/lucid/Packages.gz Something wicked happened resolving '<my.favorite.cran.mirror>:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

What do I do to fix this ? I pulled all references to cran out of the apt repository list (at least I think I did). I have no idea why this is happening or what to do. Please help. 

You have entries in your sources.list that are incorrect.
Open a terminal and post output of these commands ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

so we can determine where the entries exist.

Good Luck

---

