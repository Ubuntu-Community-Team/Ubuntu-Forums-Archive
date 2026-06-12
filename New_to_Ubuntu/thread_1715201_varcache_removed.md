---
title: "/var/cache removed"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by twr_HRT on 2011-03-26
Hi, i've read somewhere that in order to get some disk space i could remove the /var/cache directory....
You can guess what happened. I removed it by doing sudo rm -r /var/cache.
Now the software center doesn't work, the synaptics doesn't work also, and the update manager gives error when trying to install new updates.
I kow it was a stupid thing to do especialy not being a very experienced user with ubuntu. 
Can anyone help? Is it  my only option to re-instal ubuntu?
Thanks

---

### Post by JKyleOKC on 2011-03-26
Try "sudo mkdir -p /var/cache/apt" which MAY make the package managers such as Synaptic usable. However there were many subdirectories in addition to apt, many of those installed when other packages were created, so a full backup of your home directory followed by a clean re-install of everything is probably your easiest way out of the situation...

EDIT: Note: before ever doing a "rm -r" operation, best make sure you know EVERYTHING that will be affected by the recursion. Ditto before doing anything that requires "sudo" (my suggestion above simply re-creates two directories, due to the -p option).

---

### Post by kellemes on 2011-03-26
I think you have a problem indeed..

Next time use the proper tool to clean your cache..

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

[http://linux.die.net/man/8/apt-get]("http://linux.die.net/man/8/apt-get")

---

### Post by garvinrick4 on 2011-03-26
Your filesystem keeps packages in your cache so as not to have to fetch new ones from repo's
and will be removed if need more disk space by.
```
sudo apt-get clean
```cache directory holds more than just some installed packages and you removed what was in the whole /var/cache  directory and that was more or less a fatal mistake for GUI if not more. Here is what is in /var/cache after cleaning packages Not removing directory. And a lot
of sub-directorys in these.
/var/cache/apt
/var/cache/apt-xapian-index
/var/cache/cups
/var/cache/debconf
/var/cache/dictionaries-common
/var/cache/flashplugin-installer
/var/cache/fontconfig
/var/cache/gdm
/var/cache/jockey
/var/cache/ldconfig
/var/cache/man
/var/cache/pm-utils
/var/cache/pppconfig
/var/cache/samba
/var/cache/software-center
/var/cache/system-tools-backends
```
Here is a way to change directorys and see what is in them and who owns them.
rick@rick-HP:~$ cd /var/cache
rick@rick-HP:/var/cache$ ls
apt               dictionaries-common    jockey    pppconfig
apt-xapian-index  flashplugin-installer  ldconfig  samba
cups              fontconfig             man       software-center
debconf           gdm                    pm-utils  system-tools-backends
rick@rick-HP:/var/cache$ ls -la
total 72
drwxr-xr-x 18 root root  4096 2011-03-23 14:18 .
drwxr-xr-x 15 root root  4096 2011-01-25 01:00 ..
drwxr-xr-x  3 root root  4096 2011-03-26 00:47 apt
drwxr-xr-x  3 root root  4096 2011-03-25 12:57 apt-xapian-index
drwxrwxr-x  3 root lp    4096 2011-03-17 22:38 cups
drwxr-xr-x  2 root root  4096 2011-03-26 00:46 debconf
drwxr-xr-x  2 root root  4096 2010-10-07 09:19 dictionaries-common
drwxr-xr-x  2 root root  4096 2011-03-24 19:21 flashplugin-installer
drwxr-xr-x  2 root root  4096 2011-03-24 19:20 fontconfig
drwxr-xr-x  3 root root  4096 2011-01-11 14:54 gdm
drwxrwsr-t  2 root admin 4096 2011-01-11 14:55 jockey
drwx------  2 root root  4096 2011-03-26 00:47 ldconfig
drwxr-sr-x 33 man  root  4096 2011-03-26 00:44 man
drwxr-xr-x  2 root root  4096 2010-09-24 04:30 pm-utils
drwxr-xr-x  2 root root  4096 2009-02-20 09:56 pppconfig
drwxr-xr-x  3 root root  4096 2011-03-26 12:20 samba
drwxr-xr-x  3 root root  4096 2011-03-24 19:24 software-center
drwxr-xr-x  3 root root  4096 2011-01-25 17:12 system-tools-backends
rick@rick-HP:/var/cache$ 

```
Link to download pdf explaining Ubuntu file system below and more:
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

