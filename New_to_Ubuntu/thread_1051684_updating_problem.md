---
title: "updating problem"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by whatispaintball on 2009-01-27
hello everybody. I am totally new to ubuntu and i ran into a little problem.  I downloaded all the updates as the update manager suggests, but when i tried to install them, it gives me an error.  i am not sure what i should do.

var/cache/apt/archives/perl_5.10.0-11.1ubuntu2.2_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/perl/5.10.0/auto/Compress/Raw/Zlib/Zlib.so')
E: /var/cache/apt/archives/libperl5.10_5.10.0-11.1ubuntu2.2_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/perl-base_5.10.0-11.1ubuntu2.2_amd64.deb: subprocess dpkg-deb --control returned error exit status 2

thanks for all the help..

---

### Post by istoff on 2009-01-27
Can you describe in more detail how you did the download and update?

Did you use the graphical tools for everything or use the command line?

Have you tried doing the following

sudo apt-get update

sudo apt-get upgrade

from the commandline??

You will be prompted for your password when you do the above commands

---

