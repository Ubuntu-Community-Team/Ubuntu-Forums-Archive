---
title: "Getting Intel Fortran to run with UBUNTU 11.04"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by ptaylor1951 on 2011-09-03
Hi

I am new to LINUX and UBUNTU having made the switch because CVF 6.6 does not work on WINDOZE 7.
I have been following the Intel Fortran Compiler User and Reference Guides.
I have compiled the sample programs on page 111. However, when typing in the command 'calc' as detailed under "Running the Sample program" on page 112, I get the following message:"program 'calc' is currently not installed. You can install it by typing: sudo apt-get install apcalc". At step 4, something called 'calc' was created and I can see it in the folder but UBUNTU or Intel Fortran does not recognise it as an executable.

How do solve this?

---

### Post by grahammechanical on 2011-09-03
I have just typed calc in a terminal and I get the same message. The system is guessing that you and I want to run a program called apcalc which is not installed on our systems.

I do not know if this is the right answer for you but I suggest two things,

1) You change directory to the directory containing these sample programs. 
2) You use the full program/script name including the extension. Does calc have an file extension as part of its name?

Of course I could be completely wrong about all this.

Regards.

---

### Post by JKyleOKC on 2011-09-03
In Linux, a file must be specifically tagged as "executable" in order to be loaded and run as a program. However the error message you cited indicates that the program-loading portion of the shell was unable to locate the file in the first place. Usually this happens because the file is not found in the search path; while Windows automatically includes the current directory in the path, Linux does not do so (although it can be added to the PATH environment variable, doing so introduces a potential security risk). Try ```
./calc
```instead, to force the loader to look only in the current directory. If you then get a different error message, try ```
chmod +x calc
```to set the "executable" bit, and re-try the previous command.

It's possible, still, that the compiler may generate code for the Windows API rather than for Linux, in which case it still won't work directly in any Linux distribution -- but might run under WINE...

---

### Post by ptaylor1951 on 2011-09-05
Jim

Very many thanks.
./calc did the trick.
I had already discovered that it is better keeping all the files in the one directory, well at least until I gain more experience with UBUNTU and can set up all the appropriate path names.
Until the next time.

Kind Regards

Paul

---

### Post by JKyleOKC on 2011-09-05
Great to hear. Please use the link in my signature to mark the thread as "solved" for the benefor of future searchers.

---

