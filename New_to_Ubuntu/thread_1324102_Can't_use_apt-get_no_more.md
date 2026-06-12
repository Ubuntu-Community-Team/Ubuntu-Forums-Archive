---
title: "Can't use apt-get no more"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by zelalem on 2009-11-12
Hi, yesterday I was trying to install a software on ubuntu hardy machine and everything got broken. I can't no longer use apt-get. I get an error that says 
apt-get: /usr/local/lib/libgcc_s.so.1: version 'GCC_4.2.0' not found (required by /usr/local/lib/libstdc++.so.6). 
You know I was changing different things and I don't know what caused this. Originally I was getting an error that looks like the following
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
......
apt-get: relocation error: apt-get: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13ba sic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6

Then aas the above link was pointing to a file in another folder, I copied libstdc++.so.6.0.9 file from /usr/local/lib to /usr/lib. And I started to get the above erro messge afterwards. 

when I try to install the packages (GCC_4.2.0) manually using libstdc++6_4.2.4-1ubuntu3_i386.deb package, I got the following error:
ldconfig deffered processing now taking place
/sbin/ldconfgig.real: /usr/lib/libavdevice.so.52 is not a symbolik link. I don't really what to do. I have so many packages installed on my machine and don't want to re-install everything. I think can't also configure libraries (can't use ldconfig). Pls help me.

Thank you.

Zelalem

---

### Post by zelalem on 2009-11-12
The error related to ldconfig (which is /sbin/ldconfgig.real: /usr/lib/libavdevice.so.52 is not a symbolik link) seems to be solved. I copied a file named libavdevice.so.52.0.0 from anotehr PC and made the previous file a link to the new file. Now I can issue ldconfig and I get no error. I also had difficulty installing the dependencies for the libstdc++6... package(paritcularly the dev package of this file and the g++ packages were depending on each otehr - a kind of circular dependency). I then issued the "dpkg -i" together with the two package names and now I installed them. But I couldn't install the actual file (libstdc++6_4.2.4-1ubuntu3_i386. There is no error message but at the end it says "
"processing triggers for libc6.......
ldconfig deffered processing now taking place"

And I still get the same error. What can I do? Why can't I install this package? Please help me.

---

### Post by zelalem on 2009-11-12
Hi guys, it is working now. I followed the following link (especially the comment by phizzzt ) and apt-get is now working.

[http://ubuntuforums.org/archive/index.php/t-270605.html](http://ubuntuforums.org/archive/index.php/t-270605.html)

I changed the name of the file that was creating teh problem (i.e. /usr//local/lib/libgcc_s.so.1) to anotehr file and created a symbolic link as specified by the above person.

Cheers!

---

### Post by philinux on 2009-11-12
This is turning into a self help forum today :lolflag:

---

### Post by zelalem on 2009-11-13
Hi, pilinux, actually I still have the problem in another way. As I said I was trying to fix the problem by installing a debian package manually. So, you know after I removed some of the packages using apt-get remove, they were still there (particularly I couldn't remove g++ package). The problem is that after I remove it when i say "g++ --version" it used to give me a version info. after a long trial i found out that there was a file in the bin directory which was refered so i removed it. I also had the same problem with gcc.  so now they both are the correct versions, but now when i try to compile anotehr package i got teh following error:
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
etc.
So, my suspision is that there are some reminants left from the package that i installed yesteday (as part of my trial and error process i had installed libgcc1_4.2.4-1ubuntu3_i386.deb).
Do you know how I can fix this problem.

Thank you.

Zelalem

---

### Post by ukripper on 2009-11-13
Problem with this thread is - real info is cluttered. it is hard to separate any readable details. please next time post terminal output in Quotes using message tools.

---

