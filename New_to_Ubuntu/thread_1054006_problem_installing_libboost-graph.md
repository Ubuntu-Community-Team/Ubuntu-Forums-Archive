---
title: "problem installing libboost-graph"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by david.mountain on 2009-01-29
Hi

My setup is Ubuntu 8.04, with apache2, php5 and postgresql83.

I now need to install the libboost-graph* package (for pgrouting - see [http://pgrouting.postlbs.org/wiki/1.x/InstallationUbuntu804](http://pgrouting.postlbs.org/wiki/1.x/InstallationUbuntu804)).

When I run:
  * sudo apt-get install libboost-graph*
I get the message

=====================================

root@ubuntu:~# sudo apt-get install libboost-graph*

Reading package lists... Done Building dependency tree Reading state information... Done Note, selecting libboost-graph-dev for regex ‘libboost-graph*’ Note, selecting libboost-graph1.34.1 for regex ‘libboost-graph*’ Note, selecting libboost-graph1.35.0 for regex ‘libboost-graph*’ Note, selecting libboost-graph1.35-dev for regex ‘libboost-graph*’ Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

    The following packages have unmet dependencies.

        libboost-graph1.35-dev: Depends: libboost1.35-dev (= 1.35.0-8ubuntu1) but it is not going to be installed

            Depends: libboost-serialization1.35-dev (= 1.35.0-8ubuntu1) but it is not going to be installed Depends: libboost-test1.35-dev (= 1.35.0-8ubuntu1) but it is not going to be installed Conflicts: libboost-graph-dev but 1.34.1-11ubuntu1 is to be installed

E: Broken packages

===================================== 

I've searched, but not turned up anything on this. Does anyone have any advice on how to resolve?

Many thanks
David

---

### Post by david.mountain on 2009-02-17
An update on this bug. Several others have reported it on the same [discussion thread]("http://pgrouting.postlbs.org/discussion/21/208").

The latest posting suggests the bug has been id'd and a fix found.

[QUOTING DISCUSSION POST]
_____________________________________________
I had the same error with Debian Lenny.

That file belongs to libboost-dev $dpkg -S /usr/include/boost/pending/relaxed_heap.hpp libboost-dev: /usr/include/boost/pending/relaxed_heap.hpp

and it turns out the bug has just been fixed in the Debian package libboost-dev_1.34.1-15_i386 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=495204](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=495204)

I suppose the same has/will occur with the Ubuntu package.

pgRouting compiles fine afterwards
_____________________________________________


Does anyone know if/when a fix will be available for ubuntu 8.10?

Many thanks
David

---

