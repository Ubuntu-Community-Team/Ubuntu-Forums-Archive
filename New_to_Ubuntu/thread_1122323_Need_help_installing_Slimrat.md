---
title: "Need help installing Slimrat"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by jacatone on 2009-04-10
I'd like to try Slimrat which is a Linux Rapidshare Downloader. In the  instructions it say's to install the:

# perl modules:

    * Getopt::Long
    * LWP::UserAgent
    * Term::ANSIColor
    * WWW::Mechanize
          o HTTP::Response::Encoding (newer versions of WWW::Mechanize depends on this) 

How do I do that?

And to: # Make symlinks in $PATH

ln -s /path/to/slimrat/slimrat /usr/local/bin/slimrat
ln -s /path/to/slimrat/slimrat-gui /usr/local/bin/slimrat-gui

# edit config file and select your terminal emulator 

Don't know how to do that either? Thanks.

---

### Post by cariboo on 2009-04-10
Perl modules are pretty easy to install using MCPAN. Open a terminal and type:

```
perl -MCPAN -e 
```

and run through the configuration. Once you have it configured, type:

```
install Getopt::Long
```

for example to install modules.

Jim

---

### Post by kostkon on 2009-04-11
I would like to recommend you *Tucan*, I believe it's much better than *Slimrat*. You can [download it and easily install it from here]("http://www.getdeb.net/app/Tucan").

If you decide to use it, don't forget to check regularly for updates for its plugins; there is an option in its preferences.

---

### Post by alfbar1 on 2010-07-09
Therre are other options jDownloader, FreeRapid Downloader, both in java require more memory, I use FreeRapid Downloader , because gui's faster than jDownloader, and has more plugins than Slimrat an Tucan, and support resume

---

