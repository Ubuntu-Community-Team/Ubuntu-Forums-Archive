---
title: "Problem with installing file .tar.gz2"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by alarikh on 2009-03-02
Hello, tried to install firefox after
 cd ~/Desktop
tar xjvf file .tar.gz2
> $:~/Desktop$ cd firefox
~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory 

Dont know how to install this another way, Thx

---

### Post by taurus on 2009-03-02
Did you actually download the source or just the binary?  

Post the output of the second command.

```
cd ~/Desktop/firefox
ls -la
```

---

### Post by wilbbe01 on 2009-03-02
Are you trying to install firefox???  I'm confused?  Or are you just trying to install something but using firefox in the example?

---

### Post by zarma on 2009-03-02
does the file decompress?? in your directory ??

---

### Post by alarikh on 2009-03-02
> Post the output of the second command.

Code:
cd ~/Desktop/firefox
ls -la


alex@alex-laptop:~/Desktop/firefox$ ls -la
total 16508
drwxr-xr-x 13 alex alex     4096 2009-01-19 23:08 .
drwxr-xr-x  7 alex alex     4096 2009-03-02 23:10 ..
-rw-r--r--  1 alex alex     2035 2009-01-19 23:08 application.ini
-rw-r--r--  1 alex alex        0 2009-01-19 23:08 .autoreg
-rwxr-xr-x  1 alex alex     1953 2009-01-19 23:08 blocklist.xml
-rw-r--r--  1 alex alex      232 2009-01-19 23:08 browserconfig.properties
drwxr-xr-x  3 alex alex     4096 2009-01-19 23:08 chrome
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 components
-rwxr-xr-x  1 alex alex    45096 2009-01-19 23:08 crashreporter
-rw-r--r--  1 alex alex     3558 2009-01-19 23:08 crashreporter.ini
-rw-r--r--  1 alex alex      583 2009-01-19 23:08 crashreporter-override.ini
drwxr-xr-x  5 alex alex     4096 2009-01-19 23:08 defaults
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 dictionaries
drwxr-xr-x  3 alex alex     4096 2009-01-19 23:08 extensions
-rwxr-xr-x  1 alex alex     3951 2009-01-19 23:08 firefox
-rwxr-xr-x  1 alex alex     7476 2009-01-19 23:08 firefox-bin
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 greprefs
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 icons
-rw-r--r--  1 alex alex      478 2009-01-19 23:08 libfreebl3.chk
-rwxr-xr-x  1 alex alex   292320 2009-01-19 23:08 libfreebl3.so
-rwxr-xr-x  1 alex alex    30920 2009-01-19 23:08 libjemalloc.so
-rwxr-xr-x  1 alex alex   603384 2009-01-19 23:08 libmozjs.so
-rwxr-xr-x  1 alex alex   200736 2009-01-19 23:08 libnspr4.so
-rwxr-xr-x  1 alex alex   960176 2009-01-19 23:08 libnss3.so
-rwxr-xr-x  1 alex alex   313676 2009-01-19 23:08 libnssckbi.so
-rwxr-xr-x  1 alex alex   119844 2009-01-19 23:08 libnssdbm3.so
-rwxr-xr-x  1 alex alex    77564 2009-01-19 23:08 libnssutil3.so
-rwxr-xr-x  1 alex alex    13180 2009-01-19 23:08 libplc4.so
-rwxr-xr-x  1 alex alex     8748 2009-01-19 23:08 libplds4.so
-rwxr-xr-x  1 alex alex   125644 2009-01-19 23:08 libsmime3.so
-rw-r--r--  1 alex alex      478 2009-01-19 23:08 libsoftokn3.chk
-rwxr-xr-x  1 alex alex   181776 2009-01-19 23:08 libsoftokn3.so
-rwxr-xr-x  1 alex alex   406596 2009-01-19 23:08 libsqlite3.so
-rwxr-xr-x  1 alex alex   160036 2009-01-19 23:08 libssl3.so
-rwxr-xr-x  1 alex alex    11816 2009-01-19 23:08 libxpcom.so
-rwxr-xr-x  1 alex alex 13012064 2009-01-19 23:08 libxul.so
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 modules
-rwxr-xr-x  1 alex alex    10772 2009-01-19 23:08 mozilla-xremote-client
-rw-r--r--  1 alex alex      112 2009-01-19 23:08 old-homepage-default.properties
-rw-r--r--  1 alex alex       45 2009-01-19 23:08 platform.ini
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 plugins
-rw-r--r--  1 alex alex      177 2009-01-19 23:08 README.txt
-rwxr-xr-x  1 alex alex    15767 2009-01-19 23:08 removed-files
drwxr-xr-x  6 alex alex     4096 2009-01-19 23:08 res
-rwxr-xr-x  1 alex alex    11410 2009-01-19 23:08 run-mozilla.sh
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 searchplugins
-rw-r--r--  1 alex alex      825 2009-01-19 23:08 Throbber-small.gif
-rwxr-xr-x  1 alex alex    69672 2009-01-19 23:08 updater
-rw-r--r--  1 alex alex      300 2009-01-19 23:08 updater.ini

