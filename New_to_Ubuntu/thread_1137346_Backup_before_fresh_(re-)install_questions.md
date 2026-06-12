---
title: "Backup before fresh (re-)install questions"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Nico-dk on 2009-04-25
I'm dual-booting Ubuntu 8.04 and XP.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2   *    83891430   108310229    12209400   83  Linux
/dev/sda3       108310230   312576704   102133237+   5  Extended
/dev/sda5       108310293   306696914    99193311   83  Linux
/dev/sda6       306696978   312576704     2939863+  82  Linux swap / Solaris
nico@nico-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              12G  3,0G  8,0G  28% /
varrun                1,8G   92K  1,8G   1% /var/run
varlock               1,8G     0  1,8G   0% /var/lock
udev                  1,8G   60K  1,8G   1% /dev
devshm                1,8G   24K  1,8G   1% /dev/shm
lrm                   1,8G   39M  1,7G   3% /lib/modules/2.6.24-22-generic/volatile
/dev/sda5              94G   18G   72G  20% /home
gvfs-fuse-daemon       12G  3,0G  8,0G  28% /home/nico/.gvfs
```

I want to double my ntfs partition size, and figure a clean install will be the best option. Clean as in wiping all partitons and starting from scratch.

I would like to retain all my apps and settings, which should be possible if I do this

```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

and after reinstall this

```
sudo apt-get update
sudo apt-get dist-upgrade
dpkg –set-selections < ubuntu-files
sudo dselect

```

I'll of course be backing up /home too.

2 questions though.

1) Should I back up anything in addition to /home?
2) Did I miss a better method of retaining apps and settings ?

Thanks for your time :)

---

### Post by kwacka on 2009-04-25
It may also be useful to go to Synaptic --> File --> Save Markings.

In the window that opens, mark the box 'save full state' and save where you want.

After re-install, go back to Synaptic --> File --> Read Markings and your current list of applications will be re-installed. (Assuming you've reactivated all your repositories, of course).

---

### Post by Sef on 2009-04-25
```
sudo apt-get update
sudo apt-get dist-upgrade

```

That is a way that is no longer supported to upgrade.

After doing a clean install, you simply need these two commands below to be up to date.

```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Nico-dk on 2009-04-25
Thanks ... both of you

---

