---
title: "Software Center not working"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by JohnJD on 2010-03-17
Everytime I click on the Software Center, it fails to pop up.  When I try to launch from the terminal, I get this:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 42, in <module>
    from softwarecenter.enums import *
  File "/usr/share/software-center/softwarecenter/enums.py", line 1
    BJECTS {
           ^
SyntaxError: invalid syntax

What does this mean?

---

### Post by ndefontenay on 2010-03-17
Wow.

It means you have a serious bug in the code of your software centre. How is that even possible? Oo

It looks like somehow someone modified that file and removed the o for OBJECT. It might be easy to modify this if it's in a python script but I'm not sure where that is located.

I believe the best and cleanest way to achieve this would be to use apt-get and remove the software centre packages and re-install them.

Nico

---

### Post by JohnJD on 2010-03-17
I tried to use the sudo apt-get remove for the software center and here is what I got:

johnny@johnny-desktop:~$ sudo apt-get remove software-center
[sudo] password for johnny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 241 not upgraded.
After this operation, 1,540kB disk space will be freed.
Do you want to continue [Y/n]? y
Unquoted string "make" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 2.
Unquoted string "del" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 3.
Unquoted string "laser" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 5.
Unquoted string "dpi" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 7.
Number found where operator expected at /usr/share/perl/5.10/File/Spec.pm line 8, near "<x>1200"
    (Missing operator before 1200?)
Bareword found where operator expected at /usr/share/perl/5.10/File/Spec.pm line 15, near "<url>http"
    (Missing operator before http?)
Unquoted string "http" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "www" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "lexmark" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "com" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "printers" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "laser" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "html" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 15.
Unquoted string "tscript" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 18.
Unquoted string "charset" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 21.
Unquoted string "us" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 21.
Unquoted string "text" may clash with future reserved word at /usr/share/perl/5.10/File/Spec.pm line 22.
debconf: Perl may be unconfigured (syntax error at /usr/share/perl/5.10/File/Spec.pm line 2, near "make>"
"no" not allowed in expression at /usr/share/perl/5.10/File/Spec.pm line 13, at end of line
Compilation failed in require at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 15%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'apport-symptoms' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

