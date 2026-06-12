---
title: "How to install a newer version of Gtk2 and Glib in Ubuntu Hardy safely"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by maskiepop on 2010-04-15
The install of Gtk2 and Glib mentioned above is only the first part. What I really want to do is install a piece of software called Chart in my Ubuntu Hardy machine. Here is the instruction:

"To run Chart you need Perl 5.10, Gtk2-Perl 1.220, and a list of Perl modules as long as your arm, per the Makefile.PL in the sources, all available from CPAN. "

My problem basically is that I am at a loss as to how to proceed with that. I am not familiar with Perl at all. I need some very detailed instructions.

To the experts: you might want to:

   1. tell me why I am having problems with my install of ExtUtils::Depends

   2. tell me, in addition, how I should go about installing Glib and Gtk2-Perl in my machine,

   3. if I can do it safely with the "sandbox" code below, or whether I should consider other ways of doing it.

My Ubuntu Hardy has perl 5.8.8. I have a perl 5.10.0 installed in /opt/lampp, as part of an earlier lampp install. I understand I have to keep these two perls separate. I believe they are right now.

I came across a piece of code called the "sandbox" (see below) fromL [http://live.gnome.org/GTK2-Perl/FrequentlyAskedQuestions](http://live.gnome.org/GTK2-Perl/FrequentlyAskedQuestions) that, it seems to me, would do what I want to do. But I haven't been able to get that to run. It seems I need to install ExtUtils::Depends, and one other (?) as well, first. The problem is that when I tried installing the ExtUtils::Depends with:

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

