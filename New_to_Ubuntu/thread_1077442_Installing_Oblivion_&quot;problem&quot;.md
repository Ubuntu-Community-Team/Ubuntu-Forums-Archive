---
title: "Installing Oblivion &quot;problem&quot;"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Zazagabor on 2009-02-22
Hi there

I am totally new to Ubuntu. I will give it a try now that I managed to install it to my system. I am using dualboot with Xp. 

Ubuntu has now 31gb of free space to use but I am a bit confused here...
When I try to install Oblivion, using Wine, is says that I don+t have enought free disk space... cough cough...there is 31gb if it would just start to install itself....

Under "My computer" I can see c: partition and / partition and Z: (????!) partition 

Maybe / and Z are the same ???

Where is this 31 ext2 for Ubuntu ? Gee this is hard....
And does Ubuntu install files automatically or do I have to do it myself...

*Edit* Quiet over here

---

### Post by prinny42 on 2009-02-22
Since Wine has to pretend to be Windows, it recognizes the filesystem with a letter scheme as Windows would.  By default, Z corresponds to /, C corresponds to ~/.wine/dosdevices/c:, etc.

As for your problem, it might be caused by issues with partitioning and the location of your fake C Drive.  Might you please post the output of the following two commands?

```
sudo fdisk -l
```

```
df -h
```

As for installing things under Ubuntu, generally it is very automatic.  Almost everything you need can be found in a repository, which will allow you to install as simply as

```
sudo apt-get install (package)
```

This can also be done with a GUI through Synaptic or "Add/Remove."

Things that aren't in a repository are different.  If a .deb exists, it's still pretty easy, and usually just a matter of double-clicking the package (although I would strongly advise you to be wary of anything that isn't in the repositories *and* isn't well known; Handbrake or Wallpapoz are fine, but don't install random.deb unless you're sure of what you're doing).

Otherwise you might have to compile it or use alien, which can get a bit involved but isn't necessarily difficult.

Of course, things from Windows that install in Wine are generally just installed the same way as under Windows, perhaps with a bit of tweaking.

For more information, I recommend *The Ubuntu Pocket Guide and Reference*, which is available as a free PDF.

---

### Post by Zazagabor on 2009-02-22
Thanks for the answer. In the 1st place I reserved only 5gb of diskspace for Ubuntu. Today I tried to make more space, 30gb now, with Gparted. 

Output of the commands is in finnish, sorry ! Hope you get something out of them 

Levy /dev/sda: 320.0 Gt, 320072933376 tavua

255 päätä, 63 sektoria/ura, 38913 sylinteriä

Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

Levyn tunniste: 0x9802cc49



    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä

/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS



Levy /dev/sdb: 120.0 Gt, 120034123776 tavua

255 päätä, 63 sektoria/ura, 14593 sylinteriä

Yksiköt = 16065 * 512 = 8225280 -tavuiset sylinterit

Levyn tunniste: 0x06070607



    Laite Käynn     Alku          Loppu    Lohkot   Id  Järjestelmä

/dev/sdb1               1       10759    86421636    7  HPFS/NTFS

/dev/sdb2           10760       14593    30796605   83  Linux


/dev/sdb1               1       10759    86421636    7  HPFS/NTFS

/dev/sdb2           10760       14593    30796605   83  Linux

jukka@ubuntu:~$ df -h

Tiedostojärj.            Koko  Käyt Vapaa Käy% Liitospiste

/host/ubuntu/disks/root.disk

                      4,3G  3,4G  699M  83% /

tmpfs                 505M     0  505M   0% /lib/init/rw

varrun                505M  216K  505M   1% /var/run

varlock               505M     0  505M   0% /var/lock

udev                  505M  2,9M  502M   1% /dev

tmpfs                 505M  456K  505M   1% /dev/shm

/dev/sdb1              83G   23G   61G  27% /host

lrm                   505M  2,0M  503M   1% /lib/modules/2.6.27-11-generic/volatile

/dev/loop0            4,3G  3,4G  699M  83% /media/loop0

/dev/sda1             299G  129G  170G  44% /media/sda1

/dev/sdb2              29G   44M   28G   1% /media/sdb2

/dev/scd0             4,2G  4,2G     0 100% /media/Oblivion

---

### Post by Zazagabor on 2009-02-22
Thanks for your time. Loaded the manual and found a way to install Obi. I presume that problem was between the PC and the chair :D

Bye

---

