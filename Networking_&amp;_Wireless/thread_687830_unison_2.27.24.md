---
title: "unison 2.27.24"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by waldorf on 2008-02-04
Is there a way to install unison 2.27.24?

Thanks in advance

---

### Post by kevdog on 2008-02-04
Why dont you either download and compile the sources or grab the svn version.  Is this an older or very new version?

---

### Post by crispinb on 2008-02-22
I too would like the latest version, which is 2.27.57, or at least something comparatively recent. The current ubuntu repo version, 2.13.16, is very old indeed. Perhaps it's an app that doesn't attract much interest.

I don't want to compile it myself -- it involves OCaml and other stuff irrelevant to my system, and I use Ubuntu precisely because it has lots of binaries easily available, and easy to maintain and upgrade.

Alternatively, can anyone recommend a different app to sync a home directory to a (locally attached) USB drive? (Two-way; not rsync).

---

### Post by MountainX on 2008-02-25
I have Unison 2.9.1-7 available in Synaptic PM. I have all the usual repositories enabled (including universe, multiverse and 3rd party).

I was looking for advice on whether to install this version or the earlier one. I think I'll try this one. Do I need the GTK package for Gutsy?

---

### Post by crispinb on 2008-02-25
2.9.1 is even older. The 'unison' package provided in universe is 2.13.16. I'd use that. 

You only need unison-gtk if you want to run unison from a GUI. The gtk front-end is a bit primitive, but OK if you don't want to use the commandline. However in either case you'll need to read the unison documentation to find out how to set out the sync profile configuration files (*.prf).

---

### Post by virgo977virgo on 2008-02-25
from the Unison download page [http://www.cis.upenn.edu/~bcpierce/unison/download.html]("http://www.cis.upenn.edu/~bcpierce/unison/download.html") I found two precompiled versions of Unison for linux:

**version 2.27.57**
[http://alan.petitepomme.net/projets/unison/index.html]("http://alan.petitepomme.net/projets/unison/index.html")
*download, decompress the .zip and make the content executable with "chmod 755 unison-2.27.57"*

**version 2.27.47**
[http://www.cs.haifa.ac.il/%7Eshuly/unison/]("http://www.cs.haifa.ac.il/%7Eshuly/unison/")
*download and make the downloaded file executable with "chmod 755 unison-2.27.47-linux32.text"*


to compile manually Unison, follow the simple steps below:
[LIST=1]
[*]download the source package *unison-2.27.57.tar.gz* from [http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/]("http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/")
[*]install ocaml from Ubuntu Synaptic Package Manager
[*]decompress the source package downloaded from the Unison site
[*]as written in the *INSTALL* file in the source package, compile with the command ```
 make UISTYLE=text
```
[*]run unison with the command ```
./unison
```
[/LIST]

bye

---
Stefano Spinucci

---

### Post by crispinb on 2008-02-26
Thanks for those suggestions Stefano. I generally try to avoid installing anything unpackaged (for the sake of easy maintainability). But it does seem that its the only choice in this instance.

---

### Post by bennywhere on 2008-03-19
Maybe you already noticed, but the newest version in .deb format can be downloaded at:

[http://www.getdeb.net/release.php?id=2321](http://www.getdeb.net/release.php?id=2321)

---

### Post by crispinb on 2008-03-19
> **bennywhere said:**
> Maybe you already noticed, but the newest version in .deb format can be downloaded at:

[http://www.getdeb.net/release.php?id=2321](http://www.getdeb.net/release.php?id=2321)

I hadn't noticed, and haven't really checked out getdeb.net before. It looks useful, so thanks for that.

---

