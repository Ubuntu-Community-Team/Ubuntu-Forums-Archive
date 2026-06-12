---
title: "Wine will not uninstall"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2009-07-28
I cannot get wine to uninstall. I used Synaptic to install it but it wasn't working with anything. I have used DVD_Shrink with it before flawlessly and it was not working so I thought I'd remove Wine completely and reinstall it again. So when I went into Synaptic again I got a broken package error that not all of it was removed. 

I fired up a terminal and ran

```
sudo apt-get purge wine
```


I got back this:

```
gary@gary-laptop:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-liberation lib32nss-mdns winbind
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 55.8MB disk space will be freed.
Do you want to continue [Y/n]? y
Segmentation fault
(Reading database ... 130603 files and directories currently installed.)
Removing wine ...
Segmentation fault
dpkg: error processing wine (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I don't know what a status 139 error is. 

Anyone have any ideas?

---

### Post by RomeReactor on 2009-07-28
Hi. You can try with:
```
sudo aptitude -f install
```
If that doesn't work:
```
sudo dpkg --remove --force-remove-reinstreq wine
```

---

