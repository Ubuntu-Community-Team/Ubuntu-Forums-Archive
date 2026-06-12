---
title: "install problem"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by drordh on 2010-12-21
Hey, i am trying to install a program name blat,
i am adding the instructions for install and what i did...
The instructions:
CONTENTS AND COPYRIGHT

This archive contains the entire source tree for BLAT and
associated utilities.  All files are copyrighted, but license 
is hereby granted for personal, academic, and non-profit use.  
A license is also granted for the contents of the top level 
lib and inc directories for commercial users.  Commercial 
users should contact [email]jim_kent@pacbell.net[/email] for access to other modules.

INSTALL INSTRUCTIONS

1. Unzip this to create a blatSrc directory.
2. Check that the environment variable MACHTYPE
   exists on your system.  It should on Unix.  
   (And making this on non-Unix systems is beyond
   the scope of this README).  For a Linux 
   system MACHTYPE will probably be 'i386', for
   and Alpha it will be 'alpha', for a Sun
   probably 'sparc'.  If necessary set up
   this environment variable.  Do this under the
   bash shell as so:
       MACHTYPE=something
       export MACHTYPE
   or under tcsh as so:
       setenv MACHTYPE something
3. Make the directory ~/bin/$MACHTYPE which is
   where the (non-web) executables will go.
   Add this directory to your path.
4. Go to the lib directory.  If it doesn't
   already exist do a mkdir $MACHTYPE.
5. If you're on an alpha system do a:
     setenv SOCKETLIB -lxnet
   on Solaris do
     setenv SOCKETLIB "-lsocket -lnsl"
   on SunOS do
     setenv SOCKETLIB "-lsocket -lnsl -lresolv"
   on Linux you can skip this step.
6. At the blatSrc directory type 'make'

i did:
1. to find my path
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
2. MACHTYPE=/usr/bin
   export MACHTYPE
3. i cant create the ~/bin/$MACHTYPE  . i am going to the bin and doing 

sudo mkdir $MACHTYPE

mkdir: cannot create directory `i486-pc-linux-gnu': File exists

what does it mean?

thanks

---

### Post by madjr on 2010-12-21
not sure if this might help.

[http://www.mail-archive.com/genome@lists.soe.ucsc.edu/msg02750.html](http://www.mail-archive.com/genome@lists.soe.ucsc.edu/msg02750.html)
[http://ubuntuforums.org/showthread.php?t=1594650](http://ubuntuforums.org/showthread.php?t=1594650)

theres not much about that program.

---

### Post by drordh on 2010-12-21
thanks, but there are n answers..... in both

---

