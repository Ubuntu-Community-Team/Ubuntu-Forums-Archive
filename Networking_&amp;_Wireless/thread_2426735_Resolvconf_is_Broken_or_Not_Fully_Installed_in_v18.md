---
title: "Resolvconf is Broken or Not Fully Installed in v18.04"
date: 2019-09-12
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2019-09-12
Upgraded from 16.04 LTS to 18.04 and "DNS Bad Config". Can Ping OK, So, Ran ...

```

sudo dpkg-reconfigure resolvconf

```

and get - "resolvconf is broken or not fully installed"

Stumped as to what to do next. Any suggestions ???

Thanks!
Rick
:confused:

---

### Post by Skaperen on 2019-09-12
is the file name [COLOR=#0000cd][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR] a symlink or a regular file?  what is its contents?

---

### Post by Rick St. George on 2019-09-12
> **Skaperen said:**
> is the file name [COLOR=#0000cd][FONT=courier new]/etc/resolv.conf[/FONT][/COLOR] a symlink or a regular file?  what is its contents?

Link !!!  Think v18.04 uses NetPlan instead. Look here; [https://askubuntu.com/questions/1075692/dns-resolution-broke-after-upgrading-to-18-04-resolvconf-broken-or-not-fully-in](https://askubuntu.com/questions/1075692/dns-resolution-broke-after-upgrading-to-18-04-resolvconf-broken-or-not-fully-in)  
Says to download resolvconf.deb manually from official Ubuntu source. May try that and post back.... what do you think ???

---

### Post by Rick St. George on 2019-09-12
Downloaded new file as state above, and Ran the following;

```

$ sudo apt install ./resolvconf_1.79ubuntu10_all.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'resolvconf' instead of './resolvconf_1.79ubuntu10_all.deb'
The following packages were automatically installed and are no longer required:
  libwhoopsie-preferences0 python-pyasn1 whoopsie-preferences xbrlapi
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  resolvconf
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/48.2 kB of archives.
After this operation, 187 kB of additional disk space will be used.
Get:1 /home/stephen/Downloads/ISO/resolvconf_1.79ubuntu10_all.deb resolvconf all 1.79ubuntu10 [48.2 kB]
Preconfiguring packages ...
Unknown interface eth0
Selecting previously unselected package resolvconf.
(Reading database ... 258255 files and directories currently installed.)
Preparing to unpack .../resolvconf_1.79ubuntu10_all.deb ...
Unpacking resolvconf (1.79ubuntu10) ...
Setting up resolvconf (1.79ubuntu10) ...
Unknown interface eth0
Created symlink /etc/systemd/system/sysinit.target.wants/resolvconf.service -> /lib/systemd/system/resolvconf.service.
Created symlink /etc/systemd/system/systemd-resolved.service.wants/resolvconf-pull-resolved.path -> /lib/systemd/system/resolvconf-pull-resolved.path.
resolvconf-pull-resolved.service is a disabled or a static unit, not starting it.
resolvconf-pull-resolved.service is a disabled or a static unit, not starting it.
Processing triggers for systemd (237-3ubuntu10.29) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for ureadahead (0.100.0-21) ...
Processing triggers for resolvconf (1.79ubuntu10) ...
N: Download is performed unsandboxed as root as file '/home/stephen/Downloads/ISO/resolvconf_1.79ubuntu10_all.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
stephen@stephen-evo-5723:~/Downloads/ISO$ sudo dpkg --reconfigure resolvconf
dpkg: error: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


```

Now I'm really stumped ?!?!?

---

### Post by Skaperen on 2019-09-12
i found that systemd was running a resolver and doing funny things.  not laughable.

---

### Post by pcfan1234 on 2019-09-13
Remove resolvconf!
Ubuntu 18.04 uses systemd-resolve
This software manages the symlink of /etc/resolv.conf
The symlink should be the following
```
djkuhpisse@djkuhpisse-HP-ZBook-15:~$ ls -la /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Jan  6  2019 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
djkuhpisse@djkuhpisse-HP-ZBook-15:~$ 

```

---

### Post by Rick St. George on 2019-09-13
> **pcfan1234 said:**
> Remove resolvconf!
Ubuntu 18.04 uses systemd-resolve
This software manages the symlink of /etc/resolv.conf
The symlink should be the following
```
djkuhpisse@djkuhpisse-HP-ZBook-15:~$ ls -la /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Jan  6  2019 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
djkuhpisse@djkuhpisse-HP-ZBook-15:~$ 

```

Mine points to : /run/resolvconf/resolv.conf

Go figure????

But woke up this morning, turned on computer it has normal network access!  Go figure???

THANKS GUYS!

:popcorn:

---

### Post by pcfan1234 on 2019-09-13
I recommend removing resolvconf. You do not need it.

---

