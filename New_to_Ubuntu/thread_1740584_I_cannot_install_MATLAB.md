---
title: "I cannot install MATLAB"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by aab001 on 2011-04-27
hi 
every time i want to install MATLAB software i have the messege[IMG]file:///tmp/moz-screenshot.jpg[/IMG] "unable to create destination folder /usr/local/MATLAB/R2011a_Student
please I need your help

---

### Post by alphacrucis2 on 2011-04-27
> **aab001 said:**
> hi 
every time i want to install MATLAB software i have the messege[IMG]file:///tmp/moz-screenshot.jpg[/IMG] "unable to create destination folder /usr/local/MATLAB/R2011a_Student
please I need your help

Sounds like a permissions problem. Did you run the installer using sudo as suggested here?:

[https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")

---

### Post by Koppenaal on 2011-04-27
Here I had the same problem. You need to run the install as root. (Probably /tmp/mathwork_downloads/R2011a/install)

---

### Post by aab001 on 2011-04-27
thank you
it has been installed. but i don't know how to run it?

---

### Post by alphacrucis2 on 2011-04-27
> **aab001 said:**
> thank you
it has been installed. but i don't know how to run it?

Try following the instructions to create a MATLAB launcher as described in the MATLAB community documentation I linked in my earlier post.

---

### Post by wcasper4 on 2011-05-01
have a copy of MATLAB 2010a and I am running into issues installing it. I have followed the code here: and when I try and run the installer, it comes back with this:


```

walter@W:~$ sudo /home/walter/Desktop/MATLAB/install
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        Segmentation fault

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .
```

and then 

```
Sorry! Setup aborted . . .

walter@W:~$ sudo sh /home/walter/Desktop/MATLAB/install* -t
awk: cmd. line:2: 	BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2: 	                                        ^ syntax error
awk: cmd. line:6: 		    if (nrows < min) nrows = default
awk: cmd. line:6: 		                             ^ syntax error
awk: cmd. line:12: 	END { if (found == 0) print (default - extra) }
awk: cmd. line:12: 	                             ^ syntax error
awk: cmd. line:12: 	END { if (found == 0) print (default - extra) }
awk: cmd. line:12: 	                                              ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
[: 582: -le: argument expected
Segmentation fault
```

---

