---
title: "oracle? how to install.."
date: 2009-07-19
forum: New to Ubuntu
---

### Post by levis lover on 2009-07-19
i have ubuntu 9.04 and oracle 9i..
i want to install oracle.. how can i do it ?

is there any way i cn download oracle from the repositories like we do with the other softwares??

---

### Post by 3rdalbum on 2009-07-19
Most users here can't afford any Oracle products, so we're not going to know the specific installation instructions for this software.

Try reading the installation instructions and following them as best as you can, and if you get stuck post to this thread with the instructions and what you're getting stuck on.

---

### Post by dizwell on 2009-07-29
You don't want to muck about with Oracle 9i. It's a long-since de-supported version. Current versions are 10g and 11i. Both are available completely and utterly free of charge, provided you are going to use them for experimenting, learning and testing out ideas. The minute you want to put them into a production environment, they would cost a lot of money... but until then, download and use them freely from:

[http://www.oracle.com/technology/software/products/database/index.html](http://www.oracle.com/technology/software/products/database/index.html)

With a fresh install of 32-bit Ubuntu and your new copy of 10g or 11g, you could do worse than use my doris script to help automate the preparations needed to make an Oracle install happen. That's downloadable from:

[http://www.diznix.com/wp-content/uploads/2009/06/doris1.1g.sh](http://www.diznix.com/wp-content/uploads/2009/06/doris1.1g.sh)

You basically save that on your file system somewhere, run it as sudo whilst connected to the Internet, and all the kernel settings and packages required to make Oracle work are done for you. You then log on as the oracle user, insert your Oracle installation media, and run the runInstaller application. Works perfectly. 

And if it's 64-bit Oracle on 64-bit Ubuntu you are after, then try reading this:

[http://diznix.com/2009/07/27/64-bit-oracle-on-64-bit-ubuntu/](http://diznix.com/2009/07/27/64-bit-oracle-on-64-bit-ubuntu/)

That still produces an error during the linking (compiling) phase, but it's nothing much to worry about.

Anyway: have fun with it. You're running on Ubuntu, which isn't a supported distro, so this is definitely not going to be for production-quality work. But it works fine anyway, and it's good to get it working on *your* choice of distro rather than Oracle's.

(PS, I am sure someone will recommend you install Oracle XE, which is a completely free of charge cut-down version of Oracle, for which a .deb package is actually provided. You are limited to 4GB of data, 1GB RAM and 1CPU, but if that suits you, fine. Personally, I'd always recommend learning Oracle with the full-blown Enterprise/Standard Editions, which are just as free for learning purposes but completely uncrippled. Your choice, though).

---

