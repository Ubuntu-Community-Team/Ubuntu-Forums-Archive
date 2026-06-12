---
title: "Can I get AsfBin to work?"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by andjen on 2009-03-20
I'm running 8.04 and I have been looking for a good app to trim WMV files. When I used Vista then I always used AsfBin which I found very quick and gave good quality output.

On this page

[http://www.radioactivepages.com/index.php?section=software&docid=asfbin](http://www.radioactivepages.com/index.php?section=software&docid=asfbin)

I found a Linux version of the same program which it says has been tested on Ubuntu but after extracting the download I can't seem to get it to run.

I'm fairly new to Ubuntu so is there something I should be doing to the file after extraction in order to get it to run?

Andjen

---

### Post by taurus on 2009-03-20
Did you download this file to your desktop, asfbinlinux1.7.1.756.zip?

If you did, then open a terminal extract it first.

```
cd ~/Desktop
unzip -x asfbinlinux1.7.1.756.zip
```
Now, you would get a new file, asfbin-bin, which you have to change the permissions.

```
chmod 755 asfbin-bin
ldd asfbin-bin
```
What is the output of the second command?

---

### Post by andjen on 2009-03-20
Thanks for your reply.

The output after using your second command is :

	linux-gate.so.1 =>  (0xffffe000)
	libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0xf7e63000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d14000)
	libm.so.6 => /lib32/libm.so.6 (0xf7cee000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7ce3000)
	/lib/ld-linux.so.2 (0xf7f33000)

I hope this means something to you because it doesn't to me!!!

---

### Post by taurus on 2009-03-20
It means the program finds all the necessary libraries on your machine.  Now, see what happens if you run it from a terminal, assuming you're still in same directory that you ran the last command.

```
./asfbin-bin
```

---

### Post by andjen on 2009-03-20
Sorry, but the out put from trying to run it is:

Application name is asfbin-bin
ASFBIN - version asfbin-bin 1.7.1.756. Copyright 2001-2007 by RadioActive.
Non-commercial version.
Visit [www.radioactivepages.com](www.radioactivepages.com) for latest updates.
PROCESSING FAILED!
   Reason: No output file specified.
For more help run asfbin with -h switch.

Where do we go from here?

---

### Post by taurus on 2009-03-20
You need to specify an output file.  For help, run

```
./asfbin-bin -h
```

---

### Post by andjen on 2009-03-20
The result is a long list of instructions about how to use the program from a command line (and the various switches that are needed in order to get different results.

Pity really cos I was expecting to get a GUI like the program that I used in Vista. Still, I'm sure I'll be able to get it to work after a bit of practice.

Thanks for all your help and patience.

Andjen

---

