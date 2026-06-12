---
title: "install tar.gz applications"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by bobin on 2009-06-05
how do i do this

---

### Post by Tibuda on 2009-06-05
tar.gz is only a compressed archive. it can have any content, like executables (like firefox downloaded from official website) or source code (like most "tar.gz applications"). What application are you trying to install? Are you sure the application is not available in Ubuntu package manager? There's a README file in the archive?

---

### Post by bobin on 2009-06-05
its a djvu to pdf converter . due internet problems i cannot use the repository

---

### Post by x33a on 2009-06-05
you'll have to compile the software yourself.

take a look here:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Tibuda on 2009-06-05
Ok. There's a README file in the archive with installation instructions? Can you link to a site where I can download this tar.gz gile?

---

### Post by LepeKaname on 2009-06-05
I highly recommend to use "checkinstall".
After your "make install", run "checkinstall" (it will generate a .deb file) and then run dpkg -i ****.deb. 
In that way, you will be able to uninstall it easily.

---

### Post by bobin on 2009-06-05
linux.softpedia.com

---

### Post by x33a on 2009-06-05
> **LepeKaname said:**
> I highly recommend to use "checkinstall".
After your "make install", run "checkinstall" (it will generate a .deb file) and then run dpkg -i ****.deb. 
In that way, you will be able to uninstall it easily.

checkinstall replaces make install, it shouldn't be run after make install. instead it should be run after make.

1. ./configure
2. make
3. sudo checkinstall

---

### Post by LepeKaname on 2009-06-05
I know, but in my experience, sometimes checkinstall didn't perform correctly (or maybe I just don't trust it that much). I used to use it a lot when I used Slackware (around 5 to 6 years ago). I believe it may be safe now just running "checkinstall" after make...

---

### Post by x33a on 2009-06-05
maybe you mean this:

[http://linux.softpedia.com/get/Text-Editing-Processing/Others/djvu2pdf-26363.shtml](http://linux.softpedia.com/get/Text-Editing-Processing/Others/djvu2pdf-26363.shtml)

first extract the contents using

```
tar xvzf djvu2pdf-0.9.1.tar.gz
```

To install it:

```
Copy the djvu2pdf shell script in one of your PATH directories and make it executable.

$ chmod +x djvu2pdf && mv djvu2pdf ~/bin

To install the manpage, copy it in your man1 directory.

# mv djvu2pdf.1.gz /usr/man/man1

```

note: these instructions are from softpedia.

---

### Post by andrew.46 on 2009-06-13
Hi LepeKaname,

> **LepeKaname said:**
> I know, but in my experience, sometimes checkinstall didn't perform correctly (or maybe I just don't trust it that much). I used to use it a lot when I used Slackware (around 5 to 6 years ago). I believe it may be safe now just running "checkinstall" after make...

There is a longstanding problem with checkinstall that in fact resulted in checkinstall being removed from Slackware completely. The checkinstall home page mentions it briefly:

[http://checkinstall.izto.org/](http://checkinstall.izto.org/)

and apparentlynow  there is a fix in git but frustratingly it has not been incorporated into a *[I]new*[/I] release. The temporary fix has been to add the following to the checkinstall string:

```
--fstrans=no
```

and this works well enough. I note that for Jaunty the equivalent option has been added to the checkinstall configuration file /etc/checkinstallrc as:

```
# Are we going to use filesystem translation?
# Note: checkinstall, as of 1.6.1 doesn't handle the at family of syscalls.
# This means that translation doesn't work as coreutils uses them.
TRANSLATE=0
```

so the commandline option should not be required for Jaunty. I am not sure if the same change has been made in Karmic but I would imagine the package + configuration would be the same.

All the best,

Andrew

---

