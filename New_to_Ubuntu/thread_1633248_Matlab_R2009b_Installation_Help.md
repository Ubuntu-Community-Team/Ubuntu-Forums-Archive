---
title: "Matlab R2009b Installation Help"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by allthewine on 2010-11-29
I decided to switch to Ubuntu today so I installed it and then I tried to install Matlab R2009b. I followed the directions on this page: [https://help.ubuntu.com/community/MATLAB/R2009b](https://help.ubuntu.com/community/MATLAB/R2009b)
The directions said to write:[INDENT]sudo chown -R ${USER}:${USER} ~/.matlab
[/INDENT]So I made a directory called .matlab in the home directory before executing the command (was that bad?) but now I don't see it any more.

After that I followed the steps until I got to the "Setup gcc 4.2 for compiling Mex code" part. This command:[INDENT]sudo aptitude install gcc-4.2-multilib libstdc++6-4.2-dev
[/INDENT]just resulted in this error:[INDENT]sudo: aptitude: command not found
[/INDENT]Also, I tried clicking on the Matlab link in "Applications," which was for some reason called "Matlab R2009a," (not 2009b) and it resulted in the following error:[INDENT]Could not launch 'Matlab R2009a'
Failed to execute child process "matlab" (No such file or directory)
[/INDENT]What do I do now? I'm a total beginner and just got over my fear of Linux and command prompts.

---

### Post by Sub101 on 2010-11-29
> **allthewine said:**
> 
After that I followed the steps until I got to the "Setup gcc 4.2 for compiling Mex code" part. This command:[INDENT]sudo aptitude install gcc-4.2-multilib libstdc++6-4.2-dev
[/INDENT]just resulted in this error:[INDENT]sudo: aptitude: command not found
[/INDENT]

To fix this error run either: 

```
sudo apt-get install gcc-4.2-multilib libstdc++6-4.2-dev 
```

or 

```
sudo apt-get install apititude

then

sudo aptitude install gcc-4.2-multilib libstdc++6-4.2-dev

```

Aptitude is a package handler (as is apt-get) which is used to install programs.

As your trying to use matlab here are a few links to a few similar projects:

[http://www.gnu.org/software/octave/](http://www.gnu.org/software/octave/)
[http://www.scilab.org/](http://www.scilab.org/)

---

### Post by allthewine on 2010-11-29
Thanks a lot for the help. I figured out that ".matlab" is a hidden folder, and I installed Aptitude and the Gnu Compiler and all that, as directed. But for some reason Matlab still would not run. I figured maybe the link in the Applications menu is wrong, so I tried going into the /usr/local/matlabR2009b/bin where I installed Matlab and launching it using the icon. That didn't work. It only launched through this command:
[INDENT]sudo /usr/local/matlabR2009b/bin/matlab
[/INDENT]How do I make the applications menu "sudo run" Matlab automatically?

Also, once it turned on, it displayed this:
[INDENT]Warning: Executing startup failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:m_improper_grouping
Error: File: startup.m Line: 1 Column: 79
Unbalanced or unexpected parenthesis or bracket. 
> In matlabrc at 232
[/INDENT]What do I do?

---

### Post by Sub101 on 2010-11-30
> **allthewine said:**
> That didn't work. It only launched through this command:[INDENT]sudo /usr/local/matlabR2009b/bin/matlab
[/INDENT]How do I make the applications menu "sudo run" Matlab automatically?



If you right click in the menu you should have an option to edit menu.

Change the command to;

```
 gksudo /usr/local/matlabR2009b/bin/matlab
```

gksudo is the graphical way to use sudo.

Sorry - I cant help on the other problem, I have not used Matlab much.

---

### Post by Sigurgrímur on 2011-04-10
> **allthewine said:**
> 

Also, once it turned on, it displayed this:
[INDENT]Warning: Executing startup failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:m_improper_grouping
Error: File: startup.m Line: 1 Column: 79
Unbalanced or unexpected parenthesis or bracket. 
> In matlabrc at 232
[/INDENT]What do I do?


I had the same problem. In "starup.m" there is an extra ":" and a missing ")". Open the file by clicking on the link in the error message, change these two things and you are good to go. 
I worked for me.

---

