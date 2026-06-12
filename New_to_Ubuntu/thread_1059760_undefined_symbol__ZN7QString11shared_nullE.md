---
title: "undefined symbol: _ZN7QString11shared_nullE"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by jackdale on 2009-02-04
Probably a stupid question, but I only downloaded ubuntu less than a month ago...

I'm trying to install a Kbasic binary file.  I initially had trouble because of a couple of missing library files that are apparently "dependencies" without which the program cannot run.  Having installed the libraries, and logged in as root (because I could not find another way to change the folder permission on usr/lib) I type ./[then the binary name] and i get the following message:

```
# ./installer_kbasic_professional_linux.bin: symbol lookup error: ./installer_kbasic_professional_linux.bin: undefined symbol: _ZN7QString11shared_nullE
#
```

I don't know how to go about trying to run it outside the terminal because even though I have checked the permission to allow it to run as an executable file, it gives an error saying that there is no program to show the file.

The Kbasic website states it has been tested on Ubuntu 8.04.

The question: Is _ZN7QString11shared_nullE like a library file or some other dependency? If so, is there anywhere I can download it to install it?

(Minor question: I'm only used to Mac and Windows but I like the freedom that GNU/Linux offers, however, I have very little programming skills and almost no UNIX experience. Is the problem of missing dependencies a common one?  Is there somewhere I can download common dependencies?)

Thanks for any help that can be provided.

Jack

P.S.  System Info:
GNOME 2.24.1 on Ubuntu 8.10 running on a 64bit virtual machine (VMWare Fusion) on a MacBook Pro 2.53GHz Intel Core 2 Duo; 4GB 1067 MHz DDR3.

---

### Post by petervk on 2009-02-04
I hate to say it but your going about this the wrong way. You shouldn't have to use the root account ever, and you definitely shouldn't be messing around with the permissions of the /usr/lib directory.

Usually you should be able to download the file to a directory, open a terminal, navigate to that directory, "chmod +x filename" to make the file executeable, and then "sudo ./filename" to install as root.

On a somewhat related note, why Kbasic? Are you interested in programming for linux? I'd then recommend python. It comes with Ubuntu, it's extremely well designed, and it's can do everything from simple shell scripting to full gui/database applications.

---

### Post by Malalo on 2009-02-04
+1 for Python
And, you don't have the hassle of installing since it's in the repos.

---

### Post by jackdale on 2009-02-05
Thanks for the replies so far.
Like I said, I'm only new to gnu/linux, so i'm was experimenting with the terminal without reading the manual yet...(a bit naughty i guess...)

As for the choice of Kbasic, I'm just reviewing it as it has been recommended to me (normally I use RealBasic when I use basic at all).

I tend to use basic IDEs when i want to test out an idea for an app quickly that may later need the power of C/C++.  I must say, I have not yet tried python and as I have not found the missing symbol, I think I will give it a go! 

Thanks again for the advise, although if anyone knows how to get a hold of _ZN7QString11shared_nullE, I would love to hear about it.

---

### Post by jackdale on 2011-10-30
Marking this thread as solved (as in solved by time, new software versions and I've moved on ;))

---