---

### Post by alarikh on 2009-03-02
> **wilbbe01 said:**
> Are you trying to install firefox???  I'm confused?  Or are you just trying to install something but using firefox in the example?

trying install firefox

---

### Post by aysiu on 2009-03-02
Firefox already comes with Ubuntu.

If you have some strange reason for wanting to install the Mozilla build of it, though, here are step-by-step instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by kansasnoob on 2009-03-02
If you're trying to install Firefox (not sure why you want to get away from the repo version) just use Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I've personally tested it on all currently supported versions of Ubuntu as well as Linux Mint and Crunchbang!

It's simple! Just download it to your desktop (or where you want), double click it and it will install to synaptic! Then go to terminal and run:

```
ubuntuzilla.py -a install -p firefox

```

After answering a few simple questions you're done!

---

### Post by alarikh on 2009-03-02
> **aysiu said:**
> Firefox already comes with Ubuntu.

If you have some strange reason for wanting to install the Mozilla build of it, though, here are step-by-step instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Thx, but it problem with installation not just firefox/

---

### Post by kansasnoob on 2009-03-02
> **alarikh said:**
> Thx, but it problem with installation not just firefox/

Could you explain a bit more?

---

### Post by alarikh on 2009-03-02
> **kansasnoob said:**
> Could you explain a bit more?

I can't install files. after extraction, i think, it not configurate file , you can see it at my first note.

---

