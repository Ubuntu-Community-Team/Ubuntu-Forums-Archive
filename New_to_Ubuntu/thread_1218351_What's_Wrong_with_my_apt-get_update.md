---
title: "What's Wrong with my apt-get update???"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by Moe Z on 2009-07-20
HI all..
       when i type sudo apt-get update to update my system... it start getting files, but some files are ignored.. i don't know why... and at last it shows this message...

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems

pls help me.. what's that public key?

---

### Post by Yvan300 on 2009-07-20
I had a similar problem, you either have to import the keys stated or you have to change the server that you are using with ubuntu. Follow the guide here to learn how to import keys [http://blog.edseek.com/archives/2007/03/17/apt-key-gpg-key-import-on-ubuntu-and-debian/](http://blog.edseek.com/archives/2007/03/17/apt-key-gpg-key-import-on-ubuntu-and-debian/)

---

### Post by bacil on 2009-07-20
hi You need to get keys from keyserver for those repositories

```
sudo gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
```

hope that helps

EDIT:

sorry forgot to import keys :-)

```
sudo gpg --export --armor 437D05B5 | sudo apt-key add - 
```

---

### Post by Moe Z on 2009-07-20
Thanks for the quick reply, i'll check them out now.. :)

---

### Post by philinux on 2009-07-20
Just for completeness can you post yor sources list. Easy command.

```
cat /etc/apt/sources.list
```

Copy and paste the output back here. Wrap the text in code tags. (#) button.

---

### Post by Moe Z on 2009-07-20
cndev@cn-ubuntu:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg: WARNING: unsafe ownership on configuration file `/home/cndev/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

i think it's still not ok.. :(
pls help me again
:D, i'm new to ubuntu.. really dumb :(

---

### Post by Moe Z on 2009-07-20
here's the out put of cat /etc/apt/sources.list

cndev@cn-ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20080930)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mm.archive.ubuntu.com/ubuntu/](http://mm.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://mm.archive.ubuntu.com/ubuntu/](http://mm.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-security multiverse

---

### Post by bacil on 2009-07-20
can you run 

```
ls -l /home/cndev/.gnupg/gpg.conf
```it seems that you have not permissions to your own file or .gnupg directory

EDIT:

SOOORRRYYYY ! my bad 

gpg command should be run either as root or as user but not with sudo since gpg.conf is owned and accessible only to user please try without SUDO :)

so leave out suod in second part of my advice aswel 

```
gpg --export --armor 437D05B5 | sudo apt-key add -
```

---

### Post by philinux on 2009-07-20
Just try updating again. Sources look ok to me.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Moe Z on 2009-07-20
here's the out put of ls -l command

-rw------- 1 cndev cndev 28 2009-06-08 06:25 /home/cndev/.gnupg/gpg.conf

thx u all for u help.. pls help me to the end

---

### Post by Moe Z on 2009-07-20
there's a problem to update my system... cuz i got only 20Kbps connection.. too slow.. i'm living in myanmar.. :D
but i'll try what u said philinux.. thx...

---

### Post by Moe Z on 2009-07-20
it says (i think) there's nothing to update my system... but why warning??
here's the out put when i finished update && upgrade

Fetched 135kB in 23s (5732B/s)                                                 
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by bacil on 2009-07-20
Have look to my edit. it is pub_key issue when you get it from keyserver it will be working even on slow line

---

### Post by Moe Z on 2009-07-20
cndev@cn-ubuntu:~$ gpg --export --armor 437D05B5 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

i think i still don't get that key.. :D
btw, can i still update my system without those keys? if it isn't necessary... let it b

---

### Post by bacil on 2009-07-20
Did you run that first bit before second step ? :-)

it should look like this :

```

[-23% 01:21:03]-bacil@one:~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
[-23% 01:21:25]-bacil@one:~$ gpg --export --armor 437D05B5 | sudo apt-key add -
OK
[-22% 01:20:32]-bacil@one:~$


```

---

### Post by Moe Z on 2009-07-20
ahhh... my bad.. really sorry, i didn't remove that sudo command for the gpt --keyserver command...
it's now requesting key.. i think it may take a long time to get key with my 13.5Kbps.. (now it's slowing down.. not even 20Kbps).. it did.....!! hoorayy.. thx thx..

---

### Post by Moe Z on 2009-07-20
it said "key server timed out" i think the main problem is my internet connection..!! damn!!

---

### Post by bacil on 2009-07-20
No worries, good luck :-) on that line .. i had trouble with my isp couple weeks back and was running on similar speed :-)

---

### Post by Moe Z on 2009-07-20
LOL.. ok.. thank u bacil..

---

### Post by LiaGalanodel on 2009-10-14
Hi! 

I have the same problem but I don't know what I must doing.

I'm sorry but I new in Linux and I try but I fail.

When I write : 

```
apt-get update
```

```
Fetched 570B in 1s (399B/s)                               
W: GPG error: http://us.archive.ubuntu.com jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://us.archive.ubuntu.com jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/jaunty/Release  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Here that's whath I have when I do your solution:

```
amelieathanassiadis@SorinLinux:~$ gpg --keyserver keyserver.ubuntu.com --recv 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpgkeys: key 437D05B5 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
amelieathanassiadis@SorinLinux:~$ gpg --export --armor 437D05B5 | sudo apt-key add -
[sudo] password for amelieathanassiadis: gpg: WARNING: nothing exported

gpg: no valid OpenPGP data found.

```Thanks,

Best regards.

---

### Post by hreikin on 2009-12-18
hi, im fairly new to ubuntu and have been doing fine using these forums for help on anything i needed up until now

i think i have a similar problem to the OP but the answers provided in this thread (and a few others) havent fixed it yet :(

when i run sudo apt-get update i get this message at the end

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89

any ideas/help would be greatly appreciated

mikeee

---

### Post by slakkie on 2009-12-18
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

or

sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys KEYID

---

### Post by hreikin on 2009-12-18
> **slakkie said:**
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

or

sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys KEYID

thanks for the quick reply, it worked

thank you :)

---

### Post by buddy007 on 2011-09-16
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

or

sudo apt-key adv --keyserver wwwkeys.eu.pgp.net --recv-keys KEYID


its not working
pls suggest sumthing else

---

### Post by oldos2er on 2011-09-16
Please start a new thread with full details of your problem.

Closed for necromancy.

---

