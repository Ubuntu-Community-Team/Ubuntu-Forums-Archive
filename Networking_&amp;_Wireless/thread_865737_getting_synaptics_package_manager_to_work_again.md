---
title: "getting synaptics package manager to work again"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by reedatcentral on 2008-07-20
i switched to Ubuntu a couple of days ago, due mostly to the fact that i wanted to mostly get rid of windows.  my prior problems had been an intermittent internet connection, one which linksys nor my internet provider could solve.  this problem got so bad it would knock the other two computers on the network offline, and massively slow down my computer.  anyway when i made the switch, the problem went away, and i set off on installing applications i needed.  recently in the past two days i haven;'t been able to do much with the synaptic package manager, when previously it worked.  is there something i'm doing wrong?  or is it perhaps my ethernet card might be wearing out (which was my original theory to begin with when i encountered the problems in windows)?  here is the info on my computer:  
it is a dell dimension desktop, made in 2003.  I have an Intel p4 2.2 ghz processor, about 755 mb of ram, the Ethernet card is embedded, so i don't know what chipset it uses.  i have however had hardware failures with this computer on a couple ocassions so if that is the problem, no surprise here.  just wondering if this is a common problem,and if there is anything settings wise i should try.

---

### Post by tuxxy on 2008-07-20
Can you not install packages you mean?

---

### Post by reedatcentral on 2008-07-20
> **tuxxy said:**
> Can you not install packages you mean?

yes, i have problems with the part of install where it downloads files, hence why I'm wondering if it has anything to do with the problem i had in windows.

---

### Post by ad_267 on 2008-07-21
Can you go to applications - accessories - terminal and enter:
```
sudo apt-get install name_of_package_you_want_to_install
```
and then post the output here so we can see the error you are getting.

In my house there's a windows computer that has problems connecting to the internet and often things just won't connect for no apparent reason. This doesn't happen in Ubuntu on the same computer.

---

### Post by reedatcentral on 2008-07-21
here's the output i got back


reed@Amy:~$ sudo apt-get install scorched3d install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package install
reed@Amy:~$

---

### Post by ad_267 on 2008-07-21
Ok, that should just be:
```
sudo apt-get install scorched3d
```

Try that and post what you get. Also can you browse the internet fine? It's only installing packages that is a problem?

---

### Post by reedatcentral on 2008-07-21
ok here's what it returned this time
```
reed@Amy:~$ sudo apt-get install scorched3d
[sudo] password for reed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libavifile-0.7c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  scorched3d-data
Suggested packages:
  scorched3d-doc
The following NEW packages will be installed:
  scorched3d scorched3d-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.2MB of archives.
After this operation, 151MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com hardy/universe scorched3d-data 41.2dfsg-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com hardy/universe scorched3d 41.2dfsg-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/scorched3d/scorched3d-data_41.2dfsg-1_all.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/s/scorched3d/scorched3d_41.2dfsg-1_i386.deb  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I am able to browse the rest of the internet fine.  instant messenger works too.  it's just the packages that are a problem.

---

### Post by ad_267 on 2008-07-21
Ok open up synaptic package manager, click on settings - repositories and change where it says "Download from" to main server or another US server. Then click reload and try to install something.

---

### Post by reedatcentral on 2008-07-21
no it still returned an error when i clicked reload:

```
: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by reedatcentral on 2008-07-21
well, it's working, i went into the server menu and told it to select the best server.  in the Netherlands apparently but i don't care about speed so long as it works.  thanks much for the help.

---

