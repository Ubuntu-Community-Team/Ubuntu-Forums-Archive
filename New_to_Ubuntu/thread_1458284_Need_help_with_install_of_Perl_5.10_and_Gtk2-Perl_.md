---
title: "Need help with install of Perl 5.10 and Gtk2-Perl in Ubuntu Hardy"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by maskiepop on 2010-04-19
I want to install a software called Chart in my Ubuntu Hardy. I was provided with this instruction: "To run Chart you need Perl 5.10, Gtk2-Perl 1.220, and a list of Perl modules as long as your arm, per the Makefile.PL in the sources, all available from CPAN. "

I am at a loss as to how to proceed with that. I am not familiar with Perl at all. I need some very detailed instructions. 

I have an older vesrsion of (5.8.8 ) Perl, and libgtk2-perl 1.161 in my Ubuntu right now. 

I have a perl 5.10.0 installed in /opt/lampp, as part of an earlier lampp install. I understand I have to keep these two perls separate. I believe they are right now.

I came across a piece of code called the "sandbox" (see below) from [http://live.gnome.org/GTK2-Perl/FrequentlyAskedQuestions](http://live.gnome.org/GTK2-Perl/FrequentlyAskedQuestions) that, it seems to me, would do what I want to do. But I haven't been able to get that to run. It seems I need to install ExtUtils::Depends, and one other (?) as well, first. The problem is that when I tried installing the ExtUtils::Depends with:

  /opt/lampp/bin/cpanp -i ExtUtils::Depends

it came up with a whole lot of errors: 

"[ERROR] No such author " blah, blah, " -- can't make module object" blah, blah.

Here is the "sandbox" code:

<

export SANDBOX=/opt/lampp

export PERL5LIB=$SANDBOX/lib/perl5/site_perl:$PERL5LIB

alias do_makefile_pl='perl Makefile.PL PREFIX=$SANDBOX'

export PATH=$SANDBOX/bin:$PATH 
export LD_LIBRARY_PATH=$SANDBOX/lib:$LD_LIBRARY_PATH 
export MANPATH=$SANDBOX/share/man:$MANPATH alias 
do_configure='./configure --prefix=$SANDBOX'

(cd ExtUtils-Depends && do_makefile_pl && make all test install) 
(cd ExtUtils-PkgConfig && do_makefile_pl && make all test install) 
(cd Glib && do_makefile_pl && make all test install) 
(cd Gtk2 && do_makefile_pl && make all test install) 
(cd Gnome2::Canvas && do_makefile_pl && make all test install)

---

