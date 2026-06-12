---
title: "[SOLVED] rTorrent from svn help"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by BurkDP on 2008-08-29
I'm running Hardy, currently updated, and I'm having trouble with rTorrent compiled from the svn. I compiled it from the latest svn because the one in the repositories is an older version that I was having problems with, and it has been working well for the past couple of months. I got the information on how to from this guide at howtoforge: [[COLOR="RoyalBlue"]HowTo Compile rTorrent From SVN In Ubuntu 8.04 Hardy Heron[/COLOR]]("http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron").

My problem is that the most recent svn update won't compile, and it's broken my current install. The client will start up but it's frozen and I have to kill it (fortunately I run it in screen so I haven't had to reboot b/c of a locked up display).

**Works**
[LIST=1]
[*]svn up
[*]cd libtorrent
[*]./autogen.sh
[*]./configure
[*]make
[*]sudo make install
[*]echo "include /usr/local/lib" | sudo tee -a /etc/ld.so.conf
[*]sudo ldconfig
[*]cd ../rtorrent
[*]./autogen.sh
[*]./configure
[COLOR="Red"][*]make <-- **Problem Occurs Here**[/COLOR]
[*]sudo make install
[/LIST]

The libtorrent compiles fine and installs, this error occurs when it tries to compile rTorrent:

```
make  all-recursive
make[1]: Entering directory `/home/danielburk/rtorrent-dev/rtorrent'
Making all in doc
make[2]: Entering directory `/home/danielburk/rtorrent-dev/rtorrent/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/danielburk/rtorrent-dev/rtorrent/doc'
Making all in src
make[2]: Entering directory `/home/danielburk/rtorrent-dev/rtorrent/src'
Making all in core
make[3]: Entering directory `/home/danielburk/rtorrent-dev/rtorrent/src/core'
make[3]: *** No rule to make target `curl_socket.o', needed by `libsub_core.a'.  Stop.
make[3]: Leaving directory `/home/danielburk/rtorrent-dev/rtorrent/src/core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/danielburk/rtorrent-dev/rtorrent/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/danielburk/rtorrent-dev/rtorrent'
make: *** [all] Error 2

```


I should have all of the dependencies (including curl), and definitely have all the ones listed in the guide. I did try "make clean" on the odd chance that'd fix it. 

My question: Does anybody know how to fix this? If not, how do I unistall/get rid of it? (I can't use apt b/c it wasn't installed via a .deb)

All that I know about Linux has been self taught, and I don't have any programming experience so I'd appreciate explicit instructions - Though **any** response would be appreciated. I did look for an official rTorrent forum but couldn't find one, so I posted here in the amazingly helpful Ubuntu forums.

Thank you for taking the time to read my post.

---

### Post by asezen on 2008-08-30
Exactly same problem here, If anybody think to help please let me know so i can give more details.


Error:
"No rule to make target `curl_socket.o', needed by `libsub_core.a'. Stop"

---

### Post by ekettunen on 2008-08-30
Hi,

This seems to be a known error on rTorrent's tracker: [Bad Makefile after libcurl Change](http://libtorrent.rakshasa.no/ticket/1444). I'm quite sure it'll be solved in next SVN revision.

---

### Post by BurkDP on 2008-08-30
Thank you

---

### Post by asezen on 2008-08-30
Thanks ekettuken, r1064 solve the problem but now i start to get this error, i post details to here [http://libtorrent.rakshasa.no/ticket/1418](http://libtorrent.rakshasa.no/ticket/1418) .

Thanks

---

