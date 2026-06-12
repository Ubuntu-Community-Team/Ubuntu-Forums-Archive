---
title: "How to start from scratch installing LaTex/TexLive?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by peter_kint on 2009-12-19
Hi,

I'm on LInux now for thee months (newbie)
I'm working with Lyx for my physics and math documents,
and including pgf/tikz scripts for the graphics.

Everytime I want to use an new library or install a pgf/tikz based feature, I encounter many (apparantly unsolvable) problems.

Good people are giving me advice of which I dont know how to implement it.
             Example : use tex-manager (tlmgr) to install this or that.
Upon checking I see I dont have tex-manager (of which the documentation says it should be included in teh package.... (sigh)
Apparantly I messed up in previous installations, with Tex unbale to find files, libraries, etc all the time.

Therefore** I want to start from scratch** with Latex/Tex/Livetex/Lyx/pgf/tikz.

Anyone willing to coach me i this process?
Thx
Peter

---

### Post by Mornedhel on 2009-12-19
The simplest way is to install texlive-* packages from the Ubuntu repositories. If you have a good internet connection and enough free space on your hard drive, you can just install the texlive-full package and be done with it. (This pulls in all texlive packages -- the likelihood of your needing additional packages is quite low. It takes some time, though.)

Otherwise, you can install the texlive package, which pulls in only a small subset of TeXLive, more than enough for simple projects. Then you find in which texlive package is the LaTeX package you want and install that. For instance, say you need the "pseudocode" LaTeX package :

```
$ apt-cache search latex pseudocode
texlive-science - TeX Live: Typesetting for natural and computer sciences
$ apt-cache show texlive-science
Package: texlive-science
Priority: optional
Section: universe/tex
[...]
Description: TeX Live: Typesetting for natural and computer sciences
 Typesetting for natural and computer sciences
 .
 This package includes the following CTAN packages:
  SIstyle -- The SIstyle package.
  SIunits -- International System of Units.
  alg -- LaTeX environments for typesetting algorithms.
  algorithm2e -- Floating algorithm environment with algorithmic keywords.
  algorithmicx -- The algorithmic style you always wanted!
[...]
  objectz -- Macros for typesetting Object Z.
  pseudocode -- A LaTeX enviromnet for specifying algorithms in a natural
   way.
  scientificpaper -- Format a scientific paper for journal publication.
[...]
  youngtab -- Typeset Young-Tableaux.
Homepage: http://www.tug.org/texlive
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
$ sudo apt-get install texlive-science
```

At the end of the install process, the pseudocode LaTeX package should be available and cleanly installed. Just \usepackage{pseudocode}.

If you need a package that's not in the repositories, you have two solutions :

1. You can just drop the .sty file next to your master document, and it should be available for \usepackage.

2. You can unpack the archive in your own ~/texmf folder (in your home folder), run texhash so that the package tree is updated, and it should be available for \usepackage.

---

### Post by peter_kint on 2009-12-19
> **Mornedhel said:**
> The simplest way is to install texlive-* packages from the Ubuntu repositories. If you have a good internet connection and enough free space on your hard drive, you can just install the texlive-full package and be done with it. (This pulls in all texlive packages -- the likelihood of your needing additional packages is quite low. It takes some time, though.)

Otherwise, you can install the texlive package, which pulls in only a small subset of TeXLive, more than enough for simple projects. Then you find in which texlive package is the LaTeX package you want and install that. For instance, say you need the "pseudocode" LaTeX package :

```
$ apt-cache search latex pseudocode
texlive-science - TeX Live: Typesetting for natural and computer sciences
$ apt-cache show texlive-science
Package: texlive-science
Priority: optional
Section: universe/tex
[...]
Description: TeX Live: Typesetting for natural and computer sciences
 Typesetting for natural and computer sciences
 .
 This package includes the following CTAN packages:
  SIstyle -- The SIstyle package.
  SIunits -- International System of Units.
  alg -- LaTeX environments for typesetting algorithms.
  algorithm2e -- Floating algorithm environment with algorithmic keywords.
  algorithmicx -- The algorithmic style you always wanted!
[...]
  objectz -- Macros for typesetting Object Z.
  pseudocode -- A LaTeX enviromnet for specifying algorithms in a natural
   way.
  scientificpaper -- Format a scientific paper for journal publication.
[...]
  youngtab -- Typeset Young-Tableaux.
Homepage: http://www.tug.org/texlive
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
$ sudo apt-get install texlive-science
```At the end of the install process, the pseudocode LaTeX package should be available and cleanly installed. Just \usepackage{pseudocode}.

If you need a package that's not in the repositories, you have two solutions :

1. You can just drop the .sty file next to your master document, and it should be available for \usepackage.

2. You can unpack the archive in your own ~/texmf folder (in your home folder), run texhash so that the package tree is updated, and it should be available for \usepackage.

Thx for answering,
But Ubuntu gives TexLiIve2007, and people telling me a lot of my problems come from the fact that I dont have 2008 or 2009.

So I go to  [http://www.tug.org/texlive/quickinstall.html ]("http://www.tug.org/texlive/quickinstall.html") and read the install instructions.

What I dont understand is the following part:
**Post-install: setting the PATH**
**After the installation finishes, you must add the TeX Live binary directory to your PATH&#8212;except on Windows, where the installer takes care of this.  For example:**
[B]PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH 
[/B]Use the syntax for your shell, your installation directory, and your binary platform name instead of i386-linux.  


How will I do this? Is this a command? where/how to put it?
What should I put instead of i 386-linux?

Thx

---

### Post by Mornedhel on 2009-12-19
> **peter_kint said:**
> Thx for answering,
But Ubuntu gives TexLiIve2007, and people telling me a lot of my problems come from the fact that I dont have 2008 or 2009.

OK. Just to satisfy my personal curiosity, why exactly do they say that ? Do they give any reasons ? I've never had any trouble with the TeXLive in the repositories, but I don't share a lot of LaTeX source files.

> **peter_kint said:**
> [B]After the installation finishes, you must add the TeX Live binary directory to your PATH—except on Windows, where the installer takes care of this.  For example:

PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH 
[/B]

Use the syntax for your shell, your installation directory, and your binary platform name instead of i386-linux.  


How will I do this? Is this a command? where/how to put it?
What should I put instead of i 386-linux?


To check your platform, open a terminal, and type ```
arch
```. If the command prints "i386", then "i386-linux" is probably safe. If it prints "x86-64" (if you have a 64b OS), maybe it should be "x86-64-linux".

Since we're looking for a directory, we can just check what it should look like. Try ```
ls /usr/local/texlive/2009/bin
``` in the terminal. It should print the contents of that directory. We'll use the one that looks like your platform for our PATH line.

You should add this line to your .bashrc file, in your home directory. Since it starts with a dot, it's a hidden file -- to see it in the file browser, press Ctrl+H (assuming you're running Gnome (the default), and not KDE or other). Then any terminal started after you save your new .bashrc should be aware of the change.

Post again here if you get lost at some point, need clarifications, or you don't know how to do one of the above steps.

---

### Post by peter_kint on 2009-12-19
> **Mornedhel said:**
> OK. Just to satisfy my personal curiosity, why exactly do they say that ? Do they give any reasons ? I've never had any trouble with the TeXLive in the repositories, but I don't share a lot of LaTeX source files.



To check your platform, open a terminal, and type ```
arch
```. If the command prints "i386", then "i386-linux" is probably safe. If it prints "x86-64" (if you have a 64b OS), maybe it should be "x86-64-linux".

Since we're looking for a directory, we can just check what it should look like. Try ```
ls /usr/local/texlive/2009/bin
``` in the terminal. It should print the contents of that directory. We'll use the one that looks like your platform for our PATH line.

You should add this line to your .bashrc file, in your home directory. Since it starts with a dot, it's a hidden file -- to see it in the file browser, press Ctrl+H (assuming you're running Gnome (the default), and not KDE or other). Then any terminal started after you save your new .bashrc should be aware of the change.

Post again here if you get lost at some point, need clarifications, or you don't know how to do one of the above steps.

Thx for answering
1. I guess people are telling me so because eg. I dont have the ```
tlmgr
``` command they'd want me to use. 
2```
 peter@peter-desktop:~$ arch
  i686
```3. I downloaded the  install-tl-unx.tar.gz archive from CTAN and it is on my desktop
      **What now?** (I really dont want to mess up this time, so I go slow , hopefully with
     your help)

The reason why I want to this maybe is no good reason at all.
I have been able to work joyfully in Lyx/Latex until I tried to combine it with packages like circuitikz and xstring (for pff/tikz) .

Latex/Tex/lyx doesn't ever find the right files, so I suspect I messed up in the beginning went I installed Latex/Tex/Lyx. I don't know where to put/install these extra packages so that Latex/Tex/Lyx can find them. Installing instructions are often very vague and tell me to install in thr right TDS or something.
Then I look up whta TDS is, understand (more or less) it, but I just cant implement it the right way, apparantly.

Maybe starting from scratch is not necessary, I dont know.
Thx,
Peter

---

### Post by Mornedhel on 2009-12-19
OK, here's a step by step terminal version, starting with the .tar.gz archive located in folder "Downloads".

Moving into the correct directory (this step depends on where you put the archive) :
```
$ cd Downloads
```

Extracting the archive :
```
$ tar xvzf install-tl-unx.tar.gz
[the contents of the archive as displayed as they are extracted]
```

Moving into the newly extracting directory :
```
$ cd install-tl-20091217/
```

Running the installer :
```
$ ./install-tl
[note that at this point the second line of output indicates what the installer thinks your platform is -- chances are it's right : it correctly detected "x86_64-linux" for me]
[also note that the default value for the locally-installed packages directory is "~/texmf", this is where you should put packages that you install by hand]
```

Here the installer prompts you for an action. Press i and RETURN to install.

The next step, according to the installation instructions, is to add the line :
```
PATH=/usr/local/texlive/2009/bin/x86_64-linux:$PATH
```

at the end of the ".bashrc" file located in your home directory.

You should be all set now, but feel free to ask if something goes wrong.

---

### Post by peter_kint on 2009-12-20
```
$ cd install-tl-20091217/
```Running the installer :
```
$ ./install-tl
[note that at this point the second line of output indicates what the installer thinks your platform is -- chances are it's right : it correctly detected "x86_64-linux" for me]
[also note that the default value for the locally-installed packages directory is "~/texmf", this is where you should put packages that you install by hand]
```Here the installer prompts you for an action. Press i and RETURN to install.

Thank you for your patience and help!
At this point (running the installer) it detected my platform as:
```
Platform: i386-linux => 'Intel x86 with GNU/Linux
```1. Earlier in this thread you aked me to issue the arch command, which then gave:
```
peter@peter-desktop:-$ arch
  i686
```Is this OK? (difference)

2. The post-installation PATH command **in my case** should thus be

```
PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH
```or

```
PATH=/usr/local/texlive/2009/bin/i686:$PATH
```?

3. The output gives also:
 ```
<D> directories:
   TEXDIR (the main TeX directory):
     !! default location: /usr/local/texlive/2009
     !! is not writable, please select a different one!
```

Is this ok? Should I first create this directory?

(I'm going slow, to be sure not to mess up)

Thx again.
Peter

---

### Post by apolozanionut on 2009-12-20
Hello Peter. 
The last error you encounter relating to the read/write permissions are generated by the fact that you don't have root permissions. For that, try running :
```
sudo ./install-tl
```
It will prompt for your password and that should be all.
It worked for me.
Cheers.

---

### Post by peter_kint on 2009-12-20
> **apolozanionut said:**
> Hello Peter. 
The last error you encounter relating to the read/write permissions are generated by the fact that you don't have root permissions. For that, try running :
```
sudo ./install-tl
```It will prompt for your password and that should be all.
It worked for me.
Cheers.
Hello,
I don't understand. Where do you see an error?
I'm just waiting for an answer to the folowing questions:

At this point (running the installer) it detected my platform as:
```
Platform: i386-linux => 'Intel x86 with GNU/Linux
```1. Earlier in this thread you aked me to issue the arch command, which then gave:
```
peter@peter-desktop arch
  i686
```** this OK? (difference)**

2. The post-installation PATH command **in my case** should thus be:
```
PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH
```[B]
or??[/B]
```
PATH=/usr/local/texlive/2009/bin/i686:$PATH
```3. The output gives also:
```
<D> directories:
   TEXDIR (the main TeX directory):
     !! default location: /usr/local/texlive/2009
     !! is not writable, please select a different one!
```**Is this ok? Should I first create this directory? Or create an other one?**

Thx,
Peter

---

### Post by Mornedhel on 2009-12-20
Hi,

The other poster is correct : if you're not running the installer with administrative permissions, it won't be able to write to /usr/local. This was a mistake on my part : it is possible to run it without sudo if you are going to install it in a directory you own, but it is simpler to install it in /usr/local, so you should use "sudo ./install-tl". This would enable the installer to create a directory in /usr/local/texlive/2009, so the error message "not writable" at the end should disappear. The rest is unchanged.

i686 and i386, while different, are compatible (it's more complicated but I wouldn't confuse you with the details). So i386-linux is fine. The correct PATH line is the first one.

Good luck !

---

### Post by peter_kint on 2009-12-20
Ok, thx everbody and apology to apolozaniut for my ignorance.

  **BUT: I still dont have Texlive 2009 !!**

```
peter@peter-desktop:~$ tex --version
TeX 3.141592 (Web2C 7.5.6)
kpathsea version 3.5.6
Copyright 2007 D.E. Knuth.
Kpathsea is copyright 2007 Karl Berry and Olaf Weber.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.
Kpathsea written by Karl Berry, Olaf Weber, and others.

```
I followed all your instructions, what on earth did I do wrong?
Sigh

---

### Post by Mornedhel on 2009-12-20
If you installed TeXLive from the repositories at some point, did you make sure you uninstalled that version ?

OK, I just installed it from install-tl, just to make sure, and after the installation and with a correct PATH line, tex --version returns the version information for the 2009 version.

You have to make sure of two things :

1) You are running tex --version from a shell that was started *after* you added the PATH line and saved the .bashrc file
2) The PATH line must point to an existing directory : for me it's "/usr/local/texlive/2009/bin/x86_64-linux", but since you're running a 32b system, yours will be different. Since we may have made a mistake here, do "ls /usr/local/texlive/2009/bin", and the result should be the correct directory (at least on my system, the only result is "x86_64-linux"). Amend your PATH line so that it points to that directory ("/usr/local/blah/thedirectoryhere"), re-start a shell, and check again.

---

### Post by peter_kint on 2009-12-20
> **Mornedhel said:**
> If you installed TeXLive from the repositories at some point, did you make sure you uninstalled that version ?

OK, I just installed it from install-tl, just to make sure, and after the installation and with a correct PATH line, tex --version returns the version information for the 2009 version.

You have to make sure of two things :

1) You are running tex --version from a shell that was started *after* you added the PATH line and saved the .bashrc file
2) The PATH line must point to an existing directory : for me it's "/usr/local/texlive/2009/bin/x86_64-linux", but since you're running a 32b system, yours will be different. Since we may have made a mistake here, do "ls /usr/local/texlive/2009/bin", and the result should be the correct directory (at least on my system, the only result is "x86_64-linux"). .

Sorry for my ignorance.

```
peter@peter-desktop:~$ ls /usr/local/texlive/2009/bin
i386-linux
```

Amend your PATH line so that it points to that directory ("/usr/local/blah/thedirectoryhere"), re-start a shell, and check again

I didn't do anything with the .bashrc file. What should it look like?
I don't know what a shell is.
Could you give me the exact commands?
This is getting too much for me. Why cant I just install something right? 

Thx
Peter

---

### Post by Mornedhel on 2009-12-20
Sure.

1) Edit the .bashrc file in your home directory : open the text editor from the Applications/Accessories menu, open the .bashrc file in your home directory (you may need to press Ctrl+H in the Open dialogue so that hidden files are displayed), make sure the following line is present at the end of your .bashrc file :

```
PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH
```

Save the file.

2) Open a new terminal session (the terminal *has* to have been started *after* you modified the PATH and saved the file, or it won't take the change into account).

3) Run tex --version in that new terminal, which should return the correct information.

OK, I just saw your edit. The .bashrc file is the configuration file for the shell, which is the program run by the terminal to understand the commands you type in (such as tex --version) and run the corresponding applications. The file already exists and has plenty of things that you probably don't understand, but you don't need to concern yourself with it right now. Just make sure you have the PATH line at the end of the file (this is the "post-install" phase from the TeXLive installation instructions).

---

### Post by peter_kint on 2009-12-20
> **Mornedhel said:**
> Sure.

1) Edit the .bashrc file in your home directory : open the text editor from the Applications/Accessories menu, open the .bashrc file in your home directory (you may need to press Ctrl+H in the Open dialogue so that hidden files are displayed), make sure the following line is present at the end of your .bashrc file :

```
PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH
```Save the file.

2) Open a new terminal session (the terminal *has* to have been started *after* you modified the PATH and saved the file, or it won't take the change into account).

3) Run tex --version in that new terminal, which should return the correct information.

OK, I just saw your edit. The .bashrc file is the configuration file for the shell, which is the program run by the terminal to understand the commands you type in (such as tex --version) and run the corresponding applications. The file already exists and has plenty of things that you probably don't understand, but you don't need to concern yourself with it right now. Just make sure you have the PATH line at the end of the file (this is the "post-install" phase from the TeXLive installation instructions).

Thank you for your seemingly endless patience. I'm learning a lot from this.
This is what I get:

```
peter@peter-desktop:~$ tex --version
TeX 3.1415926 (TeX Live 2009)
kpathsea version 5.0.0
Copyright 2009 D.E. Knuth.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the TeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the TeX source.
Primary author of TeX: D.E. Knuth.
```So that seems ok. 

Lyx is not 'convinced' yet, though...

Thx. Peter

---

### Post by Mornedhel on 2009-12-20
You're welcome.

Unfortunately, I have no experience with Lyx whatsoever (I write my LaTeX by hand with emacs), so I can't really help you there. You're better off opening another thread and asking how to make Lyx play nice with local TeXLive installations, and hoping a Lyx user will help you.

---

### Post by peter_kint on 2009-12-20
> **Mornedhel said:**
> You're welcome.

Unfortunately, I have no experience with Lyx whatsoever (I write my LaTeX by hand with emacs), so I can't really help you there. You're better off opening another thread and asking how to make Lyx play nice with local TeXLive installations, and hoping a Lyx user will help you.

That's what I will do.
I owe u one.
Happy year-ending!
Peter

---

