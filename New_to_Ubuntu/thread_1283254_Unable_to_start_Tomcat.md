---
title: "Unable to start Tomcat"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by diabolator2 on 2009-10-05
Hi, all! I'm an experienced XP user, but on Ubuntu, damn, I'm green. 
I use Eclipse with OpenXava and I can't build my projects because of this:
 
try to start tomcat in a terminal and got next:

run-detectors: unable to find an interpreter for
/media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe 

or double clik on tomcat.exe: 

[/media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe or
          /media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe.zip, and cannot find /media/Work/*sftw/openxava-3.1.4/tomcat/bin/tomcat5.exe.ZIP, period.
No zipfiles found.

I try hard not to ask questions, but now I need help. Thanks!

---

### Post by achase79 on 2009-10-05
this is a windows executable file.  The only way to open it in linux is to have wine installed and open the executable in wine.

---

### Post by diabolator2 on 2009-10-06
thanks! got it, actually, I've found how to do it, it was like

                    sudo....and-I-dont-remember-what-else

but, a problem still persists: unable to define JAVA_HOME. It's different from XP to do. I consult ubuntuforums on this but nothing works. Just once I could get to the end of a prijoect. At my next try, JAVA_HOME was not defined again. 

I tried to edit bashrc in order to define JAVA_HOME permanently but it didnt work. 

Look, I have jdk1.6.0_16 installed on /media/Work/jdk1.6.0_16, but the command

                          export JAVA_HOME=/media/Work/jdk1.6.0_16

doesnt work.

Any ideeas? Man, I can't go on, help. Thanks!

---

