---
title: "Help installing a program called Reinteract"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by dorseye on 2009-02-17
[http://www.reinteract.org/trac/wiki/GettingIt#Linux](http://www.reinteract.org/trac/wiki/GettingIt#Linux)

Was following the tutorial here, trying to install Reinteract to Ubuntu 7.10

I got as far as getting the line: git clone git://git.fishsoup.net/reinteract
to work.

Then below that, it is talking about doing some commands with Checkinstall with Ubuntu:

"The 'checkinstall' utility makes it easy to create packages from any project with a Makefile. To use it, install the 'checkinstall' package on your distribution. The instructions below assume an Ubuntu or Debian system.

The package can be generated and installed by executing (from the checkout location):

./autogen.sh && ./configure --prefix=/usr && make
sudo checkinstall -y --fstrans=no"

Is the ./autogen line supposed to be run from terminal? When I do that I just get an error message from BASH:
ubuntu@ubuntu-desktop:/$ ./autogen.sh && ./configure --prefix=/usr && make sudo checkinstall -y --fstrans=no
bash: ./autogen.sh: No such file or directory

I tried to search for it:
ubuntu@ubuntu-desktop:/$ locate autogen
/usr/lib/perl5/Gnome2/Canvas/Install/gnomecanvasperl-autogen.h
/usr/lib/perl5/Gnome2/VFS/Install/vfs2perl-autogen.h
/usr/lib/perl5/Gnome2/Install/gnome2perl-autogen.h
/usr/lib/perl5/Gtk2/Install/gtk2perl-autogen.h

When I just run "checkinstall" from the terminal, it does come up with checkinstall dialogs, but it seems like that command is supposed to fill in everything for you? Any ideas / help? Thanks!

---

### Post by supersonicdarky on 2009-02-17
You need to be in the folder where git downloaded the snapshot.
```
find . -name autogen.sh
```
should work better.

---

### Post by RomeReactor on 2009-02-17
> **dorseye said:**
> ./autogen.sh && ./configure --prefix=/usr && make
sudo checkinstall -y --fstrans=no"

Those are two separate commands; run one:
```
./autogen.sh && ./configure --prefix=/usr && make
```
then the other:
```
sudo checkinstall -y --fstrans=no"
```[/QUOTE]

You need to change directory (in the terminal) to where you have the autogen.sh file before running the commands:
```
cd ~/reinteract
```

---

### Post by dorseye on 2009-02-17
> **RomeReactor said:**
> Those are two separate commands; run one:
```
./autogen.sh && ./configure --prefix=/usr && make
```
then the other:
```
sudo checkinstall -y --fstrans=no"
```

You need to change directory (in the terminal) to where you have the autogen.sh file before running the commands:
```
cd ~/reinteract
```[/QUOTE]

Ok sweet, at least got to the directory where the .sh file is.. now I'm getting this:

ubuntu@ubuntu-desktop:~/reinteract$ ./autogen.sh && ./configure --prefix=/usr && make
./autogen.sh: 8: autoreconf: not found

---

### Post by RomeReactor on 2009-02-17
Looks like you need autoconf and automake:
```
sudo aptitude install autoconf automake
```

EDIT: Also note that the second command:
```
sudo checkinstall -y --fstrans=no"
```
should be:
```
sudo checkinstall -y --fstrans=no
```
without the last quote.

---

### Post by dorseye on 2009-02-17
> **RomeReactor said:**
> Looks like you need autoconf and automake:
```
sudo aptitude install autoconf automake
```

That was it -- now I'll do some reading on what autoconf and automake are.

Thank you very much everyone!

---

