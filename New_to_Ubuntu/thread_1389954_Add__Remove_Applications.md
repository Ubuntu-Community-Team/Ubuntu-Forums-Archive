---
title: "Add / Remove Applications"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by beauty. proletariat on 2010-01-25
I installed add / remove applications because the ubuntu software centre did not give me functions to check which repo I'm downloading files from.

For some reason, it doesn't work. The details button is greyed out. I just switched to ubuntu from xubuntu because I didn't like the interface but now this happens lol. When I use iprimus's repo / server, it's all unmetered.

I've got a screenshot for you guys.

[img]http://ubuntuforums.org/attachment.php?attachmentid=144898&stc=1&d=1264404718[/img]

---

### Post by LuisGMarine on 2010-01-25
Try adding and removing from the command line and post the outputs here for people to go through them and try to help you out.  I like to use aptitude, you can use these commands from a terminal to add/remove programs.

```
sudo aptitude install package_name
```

```
sudo aptitude remove package_name
```

Also you said you installed Ubuntu from within Xubuntu, did you make sure you removed all the xubuntu packages?  For example if you were running xubuntu and decided that you wanted to start using Ubuntu (GNOME) you should of installed the package "ubuntu-desktop"  After that was done, you should of removed the xubuntu-desktop package once you are running Ubuntu of course.

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by beauty. proletariat on 2010-01-25
Umm lol I had an Xubuntu live CD and I reformatted my computer because I had problems with it. It's got clean install ubuntu now.

I did ```
sudo aptitude install abiword
``` and this is what I got. Quite confusing to me >.<

