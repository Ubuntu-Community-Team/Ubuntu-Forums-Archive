---
title: "Convert cue &amp; bin to ISO format cdrom ?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-01-02
I know ccd2iso but is there the same for bin ?

:KS

---

### Post by frenchn00b on 2010-01-02
```
$ sudo apt-get install bchunk
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
bchunk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.7kB of archives.
After unpacking 69.6kB of additional disk space will be used.
Get:1 http://my.archive.ubuntu.com gutsy/universe bchunk 1.2.0-6 [13.7kB]
Fetched 13.7kB in 8s (1681B/s)
Selecting previously deselected package bchunk.
(Reading database ... 96119 files and directories currently installed.)
Unpacking bchunk (from .../bchunk_1.2.0-6_i386.deb) ...
Setting up bchunk (1.2.0-6) ...
**[COLOR="Red"]$ bchunk rld-ds2a.bin rld-ds2a.cue rld-ds2a[/COLOR]**
binchunker for Unix, version 1.2.0 by Heikki Hannikainen
Created with the kind help of Bob Marietta ,
partly based on his Pascal (Delphi) implementation.
Support for MODE2/2352 ISO tracks thanks to input from
Godmar Back , Colas Nahaboo
and Matthew Green .
Released under the GNU GPL, version 2 or later (at your option).

Reading the CUE file:

Track 1: MODE1/2352 01 00:00:00

Writing tracks:

1: rld-ds2a.iso01.iso 574/574 MB [********************] 100 %
$
```

---

