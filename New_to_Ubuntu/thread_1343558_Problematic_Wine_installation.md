---
title: "Problematic Wine installation"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by tgrillot87 on 2009-12-02
So I'm a complete beginner when it comes to linux. I really don't have any idea what I'm doing. But I recently started playing around with it on my laptop, and so far everything has gone swimmingly. But today I tried to install Wine through the Ubuntu software center, and halfway through the installation I got an error message telling me that the installation or removal of a software package had failed. The "remove" link in the software center was grayed out so I went to the uninstall link for Wine in the applications menu and the uninstaller seemed to be broken. I went back to the software center and the "remove" link was active so I clicked on it. Once again, it got halfway through the operation before giving me the same error message. So my question is how do I uninstall the software, and how do I then reinstall it so it works?

---

### Post by Dullstar on 2009-12-02
Because of the way Linux handles things, I believe it should work to figure out where whatever files were installed were and then delete them.  The only problem is, I have no idea where they are stored.

---

### Post by swoody on 2009-12-02
Try opening a terminal (Applications>Accessories>Terminal) and entering:
```
sudo apt-get install -f
```

The 'sudo' command will prompt you for your password. If you are unfamiliar with this, it will look as if you are not typing anything into the terminal. *This is normal* It is a security feature of Ubuntu. Simply type in your password as normal, and then hit 'Enter'

If this works successfully, you'll have Wine installed. If it fails or gives you any errors as output, please post them here.

---

### Post by tgrillot87 on 2009-12-02
The code resulted in this output:

```
trav@trav-laptop:~$ sudo apt-get install -f
[sudo] password for trav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a linux-headers-2.6.31-14 kdelibs-data libxerces-c28 docbook-xsl
  liblualib50 libxalan110 libmysqlclient15off ruby1.8 librecode0 ruby
  kdelibs5-data libavahi-qt3-1 docbook-xsl-doc-html libqt3-mt liblua50
  libruby1.8 linux-headers-2.6.31-14-generic libaudio2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-02 15:34:08--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-02 15:34:18--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--2009-12-02 15:34:19--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-02 15:34:29--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-02 15:34:39--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-12-02 15:34:49--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net [following]
--2009-12-02 15:34:49--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-02 15:34:59--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-02 15:35:09--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net [following]
--2009-12-02 15:35:10--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-02 15:35:20--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-12-02 15:35:30--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-12-02 15:35:40--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-12-02 15:35:50--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-02 15:36:00--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
trav@trav-laptop:~$ 
```

Not sure what any of this means except that it didn't work.

---

### Post by swoody on 2009-12-03
Ah yes, that is the 'ttf-mscorefonts-installer' package that's giving you an issue. I have had the same problem recently when I installed Wine. I'm not sure how to tale care of this permanently, but as a temporary solution, you could remove the package until this issue has been resolved. Just open a terminal, and run:
```
sudo apt-get purge ttf-mscorefonts-installer
```

I'm not too sure which/how many apps rely on this package when you run them in Wine, but if you encounter any issues with fonts using Wine, you'll know where the issue is coming from.

I will look into this a bit more, and see if I can't find a better solution to getting the MS fonts installed.

---

### Post by swoody on 2009-12-03
Well, this does seem to be quite a common bug, and there are a number of solutions to get it working again. After running the command I posted above, you can follow this how-to where this fellow has created a script that downloads and installs the MS fonts:
[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

You can also try to setup persistent DNS caching, which seems to work for some people with this issue:
[http://ubuntuforums.org/showpost.php?p=7902019&postcount=33](http://ubuntuforums.org/showpost.php?p=7902019&postcount=33)

Give those a shot, and let us know of any success or if you encounter any other errors :)

---

### Post by tgrillot87 on 2009-12-03
That got it working. Thanks for your help.

---

### Post by swoody on 2009-12-03
It's no problem at all :)

Also, be sure to mark your threads as [SOLVED] when your issue has been fixed. It will help keep the forums in order, and will also help out future users who may have the same issue. Simply go to the top right of this page, and click on 'Thread Tools' and then select 'Mark as solved'

Thanks!

---

