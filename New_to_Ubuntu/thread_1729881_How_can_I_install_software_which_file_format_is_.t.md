---
title: "How can I install software which file format is .tar.bz2 ?"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Uewd on 2011-04-15
[FONT=Comic Sans MS][SIZE=2]When I download some software from the internet, they will offer only .tar.bz file format. It may be some kind of silly questions but I am still a new Linux user :) . Can any one help me?

Thanks.
Uewd
[/SIZE][/FONT]

---

### Post by Paqman on 2011-04-15
Generally you don't need to download software from random sites on Linux. Just open up Ubuntu Software Centre and install from there. Nice and easy, and it'll be kept updated a s well.

Don't bother with tar.gz, .tar.bz2, etc. They're more trouble than they're worth. If you need something that's not available in the repositories, there's almost always a better way of installing it than a tarball.

---

### Post by Uewd on 2011-04-15
> **Paqman said:**
> Generally you don't need to download software from random sites on Linux. Just open up Ubuntu Software Centre and install from there. Nice and easy, and it'll be kept updated a s well.

Don't bother with tar.gz, .tar.bz2, etc. They're more trouble than they're worth. If you need something that's not available in the repositories, there's almost always a better way of installing it than a tarball.

Maybe a solution but sometimes we need software that is not available there. Any other solution?

---

### Post by sanderd17 on 2011-04-15
.tar.gz and .tar.bz2 are just free alternatives to zip files. So the installation depends per file. If you want to install it, you need to extract it with an unzipper and then look for a README or check for documentation elsewhere.

But I fully agree with paqman. Always look for something similar in the software center. If it's not in the software center, it's probably outdated (and broken) or brandnew (and really unstable).

---

### Post by 1clue on 2011-04-15
Don't have my Ubuntu box in front of me, but presumably the options are the same as on my Mac:

**tar -xjf <myfile.tar.bzip2>** will extract that sort of thing.

@Paqman, there are all sorts of situations where software or files come in that format.  Sometimes it's the only viable option, for example on some commercial software.  Otherwise, it's an archive format with very good compression, so why tell him he doesn't need to know?

---

### Post by Uewd on 2011-04-15
> **sanderd17 said:**
> .tar.gz and .tar.bz2 are just free alternatives to zip files. So the installation depends per file. If you want to install it, you need to extract it with an unzipper and then look for a README or check for documentation elsewhere.

But I fully agree with paqman. Always look for something similar in the software center. If it's not in the software center, it's probably outdated (and broken) or brandnew (and really unstable).
I understood from what you said that it is useless and a waste of time to download software like this, is this right?

---

