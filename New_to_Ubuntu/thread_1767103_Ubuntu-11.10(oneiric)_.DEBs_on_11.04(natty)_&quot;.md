---
title: "Ubuntu-11.10(oneiric) .DEBs on 11.04(natty) &quot;E: Unable to locate package algol68g&quot;"
date: 2011-05-25
forum: New to Ubuntu
---

### Post by NevilleDNZ on 2011-05-25
In summary: I was hoping to try out the following "hello world" program with the packaged "Algol 68 compiler-interpreter" on Ubuntu:
```
#!/usr/local/bin/a68g --script #
printf($"Hello, world!"l$)
``` But it appears a precompiled Algol68 is unavailable on "natty" (Ubuntu-11.04).
> # apt-get install algol68g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package algol68g
There is a "natty" man page for Algol68: [ [http://manpages.ubuntu.com/manpages/natty/en/man1/a68g.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/a68g.1.html) ]
¢ note: I normally use yum/Fedora and get a bit lost on apt-get/Ubuntu ¢

---------------------------------------------------------------------

I then noticed the natty man page actually diverts to Ubuntu version "oneiric" (Ubuntu-11.10) man page (odd): [ [http://manpages.ubuntu.com/manpages/oneiric/en/man1/a68g.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/a68g.1.html) ]

A bit more googling and I found the Ubuntu source and a binary for oneiric: [ [https://launchpad.net/ubuntu/oneiric/+package/algol68g](https://launchpad.net/ubuntu/oneiric/+package/algol68g) ]

But none for natty: [ [https://launchpad.net/ubuntu/natty/+search?text=algol68g](https://launchpad.net/ubuntu/natty/+search?text=algol68g) ]
> No packages matching 'algol68g' are published in Natty. 

So...

I guess "+" on "+package" mean algol68 is candidate/experimental (or extra) on oneiric?

Maybe one can add launchpad.net to /etc/apt/sources.list.d to automate this, but avoid upgrading EVERYTHING from "oneiric" (Ubuntu-11.10) into "natty" (Ubuntu-11.04).

Hints appreciated
NevilleDNZ

---

### Post by meborc on 2011-05-25
what about grabbing a .deb file and installing that way?

[http://sourceforge.net/projects/algol68/files/algol68g/](http://sourceforge.net/projects/algol68/files/algol68g/)

---

### Post by NevilleDNZ on 2011-05-25
The debian .deb file from sourceforge works great, it is a copy from [ [http://packages.debian.org/sid/algol68g](http://packages.debian.org/sid/algol68g) ].

```
root@narwhal:~# dpkg -i /tmp/algol68g_2.1.2-1_i386.deb 
Selecting previously deselected package algol68g.
(Reading database ... 131160 files and directories currently installed.)
Unpacking algol68g (from /tmp/algol68g_2.1.2-1_i386.deb) ...
Setting up algol68g (2.1.2-1) ...
Processing triggers for man-db ...
```
Output:
```
owner@narwhal:~$ cat Hello_world.a68 
#!/usr/bin/a68g --script #
BEGIN
  printf($"Hello, world!"l$)
END

owner@narwhal:~$ chmod +x Hello_world.a68 

owner@narwhal:~$ ./Hello_world.a68 
Hello, world!
```

I am thinking that the Ubuntu's oneiric verion will also work on natty: [ [https://launchpad.net/ubuntu/oneiric/+package/algol68g](https://launchpad.net/ubuntu/oneiric/+package/algol68g) ]

I will figure out the grand layout of ubuntu repositories and grander questions about dependances as I go.

BTW: The debian packages repository has .deb builds for some 16 other architectures... including bsd **AND** hurd!!
[LIST]
[*] alpha - [http://packages.debian.org/sid/alpha/algol68g/download](http://packages.debian.org/sid/alpha/algol68g/download)
[*] amd64 - [http://packages.debian.org/sid/amd64/algol68g/download](http://packages.debian.org/sid/amd64/algol68g/download)
[*] armel - [http://packages.debian.org/sid/armel/algol68g/download](http://packages.debian.org/sid/armel/algol68g/download)
[*] hurd-i386 - [http://packages.debian.org/sid/hurd-i386/algol68g/download](http://packages.debian.org/sid/hurd-i386/algol68g/download)
[*] i386 - [http://packages.debian.org/sid/i386/algol68g/download](http://packages.debian.org/sid/i386/algol68g/download)
[*] ia64 - [http://packages.debian.org/sid/ia64/algol68g/download](http://packages.debian.org/sid/ia64/algol68g/download)
[*] kfreebsd-amd64 - [http://packages.debian.org/sid/kfreebsd-amd64/algol68g/download](http://packages.debian.org/sid/kfreebsd-amd64/algol68g/download)
[*] kfreebsd-i386 - [http://packages.debian.org/sid/kfreebsd-i386/algol68g/download](http://packages.debian.org/sid/kfreebsd-i386/algol68g/download)
[*] mips - [http://packages.debian.org/sid/mips/algol68g/download](http://packages.debian.org/sid/mips/algol68g/download)
[*] mipsel - [http://packages.debian.org/sid/mipsel/algol68g/download](http://packages.debian.org/sid/mipsel/algol68g/download)
[*] powerpc - [http://packages.debian.org/sid/powerpc/algol68g/download](http://packages.debian.org/sid/powerpc/algol68g/download)
[*] powerpcspe (unofficial port) - [http://packages.debian.org/sid/powerpcspe/algol68g/download](http://packages.debian.org/sid/powerpcspe/algol68g/download)
[*] s390 - [http://packages.debian.org/sid/s390/algol68g/download](http://packages.debian.org/sid/s390/algol68g/download)
[*] sh4 (unofficial port) - [http://packages.debian.org/sid/sh4/algol68g/download](http://packages.debian.org/sid/sh4/algol68g/download)
[*] sparc - [http://packages.debian.org/sid/sparc/algol68g/download](http://packages.debian.org/sid/sparc/algol68g/download)
[*] sparc64 (unofficial port) - [http://packages.debian.org/sid/sparc64/algol68g/download](http://packages.debian.org/sid/sparc64/algol68g/download)
[/LIST]

ThanX
NevilleDNZ

---

### Post by Jerry N on 2011-05-25
I learn something new everyday!  I had assumed that Algol died decades ago.

Jerry

---

### Post by NevilleDNZ on 2011-05-25
> **Jerry N said:**
> I learn something new everyday!  I had assumed that Algol died decades ago.

FYI: Check out ... [ [ Stackoverflow: Was Algol ever used for &#8220;mainstream&#8221; programming?]("http://stackoverflow.com/questions/1463321/was-algol-ever-used-for-mainstream-programming") ]

Algol 58 (In the form of [ [JOVIAL]("http://en.wikipedia.org/wiki/JOVIAL") ]) is  deployed in the US & UK military and aviation industry. UK, US [ [NAS]("http://en.wikipedia.org/wiki/National_Airspace_System") ] & Republic of China. eg. [ [=7&tx_ttnews[mode]=1"]Budget cuts kill Miami CPDLC trials]("http://www.ainonline.com/ain-and-ainalerts/aviation-international-news/single-publication-story/browse/0/article/budget-cuts-kill-miami-cpdlc-trials-10470/?no_cache=1&tx_ttnews[story_pointer) ]

IIRC the JOVAIL system at NAS was (due to be) phased out of the US a year ago.  Replaced by [ERAM]("http://en.wikipedia.org/wiki/ERAM") - c.f. [ [More Signficant ERAM Problems]("http://atcfreqs.com/wpblog/?p=3355") ].

The Soviet military used Algol "somewhere"... the only good example I know of was the [Soviet Shuttle]("http://en.wikipedia.org/wiki/Buran_program") where Algol was in the automated landing system on the shuttles maiden/only flight. I have spotted a few other, eg the Soviet [ [BESM/&#1041;&#1069;&#1057;&#1052;]("http://www.mailcom.com/besm6/runit.cgi") ] (something like "Big Electronic-Calculating Machine")

Algol68 is a total revamp of Algol60.  ¢ Maybe Algol68 should have been given different name. ¢ The British Military were first to adopt this evolution of Algol.  "Some" UK code had been "public domained" under Crown Copyright.  eg The bulk of Royal Radar's [ [ALGOL 68RS]("http://sourceforge.net/projects/algol68/files/algol68toc/") ] compiler itself, [ [TenDRA]("http://en.wikipedia.org/wiki/TenDRA_Compiler") ] and [ELLA]("http://en.wikipedia.org/wiki/ELLA_(programming_language)") ) but the bulk is military and still under wraps. 

There are **still** a few civilian uses of Algol68 in the UK as a result of ICL using it to write a the [ [VME Operating System]("http://en.wikipedia.org/wiki/ALGOL_68#Operating_Systems_written_in_ALGOL_68") ] and providing their compilers to customers in the Insurance and Custom Industry.

Having said all the above... Algol68 is *rather* "old hat" (likewise it is *rather* "space aged") the principle new use for Algol68 post [ [cold war]("http://en.wikipedia.org/wiki/Cold_War") ] is for [recreational hacking]("http://rosettacode.org/wiki/User:NevilleDNZ#ALGOL_68_Contributions").  So I'd love to get my hand on the source code to [[ICL's VME]("http://en.wikipedia.org/wiki/ICL_VME") ]! ¢ [ *[Google Chrome OS]("http://en.wikipedia.org/wiki/Google_Chrome_OS")* ] eat your heart out!!! ¢

NJoy
NevilleDNZ

---

### Post by NevilleDNZ on 2011-05-25
Blanked.

---

### Post by Jerry N on 2011-05-26
I remember Jovial.  _J_ules _O_wn _V_ersion of the _I_nternational _A_lgorithmic _L_anguage, if my memory serves me correctly, which it does occasionally.

Jerry

---

