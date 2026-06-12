---
title: "Problem with latex"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by jm22 on 2011-05-29
Hello,

I have a problem with my installation of latex. I perform a first installation using

sudo apt-get install texlive-latex-base

this installs latex in the directory

usr/share

But it seems that some packages are missing in this distribution. I decided to remove this distribution and reinstall the distribution provided by [www.latex-project.com](www.latex-project.com).
The installation is done by default in usr/local/ and performs well. I finally add the related path

PATH=/usr/local/texlive/2010/bin/i386-linux:$PATH 

but when I try to use latex I get the following message:

warning: kpathsea: configuration file texmf.cnf not found in these directories: /usr/share/texmf/web2c:/usr/share/texmf-texlive/web2c:/usr/local/share/texmf/web2c.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
**

It seems that it remains some files/packages of the previous installation and this is this version that is used.
Does anyone have an idea to fix this problem and force latex in usr/local to be used?

Many thanks

Jean-Marie

---

### Post by silex89 on 2011-05-29
Hmmm, I would suggest you to use the editor from Open/Libre Office suite, has almost the same benefits than TeX (obviously the language for editing is very different, but the result is the same) and you can export the PDF directly, you have the option of edit formulas with GUI tools.


BTW I just tried to install TeX such as you did, and I had the same issue


Regards and good luck! :D

---

### Post by jm22 on 2011-05-29
Yes but I am writing my Phd thesis with latex I have a lot of things already done with latex and I like the results I get with... I never obtain such quality with office or word...

Thank you

Jean-Marie

---

### Post by Smart Viking on 2011-05-29
Well the error message is pretty straight forward

```
sudo touch /usr/share/texmf-texlive/web2c/texmf.cnf
```See if that works.

EDIT: [http://ubuntuforums.org/showthread.php?t=663322](http://ubuntuforums.org/showthread.php?t=663322)

Maybe just the program is broken, maybe try another version.

---

### Post by jm22 on 2011-05-30
I found the way to completely remove the latex-base installation 

sudo apt-get --purge remove tex-common texlive-base texlive-binaries texlive-common texlive-doc-base texlive-latex-base texlive-latex-base-doc texlive-luatex

You may have other files/packages from this installation. Check for that in order to completely remove the installation.

Now my latex distribution works well :D

I just want to definitely add a the latex PATH 
/usr/local/texlive/2010/bin/x86_64-linux to my searched PATH...

Actually I have to add the PATH each times I restart the terminal. Maybe I should add something in my file .bashrc

I will check for that

---

### Post by Chronon on 2011-05-30
I wrote my dissertation using texlive from the repositories.  The package you installed only gives a bare-bones system.  Most people augment this by installing additional packages.

So, congratulations on manually installing a newer version of texlive. :guitar:  I just wanted you and others to know that a fully functional latex system *can* be installed directly from the repositories.

---

