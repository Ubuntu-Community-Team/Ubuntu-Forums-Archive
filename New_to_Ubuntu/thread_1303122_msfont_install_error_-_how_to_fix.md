---
title: "msfont install error - how to fix"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by powel212 on 2009-10-27
I am installing jaunty on an older celeron based system. Installing language support and ubuntu -restricted-extras keep getting error core-msfonts not installing. Have tried Main server as well as 2 different local servers but keep getting the error.

How to get these core fonts to install.

Have installed Jaunty over a hundred times, first time encountering this problem.

What's up?

Any help is appreciated

Powel

---

### Post by Buuntu on 2009-10-27
```
sudo apt-get install msttcorefonts
```

---

### Post by powel212 on 2009-10-27
No Dice.

check all the  not found errors.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract ttf-liberation ttf-mscorefonts-installer
The following NEW packages will be installed:
  cabextract msttcorefonts ttf-liberation ttf-mscorefonts-installer
0 upgraded, 4 newly installed, 0 to remove and 254 not upgraded.
Need to get 1101kB of archives.
After this operation, 2159kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://debian.nctu.edu.tw jaunty/universe cabextract 1.2-3 [55.8kB]
Get:2 http://debian.nctu.edu.tw jaunty/multiverse ttf-mscorefonts-installer 2.6 [32.2kB]
Get:3 http://debian.nctu.edu.tw jaunty/multiverse msttcorefonts 2.6 [8030B]
Get:4 http://debian.nctu.edu.tw jaunty/main ttf-liberation 1.04.93-1 [1005kB]
Fetched 1101kB in 1s (950kB/s)          
Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 101931 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.2-3_amd64.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_2.6_all.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_2.6_all.deb) ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from .../ttf-liberation_1.04.93-1_all.deb) ...
Processing triggers for man-db ...
Setting up cabextract (1.2-3) ...
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-10-28 10:15:54--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:55--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-28 10:15:56--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      715K/s   in 0.3s    

