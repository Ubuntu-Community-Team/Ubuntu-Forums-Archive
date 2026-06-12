---
title: "Changing LDFLAGS environment variable in bash?"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Birch Bark on 2009-10-11
Hello All,
I'm trying to configure libmtp-1.0.1.  Everything is fine except that I repeatedly get this message at the end:

```
configure: error: I can't find the libusb libraries on your system. You may need to set the LDFLAGS environment variable to include the search path where you have libusb installed before running configure (e.g. setenv LDFLAGS=-L/usr/local/lib)
```I wasn't sure I had the libusb package, so I went and got the libusb tarball from SourceForge and extracted it and configured it--no problem.  Then I went back and tried to run the command "setenv" as shown in the example above.  Apparently bash doesn't recognize this command; it tells me "command not found."  I tried a few other things and searched around a bit but didn't find anything to solve my problem.

Can someone please explain to me:

What are LDFLAGS?
What does "environment" mean in this context?
How can I get libmtp to be able to find libusb?

Thanks a bunch!

---

### Post by lloyd_b on 2009-10-11
First off, is it really necessary to build libusb from source?  It's in the repos (though it may be an obsolete version).  "sudo apt-get install libusb-dev" should get you the library and the development headers you'll need to compile against the library.

As for your actual questions:

1.  LDFLAGS is a place to store values that alter the normal operation of certain programs ("ld", the "linker", in particular).  For instance, the example provided in that error message causes that particular option to be applied by "ld" as if it were part of the command line that was executed.

2.  "environment" consists of a set of environment variables (PATH, HOME, TERM, etc.) that define all of the particular information that programs may need to know about the current user/session.  Type "env" in a terminal window to get a look at your current list of environment variables.

3.  Assuming you want to stick with your compiled library, instead of "setenv", type "export LDFLAGS=...", with the proper values for LDFLAGS. 

Lloyd B.

---

### Post by Birch Bark on 2009-10-11
Thanks for your help!  Your first point actually solved the problem.  Once I installed libusb-dev from the repos libmtp found it without a problem.

Ha, I was so excited about learning to compile packages manually last night (I'm really new at this) that I wanted to practice on libusb.  I could have saved myself some time by doing it the easy way.  : )

Now if I can just get libmtp to detect my player...

---

