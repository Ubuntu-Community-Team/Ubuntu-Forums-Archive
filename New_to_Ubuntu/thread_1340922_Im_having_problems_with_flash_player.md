---
title: "Im having problems with flash player :/"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by got2loveme6 on 2009-11-29
I had it installed just fine a week or so ago but had to reboot my computer. Now it won't work. I tried to uninstall and re install the plugin but this is what comes up 

                         can someone please help! its saying 1 newly installed and 17 not upgraded :/ im very confused...im running on 8.04 and im not sure if i had flash 10 or 9 but i would like 9 



any help would be greatly appreciated 
 



 
lateecia@lateecia:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for lateecia:
Reading package lists… Done
Building dependency tree
Reading state information… Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages …
Selecting previously deselected package flashplugin-nonfree.
(Reading database … 96171 files and directories currently installed.)
Unpacking flashplugin-nonfree (from …/flashplugin-nonfree_9.0.152.0ubuntu0netbook1_lpia.deb) …
Setting up flashplugin-nonfree (9.0.152.0ubuntu0netbook1) …
Downloading…
–02:25:01–  [http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz](http://download.macromedia.com/pub/flashplayer/installers/current/9/install_flash_player_9.tar.gz)
           => `./install_flash_player_9.tar.gz’
Resolving download.macromedia.com… 96.7.99.191
Connecting to download.macromedia.com|96.7.99.191|:80… connected.
HTTP request sent, awaiting response… 200 OK
Length: 3,057,910 (2.9M) [application/x-gzip]
     0K ………. ………. ………. ………. ……….  1%  335.38 KB/s
   50K ………. ………. ………. ………. ……….  3%  448.86 KB/s
  100K ………. ………. ………. ………. ……….  5%  195.57 KB/s
  150K ………. ………. ………. ………. ……….  6%  481.89 KB/s
  200K ………. ………. ………. ………. ……….  8%  374.33 KB/s
  250K ………. ………. ………. ………. ………. 10%  218.33 KB/s
  300K ………. ………. ………. ………. ………. 11%  346.86 KB/s
  350K ………. ………. ………. ………. ………. 13%  244.65 KB/s
  400K ………. ………. ………. ………. ………. 15%  140.81 KB/s
  450K ………. ………. ………. ………. ………. 16%  142.88 KB/s
  500K ………. ………. ………. ………. ………. 18%  184.22 KB/s
  550K ………. ………. ………. ………. ………. 20%  189.76 KB/s
  600K ………. ………. ………. ………. ………. 21%  184.24 KB/s
  650K ………. ………. ………. ………. ………. 23%  198.47 KB/s
  700K ………. ………. ………. ………. ………. 25%  179.25 KB/s
  750K ………. ………. ………. ………. ………. 26%  176.31 KB/s
  800K ………. ………. ………. ………. ………. 28%  204.67 KB/s
  850K ………. ………. ………. ………. ………. 30%   47.19 KB/s
  900K ………. ………. ………. ………. ………. 31%   13.35 MB/s
  950K ………. ………. ………. ………. ………. 33%   12.69 MB/s
 1000K ………. ………. ………. ………. ………. 35%  350.06 KB/s
 1050K ………. ………. ………. ………. ………. 36%  303.14 KB/s
 1100K ………. ………. ………. ………. ………. 38%  268.23 KB/s
 1150K ………. ………. ………. ………. ………. 40%  213.71 KB/s
 1200K ………. ………. ………. ………. ………. 41%  204.27 KB/s
 1250K ………. ………. ………. ………. ………. 43%  231.63 KB/s
 1300K ………. ………. ………. ………. ………. 45%  163.45 KB/s
 1350K ………. ………. ………. ………. ………. 46%  130.52 KB/s
 1400K ………. ………. ………. ………. ………. 48%  154.30 KB/s
 1450K ………. ………. ………. ………. ………. 50%  197.84 KB/s
 1500K ………. ………. ………. ………. ………. 51%  216.96 KB/s
 1550K ………. ………. ………. ………. ………. 53%  272.06 KB/s
 1600K ………. ………. ………. ………. ………. 55%  275.40 KB/s
 1650K ………. ………. ………. ………. ………. 56%  253.95 KB/s
 1700K ………. ………. ………. ………. ………. 58%  262.29 KB/s
 1750K ………. ………. ………. ………. ………. 60%  165.65 KB/s
 1800K ………. ………. ………. ………. ………. 61%  145.56 KB/s
 1850K ………. ………. ………. ………. ………. 63%  124.03 KB/s
 1900K ………. ………. ………. ………. ………. 65%  155.43 KB/s
 1950K ………. ………. ………. ………. ………. 66%  122.26 KB/s
 2000K ………. ………. ………. ………. ………. 68%  128.01 KB/s
 2050K ………. ………. ………. ………. ………. 70%   90.20 KB/s
 2100K ………. ………. ………. ………. ………. 71%  162.47 KB/s
 2150K ………. ………. ………. ………. ………. 73%  141.94 KB/s
 2200K ………. ………. ………. ………. ………. 75%  177.65 KB/s
 2250K ………. ………. ………. ………. ………. 77%  164.52 KB/s
 2300K ………. ………. ………. ………. ………. 78%   98.57 KB/s
 2350K ………. ………. ………. ………. ………. 80%  169.52 KB/s
 2400K ………. ………. ………. ………. ………. 82%  209.27 KB/s
 2450K ………. ………. ………. ………. ………. 83%  141.59 KB/s
 2500K ………. ………. ………. ………. ………. 85%  141.67 KB/s
 2550K ………. ………. ………. ………. ………. 87%  198.16 KB/s
 2600K ………. ………. ………. ………. ………. 88%  232.14 KB/s
 2650K ………. ………. ………. ………. ………. 90%  239.30 KB/s
 2700K ………. ………. ………. ………. ………. 92%  214.76 KB/s
 2750K ………. ………. ………. ………. ………. 93%  232.81 KB/s
 2800K ………. ………. ………. ………. ………. 95%  294.48 KB/s
 2850K ………. ………. ………. ………. ………. 97%  332.89 KB/s
 2900K ………. ………. ………. ………. ………. 98%  297.02 KB/s
 2950K ………. ………. ………. ……               100%  222.16 KB/s
 02:25:17 (187.83 KB/s) – `./install_flash_player_9.tar.gz’ saved [3057910/3057910]
 Download done.
md5sum mismatch install_flash_player_9.tar.gz
The Flash plugin is NOT installed.
 lateecia@lateecia:~$

---

### Post by heyho on 2009-11-29
I've never installed flash on it's own, but have always used:
> 
sudo apt-get install ubuntu-restricted-extras

make sure you have also carried out these commands beforehand.

> sudo apt-get update

then

> sudo apt-get upgrade.

---

### Post by Zoot7 on 2009-11-29
You might want to give the .deb package flash player off adobe's website a shot.
[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

I've been hearing that the one in the repos is apparently broken.

---

### Post by 73ckn797 on 2009-11-29
Have you followed the Sticky for Flash in the 64bit forum? It works just fine.

---

### Post by ikt on 2009-11-29
> **got2loveme6 said:**
> any help would be greatly appreciated 
 
(from …/flashplugin-nonfree_9.0.152.0ubuntu0netbook1_[SIZE="5"]lpia[/SIZE].deb)

Try downloading the .deb from the adobe flash website and running the following command as posted in the following post:

[http://ubuntuforums.org/showpost.php?p=7005551&postcount=3](http://ubuntuforums.org/showpost.php?p=7005551&postcount=3)

```
sudo dpkg -i --force-architecture install_flash_player_10_linux.deb
```

---

