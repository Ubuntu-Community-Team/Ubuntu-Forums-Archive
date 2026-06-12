---
title: "Redefine command"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by The average internet guy on 2010-05-27
I have a very simple question that probably is dead easy: How do you redefine a command in the terminal?

I installed an application called Matlab, but I installed it in the wrong place so I had to delete it and start over again in a different directory. Then when I try to launch it from the terminal with "matlab" it says something about some missing java files. How do I reconfigure the matlab command to be able to use the new installation?

---

### Post by Zemblan on 2010-05-27
Did it run properly with the previous installation? The one you deleted?
Could you paste the error messages that it gives when you try to launch it.

---

### Post by The average internet guy on 2010-05-27
It ran fine before, yes. Maybe I should also say that i deleted the old installation by rm -rf since there is no uninstaller available. This is the error: 


---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------
/usr/bin/glnx86/MATLAB: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

---

### Post by tom.swartz07 on 2010-05-27
Try purging Java from the system and reinstalling both Matlab and Java. I know its a big pain in the butt to get Matlab working perfectly on Ubuntu.

I installed it on my permanent /home partition so that I dont have to reinstall after re-installing Ubuntu. :P

Could you post the output of ```
matlab -n
``` from the terminal please?

---

### Post by The average internet guy on 2010-05-27
It was really easy to get it to work on my laptop, but this time on my stationary it was more difficult. Got it to work though. In the install directory there was a file called install_matlab (or something similar) which I ran, that seemed to do it. Strange that it was necessary to install it twice though, that wasn't the case when I installed it on my laptop. But thank you for your help!

---