### Post by aysiu on 2009-03-02
> **alarikh said:**
> Thx, but it problem with installation not just firefox/
Then forget about .tar.gz files altogether and read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by taurus on 2009-03-02
> **alarikh said:**
> alex@alex-laptop:~/Desktop/firefox$ ls -la
total 16508
drwxr-xr-x 13 alex alex     4096 2009-01-19 23:08 .
drwxr-xr-x  7 alex alex     4096 2009-03-02 23:10 ..
-rw-r--r--  1 alex alex     2035 2009-01-19 23:08 application.ini
-rw-r--r--  1 alex alex        0 2009-01-19 23:08 .autoreg
-rwxr-xr-x  1 alex alex     1953 2009-01-19 23:08 blocklist.xml
-rw-r--r--  1 alex alex      232 2009-01-19 23:08 browserconfig.properties
drwxr-xr-x  3 alex alex     4096 2009-01-19 23:08 chrome
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 components
-rwxr-xr-x  1 alex alex    45096 2009-01-19 23:08 crashreporter
-rw-r--r--  1 alex alex     3558 2009-01-19 23:08 crashreporter.ini
-rw-r--r--  1 alex alex      583 2009-01-19 23:08 crashreporter-override.ini
drwxr-xr-x  5 alex alex     4096 2009-01-19 23:08 defaults
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 dictionaries
drwxr-xr-x  3 alex alex     4096 2009-01-19 23:08 extensions
**[COLOR="Blue"]-rwxr-xr-x  1 alex alex     3951 2009-01-19 23:08 firefox[/COLOR]**
-rwxr-xr-x  1 alex alex     7476 2009-01-19 23:08 firefox-bin
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 greprefs
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 icons
-rw-r--r--  1 alex alex      478 2009-01-19 23:08 libfreebl3.chk
-rwxr-xr-x  1 alex alex   292320 2009-01-19 23:08 libfreebl3.so
-rwxr-xr-x  1 alex alex    30920 2009-01-19 23:08 libjemalloc.so
-rwxr-xr-x  1 alex alex   603384 2009-01-19 23:08 libmozjs.so
-rwxr-xr-x  1 alex alex   200736 2009-01-19 23:08 libnspr4.so
-rwxr-xr-x  1 alex alex   960176 2009-01-19 23:08 libnss3.so
-rwxr-xr-x  1 alex alex   313676 2009-01-19 23:08 libnssckbi.so
-rwxr-xr-x  1 alex alex   119844 2009-01-19 23:08 libnssdbm3.so
-rwxr-xr-x  1 alex alex    77564 2009-01-19 23:08 libnssutil3.so
-rwxr-xr-x  1 alex alex    13180 2009-01-19 23:08 libplc4.so
-rwxr-xr-x  1 alex alex     8748 2009-01-19 23:08 libplds4.so
-rwxr-xr-x  1 alex alex   125644 2009-01-19 23:08 libsmime3.so
-rw-r--r--  1 alex alex      478 2009-01-19 23:08 libsoftokn3.chk
-rwxr-xr-x  1 alex alex   181776 2009-01-19 23:08 libsoftokn3.so
-rwxr-xr-x  1 alex alex   406596 2009-01-19 23:08 libsqlite3.so
-rwxr-xr-x  1 alex alex   160036 2009-01-19 23:08 libssl3.so
-rwxr-xr-x  1 alex alex    11816 2009-01-19 23:08 libxpcom.so
-rwxr-xr-x  1 alex alex 13012064 2009-01-19 23:08 libxul.so
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 modules
-rwxr-xr-x  1 alex alex    10772 2009-01-19 23:08 mozilla-xremote-client
-rw-r--r--  1 alex alex      112 2009-01-19 23:08 old-homepage-default.properties
-rw-r--r--  1 alex alex       45 2009-01-19 23:08 platform.ini
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 plugins
-rw-r--r--  1 alex alex      177 2009-01-19 23:08 README.txt
-rwxr-xr-x  1 alex alex    15767 2009-01-19 23:08 removed-files
drwxr-xr-x  6 alex alex     4096 2009-01-19 23:08 res
-rwxr-xr-x  1 alex alex    11410 2009-01-19 23:08 run-mozilla.sh
drwxr-xr-x  2 alex alex     4096 2009-01-19 23:08 searchplugins
-rw-r--r--  1 alex alex      825 2009-01-19 23:08 Throbber-small.gif
-rwxr-xr-x  1 alex alex    69672 2009-01-19 23:08 updater
-rw-r--r--  1 alex alex      300 2009-01-19 23:08 updater.ini

There is nothing to compile.  Just run the thing from that directory.

```
cd ~/Desktop/firefox
./firefox
```

---

### Post by stchman on 2009-03-02
> **alarikh said:**
> Hello, tried to install firefox after
 cd ~/Desktop
tar xjvf file .tar.gz2

Dont know how to install this another way, Thx

Mozilla uses .tar.bz2 not gz2.

First off if you downloaded Firefox from Mozilla's website they are pre-compiled binaries.  You can get the source, but it is in the developers area.

Second the latest Firefox(3.0.6) is in the repos.  If you want to use 3.1 beta then yes you will need to go to Mozilla.

To install the new Firefox this way(assumes you downloaded the archive to Desktop):

```

cd ~/Desktop
sudo tar -C /opt -xjvzf ~/Desktop/firefox*

```

This will unpack the archive into the /opt directory.  To run do this:

```
/opt/firefox/firefox
```

Hope this helps.

---

