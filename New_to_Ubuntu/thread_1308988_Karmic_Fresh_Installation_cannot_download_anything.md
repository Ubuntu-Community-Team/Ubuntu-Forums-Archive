---
title: "Karmic Fresh Installation: cannot download anything?"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-11-01
I can't download anything after a fresh install. Synaptic Package Manager, Update Manager and apt-get downloads stay at 0% all the time.

I had a similar problem with Firefox before, but I typed "about:config" on the address bar and disabled IPv6 and it worked.

The only thing I could do now is Empathy and Firefox.

Ideas?

---

### Post by zkriesse on 2009-11-01
How did you install the OS?

---

### Post by infernus_crusher on 2009-11-11
It was a fresh install.

---

### Post by infernus_crusher on 2009-11-11
Downloaded ISO from [www.ubuntu.com](www.ubuntu.com) and burned it into a LiveCD (1x speed) using InfraRecorder, set up ext4 partition and just installed it there.

---

### Post by infernus_crusher on 2009-11-11
This is what I get by running this.

```

~$ sudo apt-get update
0% [Connecting to au.archive.ubuntu.com (32.1.3.136)] [Connecting to archive.canonical.com (32.1.3.136)] [Connecting to security.ubuntu.com (1.0.0.0)]

```

It stays right there, at 0% always. Does it have anything to do with the fact that it's an Australian server?

---

### Post by wilee-nilee on 2009-11-11
Go to software sources 1st tab click other then best server and let it ping the fastest connection and choose then run update. Also make sure the cd is ticked off in the 1st tab.

---

### Post by infernus_crusher on 2009-11-11
Fixes everything. Thanks heaps!

---

### Post by infernus_crusher on 2009-11-11
Installed ubuntu-restricted-extras but some packages could not be retrieved.

```

~$ sudo dpkg --configure -a
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-12 21:18:32--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:18:37--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2009-11-12 21:18:42--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 1.0.0.0
Connecting to mesh.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:18:47--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 1.0.0.0
Connecting to dfn.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:18:53--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2009-11-12 21:18:58--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 1.0.0.0
Connecting to jaist.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:03--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:13--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 1.0.0.0
Connecting to ufpr.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:19--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 1.0.0.0
Connecting to internode.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:24--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 1.0.0.0
Connecting to voxel.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:29--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... 1.0.0.0
Connecting to kent.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--2009-11-12 21:19:34--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 1.0.0.0
Connecting to internap.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up flashplugin-installer (10.0.32.18ubuntu1) ...
Downloading...
--2009-11-12 21:19:40--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.32.18.orig.tar.gz
Resolving archive.canonical.com... 1.0.0.0
Connecting to archive.canonical.com|1.0.0.0|:80... 


```

And this made me unable to install anything else with apt-get because I'll need to finish these ones first.

---

### Post by infernus_crusher on 2009-11-11
> **wilee-nilee said:**
> Go to software sources 1st tab click other then best server and let it ping the fastest connection and choose then run update. Also make sure the cd is ticked off in the 1st tab.

Why do I have to do this every time I restart? I cannot install anything else otherwise.

---

