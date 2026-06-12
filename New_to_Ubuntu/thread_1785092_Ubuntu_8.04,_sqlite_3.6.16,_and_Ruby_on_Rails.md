---
title: "Ubuntu 8.04, sqlite 3.6.16, and Ruby on Rails"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by kprescott on 2011-06-17
I give up, I'm going to have to ask for help..

I am working on a Ruby on Rails tutorial ([http://ruby.railstutorial.org/ruby-on-rails-tutorial-book](http://ruby.railstutorial.org/ruby-on-rails-tutorial-book)).  I made it all the way through installing RVM, two versions of Ruby and Rails.  When I tried to "bundle install" I came to a screeching halt.

The version of sqlite required is 3.6.16.  The version that can be installed via apt-get is 3.4.something.  A profound amount of googling brought me to the following site which explained the problem ([http://blog.dbirlem.com/2011/05/31/ubuntu-installing-sqlite3-on-8-04lts/](http://blog.dbirlem.com/2011/05/31/ubuntu-installing-sqlite3-on-8-04lts/)).  I tried to follow the directions to install sqlite 3.6.16 from source code.  Once I figured out that I had to change the ownership of the directory to my user (since I was using sudo) I did manage to get it installed.  I think.

Problem is, rubygems still doesn't see it when I try to bundle install.  sqlite3-ruby keeps telling me I don't have the right version of sqlite.

How do I tell whether I installed the version correctly, and (Please!) step -by-baby step instructions to install it where it can be found by rubygems.  

I am running Ubuntu 8.04 on a Dell Mini-10 netbook.
RVM is installed single user (no sudo) in my home directory.
I installed sqlite in /usr/bin using sudo.

Can someone please help me get this running?  I've been working on it for a full week.

---

### Post by jtarin on 2011-06-17
In the terminal run the command ```
which sqlite3
```which should give you the version. The version you installed might have installed in a location that the application does not expect. You might have to point the configuration file(s) to that location.

Edit: Note from site link:> TIP Here&#8217;s the commands I used:

    [COLOR="Red"]_./configure &#8211;prefix=/usr/bin/sqlite3 _[/COLOR]**_(replace this path with whatever directory sqlite3 was installed to before, using which sqlite3 to figure that out)_**Make sure any earlier version is uninstalled.Before installation of the newer.

---

### Post by kprescott on 2011-06-17
I did apt-get remove on the sqlite that was previously installed.

Which sqlite3 returns nothing

There is an sqlite directory in the root directory, which I believe I created to download the source file into. It is empty.

There is an sqlite3 directory in /usr/bin.  I believe I created it so that I could use the directions you quoted exactly, and because I didn't think I had sqlite at all after I removed it.

When I cd into the directory, there are three subdirectories: bin, include, lib.  There is an sqlite3 file in the bin directory, but it is neither a command nor a directory.

I am using Gemfile to tell bundle install what to download - including a specific version of sqlite-ruby as described in the first link.  RVM and Gemfile are in my personal home directory.  I am not sure how to tell bundle install to look for sqlite3, and even if I did, I suspect it is not properly installed.  I am not sure what I did wrong...

---

### Post by jtarin on 2011-06-17
> **kprescott said:**
> I did apt-get remove on the sqlite that was previously installed.

Which sqlite3 returns nothing

There is an sqlite directory in the root directory, which I believe I created to download the source file into. It is empty.

There is an sqlite3 directory in /usr/bin.  I believe I created it so that I could use the directions you quoted exactly, and because I didn't think I had sqlite at all after I removed it.

When I cd into the directory, there are three subdirectories: bin, include, lib.  There is an sqlite3 file in the bin directory, but it is neither a command nor a directory.

Soemtimes which needs some help. Use the "locate <filename>"command, but first you need to bring your database up to date. Run the command ```
sudo updatedb
``` it will take some moments to run then when it returns to the prompt run ```
locate sqlite3
``` and post the results. Let's make sure what you have or don't have.

---

### Post by kprescott on 2011-06-17
Well, that was quick.  

I tried sudo updatedb and got back:

sudo: updatedb: command not found

I tried locate sqlite3, and also got command not found.

---

### Post by jtarin on 2011-06-17
Then you need to install "slocate". Either [here]("http://packages.ubuntu.com/hardy/slocate") or your friendly repository.

---

### Post by kprescott on 2011-06-17
I did apt-get slocate (with sudo).  It appeared to install properly, but included the following:

WARNING: You should run '/etc/cron.daily/slocate' as root. locate will not work
properly until you do or until it is run by cron (it is daily).

I tried to run: sudo /etc/cron.daily/slocate, but it didn't work. 

slocate: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory

Unsurprisingly, sudo updatedb got the same error.

---

### Post by jtarin on 2011-06-17
deleted

---

### Post by jtarin on 2011-06-17
> **kprescott said:**
> I did apt-get slocate (with sudo).  It appeared to install properly, but included the following:

WARNING: You should run '/etc/cron.daily/slocate' as root. locate will not work
properly until you do or until it is run by cron (it is daily).

I tried to run: sudo /etc/cron.daily/slocate, but it didn't work. 

slocate: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory

Unsurprisingly, sudo updatedb got the same error.[http://www.basicconfig.com/linux/linux-locate-command-tutorial](http://www.basicconfig.com/linux/linux-locate-command-tutorial)

---

### Post by kprescott on 2011-06-17
The directions given in the link you included are the process I followed:

Run /etc/cron.daily/slocate command to activate slocate and then run *slocate -u* option to create slocate database starting at path /:
 
```

luzar@ubuntu:~$ [COLOR=red]sudo /etc/cron.daily/slocate[/COLOR]
luzar@ubuntu:~$ [COLOR=red]sudo slocate -u[/COLOR]
[sudo] password for luzar:

```

It did not include any information on the specific error I got:

```
katrina@katrina:/$ sudo /etc/cron.daily/slocate
slocate: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory
katrina@katrina:/$ sudo updatedb
updatedb: fatal error: load_file: Could not open file: /etc/updatedb.conf: No such file or directory
```

So I did my usual "google the error message" and found the following:

"8.04 uses mlocate instead of slocate on desktops now, so if you have an  upgraded hardy you probably should change this too, if it is not done  automatically. "

So I am off to uninstall slocate and get mlocate.

Will update when this is done.

---

### Post by kprescott on 2011-06-17
Well, locate works now. 

It returned such a long list of files that my terminal window cut off the top...

Suggestions for limiting the search to what you need to see?
 
on second thought, this looks like most of what you need.. (above this there are a lot of files in the ruby installation in my home directory)

/temp/sqlite-3.6.16/libsqlite3.la
/temp/sqlite-3.6.16/sqlite3
/temp/sqlite-3.6.16/sqlite3.1
/temp/sqlite-3.6.16/sqlite3.c
/temp/sqlite-3.6.16/sqlite3.h
/temp/sqlite-3.6.16/sqlite3.lo
/temp/sqlite-3.6.16/sqlite3.o
/temp/sqlite-3.6.16/sqlite3.pc
/temp/sqlite-3.6.16/sqlite3.pc.in
/temp/sqlite-3.6.16/.libs/libsqlite3.a
/temp/sqlite-3.6.16/.libs/libsqlite3.la
/temp/sqlite-3.6.16/.libs/libsqlite3.lai
/temp/sqlite-3.6.16/.libs/libsqlite3.so
/temp/sqlite-3.6.16/.libs/libsqlite3.so.0
/temp/sqlite-3.6.16/.libs/libsqlite3.so.0.8.6
/temp/sqlite-3.6.16/.libs/sqlite3
/temp/sqlite-3.6.16/.libs/sqlite3.o
/temp/sqlite-3.6.16/ext/async/sqlite3async.c
/temp/sqlite-3.6.16/ext/async/sqlite3async.h
/temp/sqlite-3.6.16/src/sqlite3ext.h
/temp/sqlite-3.6.16/tool/mksqlite3c.tcl
/temp/sqlite-3.6.16/tool/mksqlite3internalh.tcl
/temp/sqlite-3.6.16/tsrc/sqlite3.h
/temp/sqlite-3.6.16/tsrc/sqlite3ext.h
/usr/bin/sqlite3
/usr/bin/sqlite3/bin
/usr/bin/sqlite3/include
/usr/bin/sqlite3/lib
/usr/bin/sqlite3/bin/sqlite3
/usr/bin/sqlite3/include/sqlite3.h
/usr/bin/sqlite3/include/sqlite3ext.h
/usr/bin/sqlite3/lib/libsqlite3.a
/usr/bin/sqlite3/lib/libsqlite3.la
/usr/bin/sqlite3/lib/libsqlite3.so
/usr/bin/sqlite3/lib/libsqlite3.so.0
/usr/bin/sqlite3/lib/libsqlite3.so.0.8.6
/usr/bin/sqlite3/lib/pkgconfig
/usr/bin/sqlite3/lib/pkgconfig/sqlite3.pc
/usr/include/sqlite3.h
/usr/include/sqlite3ext.h
/usr/lib/libsqlite3.a
/usr/lib/libsqlite3.la
/usr/lib/libsqlite3.so
/usr/lib/libsqlite3.so.0
/usr/lib/libsqlite3.so.0.8.6
/usr/lib/firefox-3.6.13/libsqlite3.so
/usr/lib/pkgconfig/sqlite3.pc
/usr/lib/python2.5/sqlite3
/usr/lib/python2.5/lib-dynload/_sqlite3.so
/usr/lib/python2.5/sqlite3/__init__.py
/usr/lib/python2.5/sqlite3/__init__.pyc
/usr/lib/python2.5/sqlite3/dbapi2.py
/usr/lib/python2.5/sqlite3/dbapi2.pyc
/usr/lib/python2.5/sqlite3/test
/usr/lib/python2.5/sqlite3/test/__init__.py
/usr/lib/python2.5/sqlite3/test/__init__.pyc
/usr/lib/python2.5/sqlite3/test/dbapi.py
/usr/lib/python2.5/sqlite3/test/dbapi.pyc
/usr/lib/python2.5/sqlite3/test/factory.py
/usr/lib/python2.5/sqlite3/test/factory.pyc
/usr/lib/python2.5/sqlite3/test/hooks.py
/usr/lib/python2.5/sqlite3/test/hooks.pyc
/usr/lib/python2.5/sqlite3/test/regression.py
/usr/lib/python2.5/sqlite3/test/regression.pyc
/usr/lib/python2.5/sqlite3/test/transactions.py
/usr/lib/python2.5/sqlite3/test/transactions.pyc
/usr/lib/python2.5/sqlite3/test/types.py
/usr/lib/python2.5/sqlite3/test/types.pyc
/usr/lib/python2.5/sqlite3/test/userfunctions.py
/usr/lib/python2.5/sqlite3/test/userfunctions.pyc
/usr/lib/ruby/1.8/sqlite3
/usr/lib/ruby/1.8/sqlite3.rb
/usr/lib/ruby/1.8/i686-linux-lp/sqlite3_api.so
/usr/lib/ruby/1.8/sqlite3/constants.rb
/usr/lib/ruby/1.8/sqlite3/database.rb
/usr/lib/ruby/1.8/sqlite3/driver
/usr/lib/ruby/1.8/sqlite3/errors.rb
/usr/lib/ruby/1.8/sqlite3/pragmas.rb
/usr/lib/ruby/1.8/sqlite3/resultset.rb
/usr/lib/ruby/1.8/sqlite3/statement.rb
/usr/lib/ruby/1.8/sqlite3/translator.rb
/usr/lib/ruby/1.8/sqlite3/value.rb
/usr/lib/ruby/1.8/sqlite3/version.rb
/usr/lib/ruby/1.8/sqlite3/driver/dl
/usr/lib/ruby/1.8/sqlite3/driver/native
/usr/lib/ruby/1.8/sqlite3/driver/dl/api.rb
/usr/lib/ruby/1.8/sqlite3/driver/dl/driver.rb
/usr/lib/ruby/1.8/sqlite3/driver/native/driver.rb
/usr/lib/xulrunner-1.9.0.19/libsqlite3.so
/usr/lib/xulrunner-1.9.0.19/libsqlite3.so.0
/usr/share/doc/libsqlite3-0
/usr/share/doc/libsqlite3-dev
/usr/share/doc/libsqlite3-ruby
/usr/share/doc/libsqlite3-ruby1.8
/usr/share/doc/sqlite3
/usr/share/doc/sqlite3-doc
/usr/share/doc/libsqlite3-0/README
/usr/share/doc/libsqlite3-0/README.Debian
/usr/share/doc/libsqlite3-0/changelog.Debian.gz
/usr/share/doc/libsqlite3-0/copyright
/usr/share/doc/libsqlite3-dev/README
/usr/share/doc/libsqlite3-dev/changelog.Debian.gz
/usr/share/doc/libsqlite3-dev/copyright
/usr/share/doc/libsqlite3-ruby/changelog.Debian.gz
/usr/share/doc/libsqlite3-ruby/changelog.gz
/usr/share/doc/libsqlite3-ruby/copyright
/usr/share/doc/libsqlite3-ruby1.8/README
/usr/share/doc/libsqlite3-ruby1.8/changelog.Debian.gz
/usr/share/doc/libsqlite3-ruby1.8/changelog.gz
/usr/share/doc/libsqlite3-ruby1.8/copyright
/usr/share/doc/libsqlite3-ruby1.8/faq
/usr/share/doc/libsqlite3-ruby1.8/faq/faq.html
/usr/share/doc/libsqlite3-ruby1.8/faq/faq.rb
/usr/share/doc/libsqlite3-ruby1.8/faq/faq.yml.gz
/usr/share/doc/sqlite3/README
/usr/share/doc/sqlite3/changelog.Debian.gz
/usr/share/doc/sqlite3/copyright
/usr/share/doc/sqlite3-doc/2005osaward.gif
/usr/share/doc/sqlite3-doc/README
/usr/share/doc/sqlite3-doc/arch.gif
/usr/share/doc/sqlite3-doc/arch.html
/usr/share/doc/sqlite3-doc/arch2.gif
/usr/share/doc/sqlite3-doc/autoinc.html
/usr/share/doc/sqlite3-doc/c_interface.html
/usr/share/doc/sqlite3-doc/capi3.html
/usr/share/doc/sqlite3-doc/capi3ref.html
/usr/share/doc/sqlite3-doc/changelog.Debian.gz
/usr/share/doc/sqlite3-doc/changes.html
/usr/share/doc/sqlite3-doc/compile.html
/usr/share/doc/sqlite3-doc/conflict.html
/usr/share/doc/sqlite3-doc/copyright
/usr/share/doc/sqlite3-doc/copyright-release.html
/usr/share/doc/sqlite3-doc/copyright.html
/usr/share/doc/sqlite3-doc/datatype3.html
/usr/share/doc/sqlite3-doc/datatypes.html
/usr/share/doc/sqlite3-doc/direct1b.gif
/usr/share/doc/sqlite3-doc/docs.html
/usr/share/doc/sqlite3-doc/download.html
/usr/share/doc/sqlite3-doc/faq.html
/usr/share/doc/sqlite3-doc/fileformat.html
/usr/share/doc/sqlite3-doc/formatchng.html
/usr/share/doc/sqlite3-doc/fullscanb.gif
/usr/share/doc/sqlite3-doc/index-ex1-x-b.gif
/usr/share/doc/sqlite3-doc/index.html
/usr/share/doc/sqlite3-doc/indirect1b1.gif
/usr/share/doc/sqlite3-doc/lang.html
/usr/share/doc/sqlite3-doc/lang_altertable.html
/usr/share/doc/sqlite3-doc/lang_analyze.html
/usr/share/doc/sqlite3-doc/lang_attach.html
/usr/share/doc/sqlite3-doc/lang_comment.html
/usr/share/doc/sqlite3-doc/lang_conflict.html
/usr/share/doc/sqlite3-doc/lang_copy.html
/usr/share/doc/sqlite3-doc/lang_createindex.html
/usr/share/doc/sqlite3-doc/lang_createtable.html
/usr/share/doc/sqlite3-doc/lang_createtrigger.html
/usr/share/doc/sqlite3-doc/lang_createview.html
/usr/share/doc/sqlite3-doc/lang_createvtab.html
/usr/share/doc/sqlite3-doc/lang_delete.html
/usr/share/doc/sqlite3-doc/lang_detach.html
/usr/share/doc/sqlite3-doc/lang_dropindex.html
/usr/share/doc/sqlite3-doc/lang_droptable.html
/usr/share/doc/sqlite3-doc/lang_droptrigger.html
/usr/share/doc/sqlite3-doc/lang_dropview.html
/usr/share/doc/sqlite3-doc/lang_explain.html
/usr/share/doc/sqlite3-doc/lang_expr.html
/usr/share/doc/sqlite3-doc/lang_insert.html
/usr/share/doc/sqlite3-doc/lang_keywords.html
/usr/share/doc/sqlite3-doc/lang_reindex.html
/usr/share/doc/sqlite3-doc/lang_replace.html
/usr/share/doc/sqlite3-doc/lang_select.html
/usr/share/doc/sqlite3-doc/lang_transaction.html
/usr/share/doc/sqlite3-doc/lang_update.html
/usr/share/doc/sqlite3-doc/lang_vacuum.html
/usr/share/doc/sqlite3-doc/lemon.html
/usr/share/doc/sqlite3-doc/limits.html
/usr/share/doc/sqlite3-doc/lockingv3.html
/usr/share/doc/sqlite3-doc/mingw.html
/usr/share/doc/sqlite3-doc/nulls.html
/usr/share/doc/sqlite3-doc/oldnews.html
/usr/share/doc/sqlite3-doc/omitted.html
/usr/share/doc/sqlite3-doc/opcode.html
/usr/share/doc/sqlite3-doc/pragma.html
/usr/share/doc/sqlite3-doc/quickstart.html
/usr/share/doc/sqlite3-doc/shared.gif
/usr/share/doc/sqlite3-doc/speed.html
/usr/share/doc/sqlite3-doc/sqlite.gif
/usr/share/doc/sqlite3-doc/sqlite.html
/usr/share/doc/sqlite3-doc/support.html
/usr/share/doc/sqlite3-doc/table-ex1b2.gif
/usr/share/doc/sqlite3-doc/tclsqlite.html
/usr/share/doc/sqlite3-doc/vdbe.html
/usr/share/doc/sqlite3-doc/version3.html
/usr/share/man/man1/sqlite3.1.gz
/usr/share/mime/application/x-sqlite3.xml
/usr/share/mimelnk/application/x-sqlite3.desktop
/var/lib/dpkg/info/libsqlite3-0.list
/var/lib/dpkg/info/libsqlite3-0.md5sums
/var/lib/dpkg/info/libsqlite3-0.postinst
/var/lib/dpkg/info/libsqlite3-0.postrm
/var/lib/dpkg/info/libsqlite3-0.shlibs
/var/lib/dpkg/info/libsqlite3-dev.list
/var/lib/dpkg/info/libsqlite3-dev.md5sums
/var/lib/dpkg/info/libsqlite3-ruby.list
/var/lib/dpkg/info/libsqlite3-ruby.md5sums
/var/lib/dpkg/info/libsqlite3-ruby1.8.list
/var/lib/dpkg/info/libsqlite3-ruby1.8.md5sums
/var/lib/dpkg/info/sqlite3-doc.list
/var/lib/dpkg/info/sqlite3-doc.md5su


I appreciate your help.  You've been very patient.  Unfortunately, I get up at 5am and it is now 10:30, and therefore past my bedtime.  I will check in in the morning to see what insights you may have regarding my situation.

---

### Post by jtarin on 2011-06-17
Sh**! I should have known that. Has it been that long? Sorry my error. Make sure you completely remove the other.

---

### Post by kprescott on 2011-06-18
I did apt-get remove slocate.  Is that sufficient?

So, anyway, looks like I actually created temp to download and unpack the source to...  It's been a few days and I've tried so many things to to get this working, I'm losing track.  On the plus side, though, I am learning a lot through the process.

Is there anything additional I need to do to remove old installations of sqlite?

Should I recompile and install sqlite 3.6.16?

What are the steps to do that properly, because clearly I missed something the first time?

Following is the line in my Gemfile that references the version of sqlite3-ruby which requires the 3.6.16 version of sqlite or higher:

```
gem 'sqlite3-ruby', '1.3.2', :require => 'sqlite3'

```

---

### Post by jtarin on 2011-06-18
> **kprescott said:**
> Well, locate works now. 

It returned such a long list of files that my terminal window cut off the top...

Suggestions for limiting the search to what you need to see?
 
Use the command ```
locate <filename> | more
```This pipes the command _locate_ to the command _more_. Then just press enter for next pae.

---

### Post by jtarin on 2011-06-18
> **kprescott said:**
> I did apt-get remove slocate.  Is that sufficient?

So, anyway, looks like I actually created temp to download and unpack the source to...  It's been a few days and I've tried so many things to to get this working, I'm losing track.  On the plus side, though, I am learning a lot through the process.

Is there anything additional I need to do to remove old installations of sqlite?Possibly look in /var/apt/cache and see if the package is still there, if yes delete it as root, unless you have Ubuntu Tweak which can be used.

> **kprescott said:**
> Should I recompile and install sqlite 3.6.16?Yes I would, but first trash all your file you configured before saving only the downloaded compressed source to start with.

> **kprescott said:**
> What are the steps to do that properly, because clearly I missed something the first time?If you will return to earlier post in this thread yo will see the problem and solution with PATH=.

Following is the line in my Gemfile that references the version of sqlite3-ruby which requires the 3.6.16 version of sqlite or higher:

```
gem 'sqlite3-ruby', '1.3.2', :require => 'sqlite3'

```[/QUOTE]

---

### Post by kprescott on 2011-06-18
> If you will return to earlier post in this thread yo will see the problem and solution with PATH=.

I do not see a post with information about installation and PATH.  Only the one which quoted a bit from the instructions I used to install the first time.  Which post are you referring to?

There is a deleted post, just before the slocate discussion...

---

### Post by jtarin on 2011-06-18
> **kprescott said:**
> I do not see a post with information about installation and PATH.  Only the one which quoted a bit from the instructions I used to install the first time.  Which post are you referring to?

There is a deleted post, just before the slocate discussion...From visiting the link you gave [I posted this.]("http://ubuntuforums.org/showpost.php?p=10951726&postcount=2")

---

### Post by kprescott on 2011-06-18
I don't understand what you mean me to do by quoting a line from a process I *already tried.*

I deleted the sqlite directory in the root directory.

I deleted the /usr/bin/sqlite3 directory.

I deleted the directory in /temp that had been created when I originally unpacked the tar.gz file.

I unpacked the tar.gz file.

I followed the directions from the link, including pointing it to /usr/bin/sqlite3

It seemed to work.

which sqlite 3 returns nothing.

bundle install results in the following error:

  ```
      /home/katrina/.rvm/rubies/ruby-1.9.2-p180/bin/ruby extconf.rb 
checking for sqlite3.h... yes
checking for sqlite3_libversion_number() in -lsqlite3... yes
checking for rb_proc_arity()... yes
checking for sqlite3_initialize()... no
sqlite3-ruby only supports sqlite3 versions 3.6.16+, please upgrade!
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.
```

I am not sure where to find the mkmf.log file.  I looked for it but didn't  see it.

I am pretty much exactly where I was when I first posted.  Why won't it work?

---

### Post by jtarin on 2011-06-18
If you graphically (use Nautilus) go to the directory where the executable is located "/usr/bin/sqlite3"....is it there?

Older versions of sqlite-ruby didn't require 3.6.16. You could try
installing an older version of the gem (with the --version option)

---

### Post by kprescott on 2011-06-18
in /usr/bin/sqlite3/bin there is an sqlite3 file.  Properties says it is a 96.1K executable.  Double-clicking on it does nothing, just as typing the name of the file in the terminal did nothing.  The owner is root and the group is root.

When I installed I was able to do the ./configure without sudo, I was able to do make without sudo, but I had to use sudo to do make install.

the tutorial I am following is specific about the versions of ruby and sqlite to install so that the exercises will all work.

---

### Post by jtarin on 2011-06-18
Also try the locate command to find it. Remeber to updatedb after installing anything to bring the database up to date. If you installed it....it should be there.

---

### Post by jtarin on 2011-06-18
You might have better luck in the [Ruby Forums.]("http://www.ruby-forum.com/topic/753042#new") I'm sure someone has seen this problem before.

---