### Post by arochester on 2011-04-15
Look at e.g. [http://enli.co.cc/tutorials/how-to-install-anything-in-ubuntu-a-compilation/](http://enli.co.cc/tutorials/how-to-install-anything-in-ubuntu-a-compilation/) Scroll down to "Compiling from source-code"

---

### Post by Uewd on 2011-04-15
> **arochester said:**
> Look at e.g. [http://enli.co.cc/tutorials/how-to-install-anything-in-ubuntu-a-compilation/](http://enli.co.cc/tutorials/how-to-install-anything-in-ubuntu-a-compilation/) Scroll down to "Compiling from source-code"
If I installed software using the method you mentioned [here]("http://enli.co.cc/tutorials/how-to-install-anything-in-ubuntu-a-compilation/"), can I be able to uninstall it?

---

### Post by wyliecoyoteuk on 2011-04-15
Compiling from source is rarely necessary, there are few packages that require it, but it is not that hard.

You can easily uninstall using a package manager, but if you install using a script, unless there is a matching uninstall script, no, you can't easily uninstall.

---

### Post by 1clue on 2011-04-15
> **Uewd said:**
> I understood from what you said that it is useless and a waste of time to download software like this, is this right?

No, it's not right.

Tar is used often for transporting data and software.  It's like zip in Windows.  Slang for a file or directory compressed using tar is called a "tarball."  (tarball is actually just one type of such files but good enough for now)

The preference for the software center is a good one, because Ubuntu takes some care to ensure that the software you get from that center is from a reliable source and free of malware.

However some people take it too far and deny validity of any software which does not come from Ubuntu-recognized sources.  There is a bunch of software that doesn't come through Ubuntu which is extremely worthwhile to have if you have a use for it.  You just need to be more careful and make sure you know what you're doing.

---

### Post by oklokl on 2011-04-15
[COLOR=#000000][FONT=Verdana]sudo apt-get install bsdtar
[/FONT][/COLOR]

---

### Post by Uewd on 2011-04-15
> **oklokl said:**
> [COLOR=#000000][FONT=Verdana]sudo apt-get install bsdtar
[/FONT][/COLOR]

This command installs a program. What is this program and what is its function?

---

### Post by kliffs on 2011-04-15
Yes there is usually no reason to use a tarball but if you do need to just extract the archive, if you are lucky there will be a file called install.sh.  Double click on the install.sh script. It might ask if you want to run in terminal, so if it does just click Run in Terminal. Otherwise you will have to compile or read the documentation/README.

---

### Post by oklokl on 2011-04-15
[FONT=gulim][COLOR=#6600FF][FONT=&#44404;&#47548;][FONT=Gulim]ex>root c:#  bsdtar[/FONT][/FONT][FONT=Gulim] fxz testfiles-0.tar.bz2[/FONT][/COLOR][/FONT]

**.tar.bz2 <- **Un-compression
bsdtar
tar(1) from FreeBSD, using libarchive

The bsdtar program has a number of advantages over previous tar
implementations:

 * Library. Since the core functionality is in a library, it can be
   used by other tools, such as pkg_add.

 * Automatic format detection. Libarchive automatically detects the
   compression (none/gzip/bzip2) and format (old tar, ustar, gnutar,
   pax, cpio, iso9660, zip) when reading archives. It does this for
   any data source.

 * Pax Interchange Format Support. This is a POSIX/SUSv3 extension to
   the old "ustar" tar format that adds arbitrary extended attributes
   to each entry. Does everything that GNU tar format does, only
   better.

 * Handles file flags, ACLs, arbitrary pathnames, etc. Pax interchange
   format supports key/value attributes using an easily-extensible
   technique. Arbitrary pathnames, group names, user names, file sizes
   are part of the POSIX standard; libarchive extends this with
   support for file flags, ACLs, and arbitrary device numbers.

 * GNU tar support. Libarchive reads most GNU tar archives. If there
   is demand, this can be improved further.

---

### Post by oldos2er on 2011-04-15
> **Uewd said:**
> [FONT=Comic Sans MS][SIZE=2]When I download some software from the internet, they will offer only .tar.bz file format. It may be some kind of silly questions but I am still a new Linux user :) . Can any one help me?
[/SIZE][/FONT]

What software? Who is "they"? Is it source code, or something else?

Your questions aren't silly in the least, we just need more detail to provide a meaningful answer.

---

### Post by Paqman on 2011-04-16
> **Uewd said:**
> Maybe a solution but sometimes we need software that is not available there. Any other solution?

Yes, definitely, but tarballs are way down the list of preferences.

If your software is not available in the Ubuntu repositories your should look for:

[LIST=1]
[*]Does the software have it's own repository? Google do this for Chrome, Picasa, etc as does Virtualbox
[*]If there's no repo availablle, look for a .deb file. Download it and double click to install
[*]If there's no official .deb, has somebody packaged the software into a PPA? This is like an unofficial mini-repo, and they can be very handy
[*]Is there an alternative program that has one of the above installers available?
[*]If none of these are applicable, then consider using a tarball. Tarballs are pretty random and can contain pretty much anything, but there should ideally be instructions on how to install it (possibly inside the tarball)
[/LIST]

---

