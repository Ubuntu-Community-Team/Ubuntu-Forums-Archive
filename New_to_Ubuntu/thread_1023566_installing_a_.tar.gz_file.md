---
title: "installing a .tar.gz file"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by banerjeerupak on 2008-12-28
I have downloaded a software which i need to install. It is in the .tar.gz format. How am i supposed to install it.

---

### Post by dannytatom on 2008-12-28
Extract it, and there *should* be a README or one on the website you downloaded it from.

If not, try

```

./configure
make
make install

```

Better to look for a README, though, as not everything installs exactly the same.

---

### Post by howefield on 2008-12-28
tar.gz is a compressed archive, it depends on what is inside as to how you would install it.

What is the name of the file and where did you get it from ?

---

### Post by HotShotDJ on 2008-12-28
> **banerjeerupak said:**
> I have downloaded a software which i need to install. It is in the .tar.gz format. How am i supposed to install it.Typically, *.tar.gz files are source code for compiling.  This is a LAST resort for installing software, and probably unnecessary.  Exactly what is the software you are trying to install.  Have you checked Applications --> Add/Remove or System --> Administration --> Synaptic Package Manager to see if it is already included in the repositories?

---

### Post by Michael.Godawski on 2008-12-28
hey banerjeerupak,

the other posters are so right.
Have a look here:

[LIST]
[*][http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)
[/LIST]
Installing via tar files is / should be the last option. 

Tell us what application you  want to install please.

---

### Post by banerjeerupak on 2008-12-28
It is a pdf creator software. i tried the configure command. But its not working. There is some configure error.

What other information should i provide to you so that my problem can be solved.

---

### Post by banerjeerupak on 2008-12-28
[http://linux.softpedia.com/progDownload/Indexed-PDF-Creator-Download-1071.html](http://linux.softpedia.com/progDownload/Indexed-PDF-Creator-Download-1071.html)

This is the software that i want to install. Please guide me.

---

### Post by dannytatom on 2008-12-28
Copy/paste the error for us, please. :)

**Edit:** see ya post the link 'til after I posted.

---

### Post by banerjeerupak on 2008-12-28
root@blitzkreig:/home/rupak/softies/ipdf-1.0.0# make install
make: *** No rule to make target `install'.  Stop.
root@blitzkreig:/home/rupak/softies/ipdf-1.0.0# ./configure install
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for install-gcc... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... Invalid configuration `install': machine `install' not recognized
configure: error: /bin/bash ./config.sub install failed
root@blitzkreig:/home/rupak/softies/ipdf-1.0.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for png_read_info in -lpng... yes
checking for TIFFClose in -ltiff... yes
checking for gzclose in -lz... yes
checking for PDF_boot in -lpdf... no
configure: error: Could not find libpdf.  Get it at [www.pdflib.com](www.pdflib.com)

---

### Post by Michael.Godawski on 2008-12-28
OK, this is from the read me file:

> INSTALL

Installation works just like other autoconf style projects.  [B]Run configure,
make, and make install. [/B] If everything works out you're done.  The most
likely problem is that you'll** need to install pdflib**.  If you don't have it,
**get it at [http://www.pdflib.com](http://www.pdflib.com),** download and install, and then come back to
build ipdf.

Usually you have to do this:

navigate to the extracted folder, which should be on your Desktop. We will use the terminal to navigate and run the commands:
```
cd /Desktop/ipdf-1.0.0
```

Then run these commands:

```
./configure
make 
sudo make install
```

If you get any error messages tell us.

---

### Post by howefield on 2008-12-28
Looks like you need pdflib as per your error and readme file.

"Installation works just like other autoconf style projects.  Run configure,
make, and make install.  If everything works out you're done.  The most
likely problem is that you'll need to install pdflib.  If you don't have it,
get it at [http://www.pdflib.com](http://www.pdflib.com), download and install, and then come back to
build ipdf".

---

### Post by dannytatom on 2008-12-28
Also, run:

```

./configure
make
make install

``` 

one at a time, on their own lines.  I saw you tried doing ./configure install earlier, that won't work.

---

