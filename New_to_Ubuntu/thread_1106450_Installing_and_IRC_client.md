---
title: "Installing and IRC client?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Haioko on 2009-03-25
I want to install [http://www.irssi.org/download](http://www.irssi.org/download)

But it's telling me all this terminal stuff, which I don't understand.

> 
 Irssi installation instructions
 -------------------------------

First of all, you need GLib to compile irssi. If you don't have it
already, you can either install it or let irssi download & compile it.
The automatic downloading works only if you have wget or ncftpget
installed, you can do it manually by unpacking glib sources to irssi's
root dir.

For most people, this should work just fine:

 ./configure
 make
 su
 make install     (not _really_ required except for perl support)

You may want to give some parameters to configure, here's the most
commonly used ones:

  --prefix        - Specifies the path where irssi will be installed.
                    YES, you can install irssi WITHOUT ROOT permissions
                    by using --prefix=/home/dir
  --with-proxy    - Build the irssi proxy (see startup-HOWTO).
  --enable-ipv6   - Enable IPv6 support. If you want irssi to prefer
                    IPv6 for hosts that have both v4 and v6 addresses,
		    use /SET resolve_prefer_ipv6 ON. You can also override
		    this with /SERVER -4 or -6 options.

If GLib or ncurses is installed installed in a non-standard path you can
specify it with --with-glib=/path and --with-ncurses=/path. If anything else
is in non-standard path, you can just give the paths in CPPFLAGS and LIBS
environment variable, eg.:

  CPPFLAGS=-I/opt/openssl/include LDFLAGS=-L/opt/openssl/lib ./configure

Irssi doesn't really need curses anymore, by default it uses
terminfo/termcap directly. The functions for using terminfo/termcap
however are usually only in curses library, some systems use libtermcap
as well. If you want to use only curses calls for some reason, use
--without-terminfo.


 Perl problems
 -------------

Perl support generates most of the problems. There's quite a many
things that can go wrong:

 - Perl 5.004 doesn't work by default, you'll need to edit
   src/perl/irssi-core.pl and remove all lines with "delete_package"
   in them.
 - Compiling fails if you compile irssi with GCC in a system that has
   perl compiled with some other C compiler. Very common problem with
   non-Linux/BSD systems. You'll need to edit src/perl/*/Makefile files
   and remove the parameters that gcc doesn't like. Mostly you'll just
   need to keep the -I and -D parameters and add -fPIC.
 - If there's any weird crashing at startup, you might have older irssi's
   perl libraries installed somewhere, and you should remove those.
 - Dynamic libraries don't want to work with some systems, so if your
   system complains about some missing symbol in Irssi.so file, configure
   irssi with --with-perl-staticlib option (NOT same as --with-perl=static).
 - If configure complains that it doesn't find some perl stuff, you're
   probably missing libperl.so or libperl.a. In debian, you'll need to do
   apt-get install libperl-dev

You can verify that the perl module is loaded and working with "/LOAD"
command. It should print something like:

Module               Type    Submodules
...
perl                 static  core fe


Thanks.

---

### Post by jordilin on 2009-03-25
Have you tried XChat which is in the repos and it is one of the best out there?

---

### Post by kanikilu on 2009-03-25
I second xchat, but if you want irssi, why not install from the repos? ```
sudo apt-get install irssi
``` or search for it in Synaptic.

---

### Post by Haioko on 2009-03-25
I always think about Synaptic last. Sorry guys, I'm too used to Windows lol.

Thanks.

---

### Post by andrew.46 on 2009-03-26
Hi Haioko,

If you are keen on irssi there is a guide on these forums that will lead you through the setup:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

irssi is well worth the initial investment of time and effort in learning how to use this great irc client. And then there is always X-Chat if it does not work out :-).

Andrew

---

### Post by DarkReaper79 on 2009-03-26
xchat is the way to go. I only used it once so far, but was very happy with it.

---

### Post by som24 on 2009-03-31
i've a question regarding xchat.how could i configure it so that when i open it it'll automatically load the last opened servers?

---

### Post by hyper_ch on 2009-04-01
you can configure servers and according channels somewhere and and have them opened upon start of it. I don't think that you can set an option to connect to all servers and join channels that you were last time.

---

