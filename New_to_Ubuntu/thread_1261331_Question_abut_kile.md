---
title: "Question abut kile"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Mehrdad2009 on 2009-09-08
Hi
I have downloaded "kile-2.1b2.tar.bz2"and it included REDME file .
Content of this README file is:
Dear User/Packager,

this Readme is targeted towards people who want to build Kile from source 

or plan to create binary packages.
If you have created a package, please drop us a note ( kile-

[email]devel@lists.sourceforge.net[/email] ) so that we can promote your package.

1.) Checking dependencies
============================

- KDE 4.2/4.3 and according QT development packages (ForwardDVI 

only works with KDE 4.3)
- cmake 2.6.2
- gcc 3.x/4.x

2.) Building Kile from source
============================

- Extract the source code with "tar xjf kile-x.tar.bz2"
- Create a "kile-

build" directory somewhere for an out-of-source build.
- Enter the "kile-build" directory and call 

cmake with:
  " cmake <path to the kile directory> -DCMAKE_INSTALL_PREFIX=$HOME/.kde 

-DCMAKE_BUILD_TYPE="Debugfull" "
- Type "make -j 2" to compile the package.
- Type "make 

install -j 2" to install the programs, data files and documentation.
- Type "kile" and enjoy the power 

of LaTeX together with the joy of using Kile :)

2.1.) Building Documentation
============================

The documentation will automatically be built provided that the 

documentation files
are located in the following directories:
<kile-root>
           /doc                                   

for the standard documentation and
                                                  accompanying image files

           

/translations
                        /<language>
                                   /doc           for the translated documentation 

and
                                                  images in language <language>

                                   /messages      for the 

translated message catalogs
                                                  in language <language>

Please note that 

every docbook must be called "index.docbook" and that only PNG image
files can be used. 

Furthermore, message catalogs must be called "kile.po".

When the "doc" and "translations" 

directories are found, the build targets "docbooks"
and "translations" will be generated for the 

compiling of the documentation.

2.3.) Special Flags for the build
===============================
The 

flag "KILE_VERSION" can be set in the CMake cache to specify the installation
directory of basic 

documentation files (README, AUTHORS, ChangeLog,...), i.e. they
will be installed in 

"share/doc/kile-${KILE_VERSION}/" instead of "share/doc/kile/".

3.) Using Kile
===============================

To use Kile you (obviously) need some external programs.
The 

following list is divided into basic, advanced and additional usage.

Basic:
- TeXLive 2005/2007/2008 

(Including "AMS"-Packages and the documentation).
  This add among others the following 

programs:
    - Tex/LaTeX
    - PDFLaTeX
    - XeLaTeX
    - ConTeXt
    - BibTeX
    - MakeIndex
- 

Okular (DVI, PS, PDF Viewer from KDE)

Advanced:
- Acroread (Viewing PDF)
- Imagemagick, 

DVIPNG 1.7 (Bottom bar preview)

By default there are also tools for the following programs 

defined:
- Tar/zip/gzip/bzip2 (Archive)
- DBlatex (Docbook to LaTeX)
- Metapost and Asymptote
- 

Latex2html (LaTeX to Web)
- Tex4ht (LaTeX to Web)
- Xindy (MakeIndex replacement)
- Lilypond 

(Music Typesetting)
- Konqueror/Mozilla/Firefox (Viewing HTML)
- Kbibtex, KBib, JabRef, 

pybliographer, gbib (View Bibtex files)

If you have any questions or corrections, please don't 

hesitate to contact us via [email]kile-devel@lists.sourceforge.net[/email].

The Kile dev team


I've read it but I confused and I don't know what should I do.Please help me.
(I can't connect to internet so I can not use Add/Remove or something like this.)

---

### Post by Whiffle on 2009-09-08
Have you tried installing the version of Kile from the respository? ( Add/Remove Programs)

---

### Post by Mehrdad2009 on 2009-09-08
Hi
I have downloaded "kile-2.1b2.tar.bz2"and it included REDME file .
Content of this README file is:
Dear User/Packager,

this Readme is targeted towards people who want to build Kile from source 

or plan to create binary packages.
If you have created a package, please drop us a note ( kile-

[email]devel@lists.sourceforge.net[/email] ) so that we can promote your package.

1.) Checking dependencies
============================

