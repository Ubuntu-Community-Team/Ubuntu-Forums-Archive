---
title: "install help"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by Zaikin786 on 2011-01-22
I am trying to download MIT scheme  but when i try to install this(below) happens. I would love any help. thanks
this is what instructions i had been following.

[http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user/Unix-Installation.html#](http://www.gnu.org/software/mit-scheme/documentation/mit-scheme-user/Unix-Installation.html#)

zaikin@Zaikin-HP:~/Programming/mit-scheme-9.0.1/src$ sudo make install
/bin/bash ./microcode/mkinstalldirs /usr/local/lib/mit-scheme-x86-64
/usr/bin/install -c --preserve-timestamps -m 644 ./etc/optiondb.scm /usr/local/lib/mit-scheme-x86-64/.
/usr/bin/install -c --preserve-timestamps -m 644 lib/*.com /usr/local/lib/mit-scheme-x86-64/.
etc/make-in-subdirs.sh install microcode runtime compiler cref sf star-parser edwin imail sos ssp xml
run_cmd: make install
make[1]: Entering directory `/home/zaikin/Programming/mit-scheme-9.0.1/src/microcode'
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-x86-64
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-x86-64/lib
/bin/bash ./mkinstalldirs /usr/local/lib/mit-scheme-x86-64
/bin/bash ./mkinstalldirs /usr/local/bin
/usr/bin/install -c --preserve-timestamps scheme /usr/local/bin/mit-scheme-x86-64
/usr/bin/install: cannot stat `scheme': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/zaikin/Programming/mit-scheme-9.0.1/src/microcode'
make: *** [install-standard] Error 2
zaikin@Zaikin-HP:~/Programming/mit-scheme-9.0.1/src$

---

### Post by ubudog on 2011-01-22
And you already ran ./configure, etc?

---

### Post by 123456789123456789123456 on 2011-01-22
I don't know much about this program, but from what I read, it sounds like you may not have all supporting files needed installed.

what was the command you used to get this process started?
was the file a .deb?
or did you go through the anual make procedures?
if you went through the make procedures, did you use the make config?

---

### Post by Paqman on 2011-01-22
There's no need to compile it from scratch, MIT-scheme is available in the repos. You can install it through Ubuntu Software Centre, Synaptic, or the terminal.

---

### Post by Zaikin786 on 2011-01-22
@ ubudog Yes i ran ./config and everything
@1234  yea i went through and did all that and there is no .deb as far as i know
@ Paqman could you give me a name of a repo , cant seem to find one, just installed Synaptic and looking through that, do packages change between ubuntu and kubuntu (its what I have)

---

### Post by Paqman on 2011-01-22
> **Zaikin786 said:**
> 
@ Paqman could you give me a name of a repo , cant seem to find one, just installed Synaptic and looking through that, do packages change between ubuntu and kubuntu (its what I have)

It's in the Universe repo, which I believe may not be enabled by default. In Synaptic, go to Settings > Repositories, enable Universe and then hit reload. Package names are the same for all versions of Ubuntu, since they all use the same repos.

---

### Post by Zaikin786 on 2011-01-22
Thanks Paqman

---

