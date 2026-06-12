---
title: "Bradford Networks CSA"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by metalhawk83 on 2008-05-30
So I've been trying to register my brand new ubuntu box in the university's network. They use the Bradford networks system and it requires that every pc has the Client Security Agent installed on it (checks for appropriate anti-virus and updates). After downloading the CSA.sh and "chmod +x" it, I run the script (./CSA.sh,both with sudo and without),get a bunch of error messages, it tries to open up a browser window to display the results but gives a "cannot find CSA.tmp" and nothing else happens. As a result, I can't connect to the network,which supposedly supports Ubuntu pc's (a bunch of other guys use it here but everyone is now gone for the summer).

Anybody have any ideas?? :confused:

---

### Post by Sam Lars on 2008-05-30
Could you give us the errors you get?

---

### Post by metalhawk83 on 2008-06-01
stamatis@opencomputer:~/Desktop$ chmod +x CSA.sh

stamatis@opencomputer:~/Desktop$ sudo ./CSA.sh

mkdir: cannot create directory `.CSA.TEMP': File exists
./
engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
./
CSA.sh: 12: function: not found
./
CSA.sh: 18: mozilla: not found
./
CSA.sh: 18: mozilla: not found
./
CSA.sh: 19: function: not found
./
CSA.sh: 25: netscape: not found
./
CSA.sh: 25: netscape: not found
./
CSA.sh: 26: function: not found
./
CSA.sh: 30: function: not found
./
CSA.sh: 33: epiphany: not found
./
CSA.sh: 34: function: not found
./
CSA.sh: 37: konqueror: not found
./
CSA.sh: 38: function: not found
./
CSA.sh: 46: seamonkey: not found
./
CSA.sh: 46: seamonkey: not found
./
CSA.sh: 47: function: not found
./
CSA.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.

rm: cannot remove `tmp.csa': No such file or directory

This is what I get...

---

### Post by aos101 on 2008-06-01
There's this previous thread where someone else was having trouble with the script.  Might be of some help:

[http://ubuntuforums.org/showthread.php?t=398689](http://ubuntuforums.org/showthread.php?t=398689)

---

### Post by metalhawk83 on 2008-06-03
I finally figured it all out! Just for future reference for anyone running into a similar problem, you just need to install libstd c++ v.5 and it works perfectly. You still get some errors in the console but at least it lets you register on the network. It seems that the newer versions of Ubuntu have v.6 pre-installed, but Bradford CSA needs v.5. It was actually this line that gave me the hint:

" error while loading shared libraries: libstdc++.so.5: "

I hope this proves usefull!!

---

### Post by epq on 2008-09-27
Hey,

I have the same problem with CSA and am trying to install libstd c++ v.5 but am running into difficulties with the dependencies of the necessary files.

I am not able to connect my laptop directly to the net so I have to download them individually on a different computer. 

On installing them, however, it seems that g++-3.3 depends on libstdc++5-3.3-dev and visa versa.

How does one overcome this?

Many thanks.

---

### Post by epq on 2008-09-27
I have sorted out the dependancy problem and installed libstd c++ v.5 but I now get a segmentation fault when I execute CSA.sh.

I would really appreciate any help you could give.

---

### Post by metalhawk83 on 2008-11-06
Why don't you try a newer version of g++ and see what happens?

---