- KDE 4.2/4.3 and according QT development packages (ForwardDVI 

only works with KDE 4.3)
- cmake 2.6.2
- gcc 3.x/4.x

2.) Building Kile from source
============================

- Extract the source code with "tar xjf kile-x.tar.bz2"
- Create a "kile-

build" directory somewhere for an out-of-source build.
- Enter the "kile-build" directory and call 

cmake with:
" cmake <path to the kile directory> -DCMAKE_INSTALL_PREFIX=$HOME/.kde 

-DCMAKE_BUILD_TYPE="Debugfull" "
- Type "make -j 2" to compile the package.
- Type "make 

install -j 2" to install the programs, data files and documentation.
- Type "kile" and enjoy the power 

of LaTeX together with the joy of using Kile 

2.1.) Building Documentation
============================

The documentation will automatically be built provided that the 

documentation files
are located in the following directories:
<kile-root>
/doc 

for the standard documentation and
accompanying image files



/translations
/<language>
/doc for the translated documentation 

and
images in language <language>

/messages for the 

translated message catalogs
in language <language>

Please note that 

every docbook must be called "index.docbook" and that only PNG image
files can be used. 

Furthermore, message catalogs must be called "kile.po".

When the "doc" and "translations" 

directories are found, the build targets "docbooks"
and "translations" will be generated for the 

compiling of the documentation.

2.3.) Special Flags for the build
===============================
The 

flag "KILE_VERSION" can be set in the CMake cache to specify the installation
directory of basic 

documentation files (README, AUTHORS, ChangeLog,...), i.e. they
will be installed in 

"share/doc/kile-${KILE_VERSION}/" instead of "share/doc/kile/".

3.) Using Kile
===============================

To use Kile you (obviously) need some external programs.
The 

following list is divided into basic, advanced and additional usage.

Basic:
- TeXLive 2005/2007/2008 

(Including "AMS"-Packages and the documentation).
This add among others the following 

programs:
- Tex/LaTeX
- PDFLaTeX
- XeLaTeX
- ConTeXt
- BibTeX
- MakeIndex
- 

Okular (DVI, PS, PDF Viewer from KDE)

Advanced:
- Acroread (Viewing PDF)
- Imagemagick, 

DVIPNG 1.7 (Bottom bar preview)

By default there are also tools for the following programs 

defined:
- Tar/zip/gzip/bzip2 (Archive)
- DBlatex (Docbook to LaTeX)
- Metapost and Asymptote
- 

Latex2html (LaTeX to Web)
- Tex4ht (LaTeX to Web)
- Xindy (MakeIndex replacement)
- Lilypond 

(Music Typesetting)
- Konqueror/Mozilla/Firefox (Viewing HTML)
- Kbibtex, KBib, JabRef, 

pybliographer, gbib (View Bibtex files)

If you have any questions or corrections, please don't 

hesitate to contact us via [email]kile-devel@lists.sourceforge.net[/email].

The Kile dev team


I've read it but I confused and I don't know what should I do.Please help me.
(I can't connect to internet so I can not use Add/Remove or something like this.)

---

### Post by Whiffle on 2009-09-08
So I replied in your other thread....

[http://ubuntuforums.org/showthread.php?t=1261331](http://ubuntuforums.org/showthread.php?t=1261331)

---

### Post by Penguin Guy on 2009-09-08
Please do not create two posts. Take a look at this link: [How to install software on Ubuntu.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by overdrank on 2009-09-08
Threads merged. :)

---

### Post by Stefan_K on 2009-09-10
If you cannot access the internet directly and therefore cannot use the repositories you could install Kile by downloading a .deb package and install it by
```
dpkg -i kile...deb
```
Stefan


--
[TeXblog]("http://texblog.net")

---

