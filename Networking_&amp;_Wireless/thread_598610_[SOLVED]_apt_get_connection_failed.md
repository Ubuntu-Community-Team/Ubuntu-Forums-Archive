---
title: "[SOLVED] apt get connection failed"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by and77 on 2007-10-31
I have problems with apt-get this is what prompted:

and@and-laptop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0), tempo limite di connessione esaurito
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Impossibile connettersi a archive.canonical.com:80 (1.0.0.0), tempo limite di connessione esaurito
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-it                        
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-it                  
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-it
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-it
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg    
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-it
  Impossibile connettersi a archive.canonical.com:80 (1.0.0.0). - connect (101 La rete è irraggiungibile)


translation:la rete è irrangiungibile means network unreachable.
i can connect to internet trough a router.This is sorces.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted univers multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

I had ubuntu 7.04 and i had no problems.i have seen other threads but noone fixed my problem!

---

### Post by Stuart Morrow on 2007-10-31
Well, it looks to me like the problem is that Ubuntu servers' IP addresses are resolving, for you, to be 1.0.0.0, which is wrong.

Check /etc/hosts (in a text viewer) for 1.0.0.0 weirdness, and remove it if it's there, because it's wrong.

If there happens to be nothing of the sort in the hosts file, then do "sudo -s" to become root, and then run this command:

for host in archive.ubuntu.com archive.canonical.com it.archive.ubuntu.com; do echo $(nslookup $host |grep Address: |head -2 |tail -1 |cut -c 10-; nslookup $host |grep Name: |head -2 |tail -1 |cut -c 7-); done >> /etc/hosts

Now, probably you'll want to have another look at /etc/hosts, because (half-educated guess from me) it'll still be resolving as 1.0.0.0, in which case you'll want to remove those lines and put these ones in manually:

91.189.88.46     archive.ubuntu.com
91.189.90.142   archive.canonical.com
193.206.140.37 it.archive.ubuntu.com

(Which is what that long command outputs on this computer here.)

Important note, this is only a short-term solution, because ideally everything should work without tweaking that particular file.

I hope this helps (there's a strong chance that it won't, but I might come up with something else).

---

### Post by and77 on 2007-11-01
thank you!

---