```
proletariat@proletariat-ubuntu:~$ sudo aptitude install abiword
[sudo] password for proletariat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  abiword abiword-common{a} abiword-help{a} abiword-plugin-grammar{a} 
  abiword-plugin-mathview{a} libaiksaurus-1.2-0c2a{a} 
  libaiksaurus-1.2-data{a} libaiksaurusgtk-1.2-0c2a{a} libgdome2-0{a} 
  libgdome2-cpp-smart0c2a{a} libgnomecups1.0-1{a} libgnomeprint2.2-0{a} 
  libgnomeprint2.2-data{a} libgnomeprintui2.2-0{a} 
  libgnomeprintui2.2-common{a} libgtkmathview0c2a{a} liblink-grammar4{a} 
  libots0{a} libt1-5{a} libwv-1.2-3{a} link-grammar-dictionaries-en{a} 
The following packages will be REMOVED:
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
The following partially installed packages will be configured:
  ttf-mscorefonts-installer 
0 packages upgraded, 21 newly installed, 2 to remove and 0 not upgraded.
Need to get 9,208kB of archives. After unpacking 48.3MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://mirror.iprimus.com.au karmic/main libaiksaurus-1.2-data 1.2.1+dev-0.12-6 [318kB]
Get:2 http://mirror.iprimus.com.au karmic/main libaiksaurus-1.2-0c2a 1.2.1+dev-0.12-6 [24.0kB]
Get:3 http://mirror.iprimus.com.au karmic/main libaiksaurusgtk-1.2-0c2a 1.2.1+dev-0.12-6 [32.3kB]
Get:4 http://mirror.iprimus.com.au karmic/main libgnomecups1.0-1 0.2.3-3build1 [32.4kB]
Get:5 http://mirror.iprimus.com.au karmic/main libgnomeprint2.2-data 2.18.6-1build1 [46.9kB]
Get:6 http://mirror.iprimus.com.au karmic/main libgnomeprint2.2-0 2.18.6-1build1 [237kB]
Get:7 http://mirror.iprimus.com.au karmic/main libgnomeprintui2.2-common 2.18.4-1 [7,372B]
Get:8 http://mirror.iprimus.com.au karmic/main libgnomeprintui2.2-0 2.18.4-1 [118kB]
Get:9 http://mirror.iprimus.com.au karmic/main libots0 0.5.0-2 [39.3kB]         
Get:10 http://mirror.iprimus.com.au karmic/main libwv-1.2-3 1.2.4-2ubuntu2 [147kB]
Get:11 http://mirror.iprimus.com.au karmic/main abiword-common 2.6.8-5ubuntu2 [1,993kB]
Get:12 http://mirror.iprimus.com.au karmic/main abiword 2.6.8-5ubuntu2 [3,021kB]
Get:13 http://mirror.iprimus.com.au karmic/main abiword-help 2.6.8-5ubuntu2 [1,254kB]
Get:14 http://mirror.iprimus.com.au karmic/main link-grammar-dictionaries-en 4.3.9-2ubuntu1 [374kB]
Get:15 http://mirror.iprimus.com.au karmic/main liblink-grammar4 4.3.9-2ubuntu1 [107kB]
Get:16 http://mirror.iprimus.com.au karmic/main abiword-plugin-grammar 2.6.8-5ubuntu2 [14.7kB]
Get:17 http://mirror.iprimus.com.au karmic/main libgdome2-0 0.8.1+debian-3 [105kB]
Get:18 http://mirror.iprimus.com.au karmic/main libgdome2-cpp-smart0c2a 0.2.6-3build1 [47.1kB]
Get:19 http://mirror.iprimus.com.au karmic/main libt1-5 5.1.2-3 [170kB]         
Get:20 http://mirror.iprimus.com.au karmic/main libgtkmathview0c2a 0.8.0-3ubuntu2 [1,007kB]
Get:21 http://mirror.iprimus.com.au karmic/main abiword-plugin-mathview 2.6.8-5ubuntu2 [115kB]
Fetched 9,208kB in 55s (166kB/s)                                                
(Reading database ... 139473 files and directories currently installed.)
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
Selecting previously deselected package libaiksaurus-1.2-data.
(Reading database ... 121956 files and directories currently installed.)
Unpacking libaiksaurus-1.2-data (from .../libaiksaurus-1.2-data_1.2.1+dev-0.12-6_all.deb) ...
Selecting previously deselected package libaiksaurus-1.2-0c2a.
Unpacking libaiksaurus-1.2-0c2a (from .../libaiksaurus-1.2-0c2a_1.2.1+dev-0.12-6_amd64.deb) ...
Selecting previously deselected package libaiksaurusgtk-1.2-0c2a.
Unpacking libaiksaurusgtk-1.2-0c2a (from .../libaiksaurusgtk-1.2-0c2a_1.2.1+dev-0.12-6_amd64.deb) ...
Selecting previously deselected package libgnomecups1.0-1.
Unpacking libgnomecups1.0-1 (from .../libgnomecups1.0-1_0.2.3-3build1_amd64.deb) ...
Selecting previously deselected package libgnomeprint2.2-data.
Unpacking libgnomeprint2.2-data (from .../libgnomeprint2.2-data_2.18.6-1build1_all.deb) ...
Selecting previously deselected package libgnomeprint2.2-0.
Unpacking libgnomeprint2.2-0 (from .../libgnomeprint2.2-0_2.18.6-1build1_amd64.deb) ...
Selecting previously deselected package libgnomeprintui2.2-common.
Unpacking libgnomeprintui2.2-common (from .../libgnomeprintui2.2-common_2.18.4-1_all.deb) ...
Selecting previously deselected package libgnomeprintui2.2-0.
Unpacking libgnomeprintui2.2-0 (from .../libgnomeprintui2.2-0_2.18.4-1_amd64.deb) ...
Selecting previously deselected package libots0.
Unpacking libots0 (from .../libots0_0.5.0-2_amd64.deb) ...
Selecting previously deselected package libwv-1.2-3.
Unpacking libwv-1.2-3 (from .../libwv-1.2-3_1.2.4-2ubuntu2_amd64.deb) ...
Selecting previously deselected package abiword-common.
Unpacking abiword-common (from .../abiword-common_2.6.8-5ubuntu2_all.deb) ...
Selecting previously deselected package abiword.
Unpacking abiword (from .../abiword_2.6.8-5ubuntu2_amd64.deb) ...
Selecting previously deselected package abiword-help.
Unpacking abiword-help (from .../abiword-help_2.6.8-5ubuntu2_all.deb) ...
Selecting previously deselected package link-grammar-dictionaries-en.
Unpacking link-grammar-dictionaries-en (from .../link-grammar-dictionaries-en_4.3.9-2ubuntu1_all.deb) ...
Selecting previously deselected package liblink-grammar4.
Unpacking liblink-grammar4 (from .../liblink-grammar4_4.3.9-2ubuntu1_amd64.deb) ...
Selecting previously deselected package abiword-plugin-grammar.
Unpacking abiword-plugin-grammar (from .../abiword-plugin-grammar_2.6.8-5ubuntu2_amd64.deb) ...
Selecting previously deselected package libgdome2-0.
Unpacking libgdome2-0 (from .../libgdome2-0_0.8.1+debian-3_amd64.deb) ...
Selecting previously deselected package libgdome2-cpp-smart0c2a.
Unpacking libgdome2-cpp-smart0c2a (from .../libgdome2-cpp-smart0c2a_0.2.6-3build1_amd64.deb) ...
Selecting previously deselected package libt1-5.
Unpacking libt1-5 (from .../libt1-5_5.1.2-3_amd64.deb) ...
Selecting previously deselected package libgtkmathview0c2a.
Unpacking libgtkmathview0c2a (from .../libgtkmathview0c2a_0.8.0-3ubuntu2_amd64.deb) ...
Selecting previously deselected package abiword-plugin-mathview.
Unpacking abiword-plugin-mathview (from .../abiword-plugin-mathview_2.6.8-5ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-01-25 18:54:00--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-25 18:54:10--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2010-01-25 18:54:20--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2010-01-25 18:54:30--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2010-01-25 18:54:40--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2010-01-25 18:54:50--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2010-01-25 18:55:00--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2010-01-25 18:55:10--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2010-01-25 18:55:20--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2010-01-25 18:55:30--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2010-01-25 18:55:40--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2010-01-25 18:55:50--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libaiksaurus-1.2-data (1.2.1+dev-0.12-6) ...
Setting up libaiksaurus-1.2-0c2a (1.2.1+dev-0.12-6) ...

Setting up libaiksaurusgtk-1.2-0c2a (1.2.1+dev-0.12-6) ...

Setting up libgnomecups1.0-1 (0.2.3-3build1) ...

Setting up libgnomeprint2.2-data (2.18.6-1build1) ...
Setting up libgnomeprint2.2-0 (2.18.6-1build1) ...

Setting up libgnomeprintui2.2-common (2.18.4-1) ...
Setting up libgnomeprintui2.2-0 (2.18.4-1) ...

Setting up libots0 (0.5.0-2) ...

Setting up libwv-1.2-3 (1.2.4-2ubuntu2) ...

Setting up abiword-common (2.6.8-5ubuntu2) ...
Setting up abiword (2.6.8-5ubuntu2) ...

Setting up abiword-help (2.6.8-5ubuntu2) ...
Setting up link-grammar-dictionaries-en (4.3.9-2ubuntu1) ...
Setting up liblink-grammar4 (4.3.9-2ubuntu1) ...

Setting up abiword-plugin-grammar (2.6.8-5ubuntu2) ...
Setting up libgdome2-0 (0.8.1+debian-3) ...

Setting up libgdome2-cpp-smart0c2a (0.2.6-3build1) ...

Setting up libt1-5 (5.1.2-3) ...

Setting up libgtkmathview0c2a (0.8.0-3ubuntu2) ...

Setting up abiword-plugin-mathview (2.6.8-5ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-01-25 18:56:04--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2010-01-25 18:56:14--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `switch.dl.sourceforge.net'
--2010-01-25 18:56:24--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2010-01-25 18:56:34--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2010-01-25 18:56:44--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2010-01-25 18:56:54--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2010-01-25 18:57:04--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2010-01-25 18:57:14--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2010-01-25 18:57:24--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2010-01-25 18:57:34--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2010-01-25 18:57:44--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2010-01-25 18:57:54--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internap.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

