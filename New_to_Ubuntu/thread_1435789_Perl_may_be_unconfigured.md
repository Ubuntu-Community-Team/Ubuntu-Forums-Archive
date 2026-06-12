---
title: "Perl may be unconfigured?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by JohnJD on 2010-03-21
I have a bug in my software-center.  So, I tried to uninstall and then reinstall and see if that would work.  However, I can't do that, because I get this:

johnny@johnny-desktop:~$ sudo apt-get remove software-center
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

I've gotten a similar error for other things as well.  Anyone know what this means?

(P.S.--how do I do the thing where I have the terminal output in it's own little box instead of just copy and paste it?)

---

### Post by gmargo on 2010-03-22
Look at your errors.  Here's a list of the "unquoted strings", see if you can detect any pattern (have you been adjusting your printer lately?):

```

make del laser dpi 1200
http www lexmark com printers laser html 
tscript charset us text

```My guess is that you've overwritten /usr/share/perl/5.10/File/Spec.pm with something strange.  Check the content of that file. Here are some details for that file on 9.10 Karmic:
```

$ ls -l /usr/share/perl/5.10/File/Spec.pm
-rw-r--r-- 1 root root 597 Oct  1 15:58 /usr/share/perl/5.10/File/Spec.pm

$ wc /usr/share/perl/5.10/File/Spec.pm
 27  76 597 /usr/share/perl/5.10/File/Spec.pm

$ md5sum -b /usr/share/perl/5.10/File/Spec.pm
437a3aeecb339dc5c58eed8ba112a04a */usr/share/perl/5.10/File/Spec.pm

```> 
(P.S.--how do I do the thing where I have the terminal output in it's  own little box instead of just copy and paste it?)
Use CODE tags with backets (CODE to start, /CODE to end), i.e.
[html]
```

Paste your code here.
(It will appear in a proportional font in the preview window 
but in a fixed width font in the final display.)
You can also use the pound-sign (#) icon on the
message editor to wrap selected text in CODE tags.
The CODE keyword can be lower case too.
And I used similar QUOTE keywords to wrap your question above,
and HTML keywords to wrap this block.

```
[/html]

---

### Post by JohnJD on 2010-03-22
No, I just installed Ubuntu and haven't hooked up any printers.  I've been reading the files mentioned in the error code in my terminal and comparing them with the files on a laptop that is running ubuntu just fine.  They are totally different.  A bad install maybe?  I don't know.  I had a similar problem with my software center, so I just made a copy of all the software center files on my laptop and used them to replace the ones on the desktop.  That worked, although I am still having this problem with perl.

---