2009-10-28 10:15:56 (715 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-10-28 10:15:56--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:57--  http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2009-10-28 10:15:58--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176      646K/s   in 0.3s    

2009-10-28 10:15:58 (646 KB/s) - `./arialb32.exe' saved [168176/168176]

--2009-10-28 10:15:58--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:59--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:00--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:05--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2009-10-28 10:16:06--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:06--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:12--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2009-10-28 10:16:13--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:13--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:18--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2009-10-28 10:16:19--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:20--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:25--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=jaist.dl.sourceforge.net [following]
--2009-10-28 10:16:26--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=jaist.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:26--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:32--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=nchc.dl.sourceforge.net [following]
--2009-10-28 10:16:32--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:32--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:37--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:47--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:48--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208      813K/s   in 0.7s    

2009-10-28 10:16:49 (813 KB/s) - `./arial32.exe' saved [554208/554208]

--2009-10-28 10:16:49--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:51--  http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2009-10-28 10:16:51--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008      856K/s   in 0.3s    

2009-10-28 10:16:52 (856 KB/s) - `./comic32.exe' saved [246008/246008]

--2009-10-28 10:16:52--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:58--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:16:59--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:04--  http://internode.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2009-10-28 10:17:05--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:06--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:11--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2009-10-28 10:17:12--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:13--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:18--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2009-10-28 10:17:19--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:25--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:30--  http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=kent.dl.sourceforge.net [following]
--2009-10-28 10:17:31--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:31--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:36--  http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=internap.dl.sourceforge.net [following]
--2009-10-28 10:17:37--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=internap.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:38--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:43--  http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2009-10-28 10:17:44--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:45--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: library not compiled to support large files.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: library not compiled to support large files.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-liberation (1.04.93-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Doesn't matter what server I use.

The other curious thing is:

```
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
```

.exe files??? really???


How to get around this trouble?

Powel

---

### Post by Buuntu on 2009-10-28
Hmm...
Maybe this will fix it:
```
sudo apt-get update
sudo apt-get install -f
```If that hasn't fixed it, type:
```
sudo dpkg --configure -a
```

---

### Post by sandyd on 2009-10-28
> **powel212 said:**
> No Dice.

check all the  not found errors.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract ttf-liberation ttf-mscorefonts-installer
The following NEW packages will be installed:
  cabextract msttcorefonts ttf-liberation ttf-mscorefonts-installer
0 upgraded, 4 newly installed, 0 to remove and 254 not upgraded.
Need to get 1101kB of archives.
After this operation, 2159kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://debian.nctu.edu.tw jaunty/universe cabextract 1.2-3 [55.8kB]
Get:2 http://debian.nctu.edu.tw jaunty/multiverse ttf-mscorefonts-installer 2.6 [32.2kB]
Get:3 http://debian.nctu.edu.tw jaunty/multiverse msttcorefonts 2.6 [8030B]
Get:4 http://debian.nctu.edu.tw jaunty/main ttf-liberation 1.04.93-1 [1005kB]
Fetched 1101kB in 1s (950kB/s)          
Preconfiguring packages ...
Selecting previously deselected package cabextract.
(Reading database ... 101931 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.2-3_amd64.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_2.6_all.deb) ...
Selecting previously deselected package msttcorefonts.
Unpacking msttcorefonts (from .../msttcorefonts_2.6_all.deb) ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from .../ttf-liberation_1.04.93-1_all.deb) ...
Processing triggers for man-db ...
Setting up cabextract (1.2-3) ...
Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-10-28 10:15:54--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:55--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-28 10:15:56--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      715K/s   in 0.3s    

2009-10-28 10:15:56 (715 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-10-28 10:15:56--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:57--  http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2009-10-28 10:15:58--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176      646K/s   in 0.3s    

2009-10-28 10:15:58 (646 KB/s) - `./arialb32.exe' saved [168176/168176]

--2009-10-28 10:15:58--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--2009-10-28 10:15:59--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:00--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:05--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2009-10-28 10:16:06--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:06--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:12--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2009-10-28 10:16:13--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:13--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:18--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2009-10-28 10:16:19--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:20--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:25--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=jaist.dl.sourceforge.net [following]
--2009-10-28 10:16:26--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=jaist.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:26--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:32--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=nchc.dl.sourceforge.net [following]
--2009-10-28 10:16:32--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:32--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:16:37--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:47--  http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2009-10-28 10:16:48--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208      813K/s   in 0.7s    

2009-10-28 10:16:49 (813 KB/s) - `./arial32.exe' saved [554208/554208]

--2009-10-28 10:16:49--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:51--  http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2009-10-28 10:16:51--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008      856K/s   in 0.3s    

2009-10-28 10:16:52 (856 KB/s) - `./comic32.exe' saved [246008/246008]

--2009-10-28 10:16:52--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-28 10:16:58--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:16:59--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:04--  http://internode.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2009-10-28 10:17:05--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:06--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:11--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2009-10-28 10:17:12--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:13--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:18--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2009-10-28 10:17:19--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:25--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:30--  http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=kent.dl.sourceforge.net [following]
--2009-10-28 10:17:31--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:31--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:36--  http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=internap.dl.sourceforge.net [following]
--2009-10-28 10:17:37--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=internap.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:38--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

--2009-10-28 10:17:43--  http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2009-10-28 10:17:44--  http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2009-10-28 10:17:45--  http://ncu.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving ncu.dl.sourceforge.net... 140.115.17.45
Connecting to ncu.dl.sourceforge.net|140.115.17.45|:80... failed: Connection timed out.
Giving up.

andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: library not compiled to support large files.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: library not compiled to support large files.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of msttcorefonts:
 msttcorefonts depends on ttf-mscorefonts-installer; however:
  Package ttf-mscorefonts-installer is not configured yet.
dpkg: error processing msttcorefonts (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-liberation (1.04.93-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Errors were encountered while processing:
 ttf-mscorefonts-installer
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Doesn't matter what server I use.

The other curious thing is:

```
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
```**.exe files??? really???**


How to get around this trouble?

Powel
the fonts are extracted from the exe files using cabextract.

---

### Post by ngtechie on 2009-11-01
Not working for me either...

> **Buuntu said:**
> Hmm...
Maybe this will fix it:
```
sudo apt-get update
sudo apt-get install -f
```If that hasn't fixed it, type:
```
sudo dpkg --configure -a
```

I am having the same problem as well... So far 40% of the software/themes have tried downloading these fonts and this has happened. I did complete reinstall of 9.10 after using jaunty for several months. LOVE ME SOME LINUX. 

Fedora 11 - My Laptop
Ubuntu 9.10/ Windows XP Ultimate - PC
Ubuntu 9.04 - Fiancé's Laptop

---

### Post by shafin on 2009-11-01
I just uninstalled mscorefonts installer package and copied the fonts to my ~/.fonts folder. That solved it for now.

---

### Post by ahmadz1991 on 2009-11-02
shafin.. where did u get the fonts,,, plzzzz help

---

### Post by twotool on 2009-11-05
@ Shafin,
Please help us by telling how did that.

---

### Post by mrboojive on 2009-11-05
It looks like the error was that it failed to download one of the fonts for some reason. However as far as I can tell, the file it was trying to download is working right now. Try reinstalling ttf-mscorefonts-installer and see if it works now.

---

### Post by worm94 on 2009-11-05
This isn't the easiest (or quickest or most elegant for that matter) way to accomplish this, but I was able to manually enable Microsoft's core fonts in Karmic. I was getting the same error about the server timeout when trying to do this through the command line, so I went and manually downloaded each file from [here]("http://sourceforge.net/projects/corefonts/files/the%20fonts/final/") and proceeded to extract the files inside each .exe using the archive manager. Next, I deleted every file from every newly created folder, except those with .TTF extension. Then, I copied said folders, each one containing it's respective .TTF files, to /usr/share/fonts/truetype and voilá, the fonts now (after a restart) appear available at openoffice, system appearance settings and even as the default font for firefox. So, I hope that this helps someone. As I said at the beginning, it isn't the quickest or easiest way to install the fonts, but as far as I know, it works =)

---

### Post by narinarinari on 2009-11-06
Hi I just registered to let you guys know where is the solution to this problem.
NovaSci explains here: [http://ubuntuforums.org/showthread.php?t=1310473](http://ubuntuforums.org/showthread.php?t=1310473) that the problem is the install script and he also posts a solution that worked wonderful.

---------------------------------------------------------------------------------------------

Had the same problem and after looking at a number of forums and the behavior during install it seems that the install script is accessing the wrong sourceforge address. I made the following changes to

/var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

Add

MYURL="http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/"
MYMIRROR="?use_mirror=internode"

Just after

# Base URL for Microsoft fonts
# Can be more than one to try, but here we just use SF.net's redirection,
# which will work in most cases. The others serve as fallbacks to retry.

Then change (line 150 I believe) from

if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

to

if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $MYURL$ff$MYMIRROR ; then

Then go back to Synaptic and mark ttf-mscorefonts-installer for reinstallation. Click apply etc.

This worked for me. Although you might want to change the mirror.

Hope this is on some help

---------------------------------------------------------------------------------------------

props to NovaSci

---

### Post by lei75jkt on 2009-11-11
Thanks narinarinari,

after countless searching what cause this error, including doing some fix in DNS karmic bug, i have finally solved mscorefonts problem.

Thanks to you :D

---

