---
title: "Broken Packages - messed up PHP"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by tsalb on 2010-12-29
I was playing around with iRedAdmin and managed to screw something up - so i removed it via a shell script and all seemed well. When I tried to reinstall it, it seems some configs weren't completely removed so it wasn't like starting from square one...

Long story short, I think I may have been overzealous in cleaning packages and inadvertently removed some important packages - i think i broke my LAMP.

This is the error I'm getting when trying to reinstall something

```
The following packages have unmet dependencies:
 php5-common : Conflicts: php5-mhash
 php5-mhash : Depends: php5-common (= 5.2.10.dfsg.1-2ubuntu6.5) but 5.3.3-1ubuntu9.1 is to be installed
E: Broken packages

``` 

I've already tried the following

```

sudo apt-get -f install
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo tasksel lamp-server
sudo tasksel lamp

```

The LAMP server was set up perfectly prior to the iRedAdmin debacle, so is there a way to rebuild/reinstall the PHP portion completely? Or somehow fix my package dependency errors?

---

### Post by karthick87 on 2010-12-29
Try,
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tsalb on 2010-12-29
No go on those commands =(

---

### Post by karthick87 on 2010-12-29
Try the following,and post back the results..
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
```
sudo apt-get install -f
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tsalb on 2010-12-29
End results for both after 'sudo apt-get install -f' and sudo apt-get update && sudo apt-get upgrade'

```
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

trying
```
sudo apt-get install php5-mhash
```

still results 

```
The following packages have unmet dependencies:
 php5-mhash : Depends: php5 but it is not going to be installed or
                       phpapi-20060613
              Depends: php5-common (= 5.2.10.dfsg.1-2ubuntu6.5) but it is not going to be installed
E: Broken packages

```

[Related bug?]("https://bugs.launchpad.net/ubuntu/+source/php5/+bug/541439")

Temporary fix says to remove in /etc/php5/conf.d/mhash.ini but i dont have it.

---

### Post by sikander3786 on 2010-12-29
Yes it seems like a known bug.

Which version of Ubuntu is this?

Did you try installing php5-common manually?

```
sudo apt-get install php5-common
```

Or,

```
sudo apt-get install --reinstall php5-common
```

---

### Post by tsalb on 2010-12-29
10.10

Yep, ran both of those commands and php5-mhash still won't install.

Thanks for the help though, guys!

---

### Post by tsalb on 2010-12-29
Well this is unfortunate, I have some services that require the outdated php5-mhash to function.

I successfully downgraded php using aptitude and installed php5-mhash, but it won't let me upgrade php again including php5-mhash. 

Is there no way to reinstall latest ver of php5-common with the mhash included? ugh...

---

### Post by ppafford on 2011-01-11
Sorry to bump this thread but I'm running into the same problem. Did you find a solution?

I'm running 10.04 LTS and I don't want to upgrade. I pinned the PHP version to 5.2.x as my work have not fully upgraded to 5.3.x as some of the production scripts would break.

Any help would be great in solving this issue.

Thanks in advance,
--Phill

---

### Post by sikander3786 on 2011-01-12
> **ppafford said:**
> Sorry to bump this thread but I'm running into the same problem. Did you find a solution?

I'm running 10.04 LTS and I don't want to upgrade. I pinned the PHP version to 5.2.x as my work have not fully upgraded to 5.3.x as some of the production scripts would break.

Any help would be great in solving this issue.

Thanks in advance,
--Phill
Please post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2011-01-12
> **ppafford said:**
> Sorry to bump this thread but I'm running into the same problem. Did you find a solution?

I'm running 10.04 LTS and I don't want to upgrade. I pinned the PHP version to 5.2.x as my work have not fully upgraded to 5.3.x as some of the production scripts would break.

Any help would be great in solving this issue.

Thanks in advance,
--Phill
> **ppafford said:**
> Sorry to bump this thread but I'm running into the same problem. Did you find a solution?

I'm running 10.04 LTS and I don't want to upgrade. I pinned the PHP version to 5.2.x as my work have not fully upgraded to 5.3.x as some of the production scripts would break.

Any help would be great in solving this issue.

Thanks in advance,
--Phill
Please post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by ppafford on 2011-09-15
Well if anyone is facing this problem I figured it out.

Download and install it manually

Here are the steps:

(I'm using the Karmic Repo to match the version I have pinned)

[https://launchpad.net/ubuntu/karmic/i386/php5-mhash]("https://launchpad.net/ubuntu/karmic/i386/php5-mhash")

Download the matching version, installed on my box is this version of php-common 5.2.10.dfsg.1-2ubuntu6 So this is the version I downloaded:

[https://launchpad.net/ubuntu/karmic/i386/php5-mhash/5.2.10.dfsg.1-2ubuntu6]("https://launchpad.net/ubuntu/karmic/i386/php5-mhash/5.2.10.dfsg.1-2ubuntu6")

Then I manually installed the package like this:

```
sudo dpkg -i php5-mhash_5.2.10.dfsg.1-2ubuntu6_i386.deb
```

Output:

> Selecting previously deselected package php5-mhash. (Reading database ... 357032 files and directories currently installed.) Unpacking php5-mhash (from php5-mhash_5.2.10.dfsg.1-2ubuntu6_i386.deb) ... Setting up php5-mhash (5.2.10.dfsg.1-2ubuntu6) ...

NOTE:

I did install the wrong version before finding the correct version to download and install. The output was something like this:

```
sudo dpkg -i php5-mhash_5.2.6.dfsg.1-3ubuntu4_i386.deb 
```

> Selecting previously deselected package php5-mhash. (Reading database ... 357032 files and directories currently installed.) Unpacking php5-mhash (from php5-mhash_5.2.6.dfsg.1-3ubuntu4_i386.deb) ... dpkg: dependency problems prevent configuration of php5-mhash: php5-mhash depends on php5-common (= 5.2.6.dfsg.1-3ubuntu4); however: Version of php5-common on system is 5.2.10.dfsg.1-2ubuntu6. dpkg: error processing php5-mhash (--install): dependency problems - leaving unconfigured Errors were encountered while processing: php5-mhash

Running this to fix the broken install:

```
sudo apt-get -f install
```

Output:

> Reading package lists... Done Building dependency tree Reading state information... Done Correcting dependencies... Done The following packages were automatically installed and are no longer required: libmhash2 Use 'apt-get autoremove' to remove them. The following packages will be REMOVED: php5-mhash 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 1 not fully installed or removed. After this operation, 69.6kB disk space will be freed. Do you want to continue [Y/n]? y (Reading database ... 357033 files and directories currently installed.) Removing php5-mhash ...

---

### Post by angelicakm on 2012-03-07
Try the following:

```
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php5
apt-get update
apt-get autoremove
apt-get install php5
apt-get install php5-common
apt-get install php5-cgi
apt-get install php5-fpm
```( add any other php5 extensions you need)

Tell me if it works for you.

---