I'm installing exaile through aptitude at the moment, and it seems its trying to download the fonts again. I'll post logs of the uninstall when i get rid of rythmbox.

---

### Post by LuisGMarine on 2010-01-25
post me the contents of this command:

```
sudo gedit /etc/apt/sources.list
```

looks like you have some source on there for the msfonts that is causing all these problems, hopefully we can remove it.

---

### Post by beauty. proletariat on 2010-01-25
oh lol I was messing with it to add my isp's server before >.>
```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.iprimus.com.au/ubuntu/ karmic main restricted
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.iprimus.com.au/ubuntu/ karmic-updates main restricted
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.iprimus.com.au/ubuntu/ karmic universe
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic universe
deb http://mirror.iprimus.com.au/ubuntu/ karmic-updates universe
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.iprimus.com.au/ubuntu/ karmic multiverse
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic multiverse
deb http://mirror.iprimus.com.au/ubuntu/ karmic-updates multiverse
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.iprimus.com.au/ubuntu/ karmic-security main restricted
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-security main restricted
deb http://mirror.iprimus.com.au/ubuntu/ karmic-security universe
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-security universe
deb http://mirror.iprimus.com.au/ubuntu/ karmic-security multiverse
deb-src http://mirror.iprimus.com.au/ubuntu/ karmic-security multiverse
```

---

### Post by LuisGMarine on 2010-01-25
weird everything looks good.  Try this, this will remove the mscorefonts package since it seems to be the root of our problems.
```

sudo aptitude purge ttf-mscorefonts-installer
```

then run these two following commands, this will update our sources and install any updates that are needed, then you can go ahead and run your command to install abiword.

```
sudo aptitude update
```
```

sudo aptitude safe-upgrade
```

---

### Post by beauty. proletariat on 2010-01-25
Okay.

Thank you heaps heaaapss !
I only realised the problem was there after you told me to give you those logs. I'm going to use Synaptic instead of Add/Remove now.

---

### Post by D3V11 on 2010-01-25
> 
sudo gedit

avoid using sudo to open graphical applications as it may cause file corruption or rewrite permissions. instead use gksudo.

---

