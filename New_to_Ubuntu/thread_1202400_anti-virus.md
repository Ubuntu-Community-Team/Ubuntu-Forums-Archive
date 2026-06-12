---
title: "anti-virus?"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by adkjoe on 2009-07-02
So do any of you guys or gals use anykind of anti-virus software or is Ubuntu safe?  Any suggestions on what to use or if I even need it? thanks!

---

### Post by WRDN on 2009-07-02
You don't need any antivirus applications, because, there are no known viruses 'in the wild' for Linux. The only reason to use antivirus is if you share files with a Windows partition/drive/ users. Ubuntu/Linux cannot be infected by viruses, but they can transport them.

If you want an antivirus appliation, look at ClamAV (in the repositories). ClamTK is the graphical frontend to it, ClamAV is the antivirus engine, and clamscan is the command line scanner.

---

### Post by adkjoe on 2009-07-02
I don't use windows at all. only Ubuntu so I guess I don't have to worry then. thanks!

---

### Post by khelben1979 on 2009-07-02
[Linux malware - Wikipedia]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")

---

### Post by a2z on 2009-07-02
Isn't Linux  **GREAT**!:popcorn:

---

### Post by khelben1979 on 2009-07-02
> **a2z said:**
> Isn't Linux  **GREAT**!:popcorn:

It sure is! =D>

---

### Post by adkjoe on 2009-07-02
Thanks guys, much appreciated!

---

### Post by decoherence on 2009-07-02
A moment for humour...

```


decoherence@workstation1:~$ cat evilmalware/INSTALL

evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1) 

```

---

### Post by QIII on 2009-07-02
Great gag, decoherence!

However, I would like to add my bit of warning to those who don't anticipate Pearl Harbor.

There IS Linux malware in the wild.  It is just not very common.  YET.

The malware that exists is primarily targeted at server platforms and not at personal computers.  YET.

However, it can be said that the two chief vectors for the spread of, and subsequent infection by, viruses -- ActiveX and Internet Explorer -- are foreign to Linux.

We can be carriers.

And it would not be wise for us to be convinced of our invincibility until we are forced to recognize our vulnerability because of the brainchild of some PFY with too much time on his hands.

---

