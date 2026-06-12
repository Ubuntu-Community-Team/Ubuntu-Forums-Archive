---
title: "Strange Download Issue"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by BHelts on 2007-05-04
I am having a strange download issue on a pretty new install of Feisty.  My networking is working fine, I have internet access and I can ping forever.  But when I am downloading something, everything from Firefox themes to repo updates, it sometimes hangs.  I'm new to linux, but it seems like there is a buffer problem or a temp folder is getting full, because the download will go very fast until it bombs out, then nothing.  Just hangs.  Any ideas how to troubleshoot this small issue?  Thank you in advance for your help.

---

### Post by taurus on 2007-05-04
If you think your harddrive is running out of space, let's have a look at the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
df -h
```

Otherwise, post the output of these two commands here.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by BHelts on 2007-05-04
Thanks for your help Taurus
```
sudo aptitude update
Get:1 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/universe Sources
Hit http://archive.ubuntu.com feisty/multiverse Packages
Hit http://archive.ubuntu.com feisty/multiverse Sources
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/main Sources
Hit http://archive.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/universe Sources
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done


```

That is ok.

```
sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

Also ok.

But....
```
sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gdesklets-data
Recommended packages:
  hddtemp xmms python-xmms libwww-search-perl python-soappy python-imaging
  python-feedparser
The following NEW packages will be installed:
  gdesklets gdesklets-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3931kB/4409kB of archives.
After unpacking 15.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com feisty/universe gdesklets-data 0.35.6-1 [3931kB]
Err http://archive.ubuntu.com feisty/universe gdesklets-data 0.35.6-1          
  Connection timed out [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/g/gdesklets-data/gdesklets-data_0.35.6-1_all.deb  Connection timed out [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Does this help?

---

### Post by taurus on 2007-05-04
Any chance you are using proxy?

---

### Post by BHelts on 2007-05-04
I am not using proxy.

---

### Post by taurus on 2007-05-04
What does /etc/apt/apt.conf say?

```
cat /etc/apt/apt.conf
```
Or what happens when you run this command from a terminal?

```
ping 91.189.88.31 80
```

---

### Post by BHelts on 2007-05-04
OK.
i get:
```
:~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory

```

and when i ping that IP i get 100% loss on port 80, but 100% received without the port designation.

---

### Post by BHelts on 2007-05-07
Any new ideas?

---

### Post by insert_name_here on 2007-05-10
Sounds like you're behind a proxy - are you at some sort of school/workplace that censors your internetz so you don't access myspace during your lunchbreak?

Try accessing the URL in firefox.  If it loads fine, I don't know what the problem is.  If you get some sort of block screen, such as "Websense has blocked this page.  Category: Uncategorized" then the proxy is the problem.  I do get this block page.


If you take your computer outside the network, like to your house, it should work correctly.  

Or, you might be able to change the link in your sources.list to deb [b][ftp://[b]archive.ubuntu.com](ftp://[b]archive.ubuntu.com) feisty/universe or whatever.

---

### Post by BHelts on 2007-05-10
I work as an System's Administrator.  I support exclusively Windows.  Servers and Workstations.  But I currently use personally only Linux.  I am 100% sure I am not using proxy and I also know that if I wanted to go to myspace on my lunch break, I am certainly able to.  There is nothing blocking my packets, in or out.  I can use bittorrent, i stream audio all day, video hasn't been a problem, and web surfing is flawless.  This is some kind of weird problem that I just don't yet know enough about to fix.

---

