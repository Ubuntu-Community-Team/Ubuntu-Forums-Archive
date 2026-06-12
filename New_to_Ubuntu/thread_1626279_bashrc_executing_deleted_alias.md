---
title: "bashrc executing deleted alias"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by shigalla on 2010-11-20
Hi,

I am new to Ubuntu. I recently installed Ubuntu Lucid lynux and wanted to execute matlab. by adding an alias in bashrc:

*alias matlab='/usr/local/matlab6/bin/glnx86/matlab: not found*


Although the alias is already deleted in bashrc, it is still being executed every time I try to run matlab.:

*exec: 1: /usr/local/matlab6/....: not found. *

My question is how to get rid of this undesirable execution.

---

### Post by Hippytaff on 2010-11-20
Have you closed the terminal and then opened it again?

---

### Post by CharlesA on 2010-11-20
If you exit and reopen the terminal it should be fine.

Verify that the line is removed from .bashrc and reboot if it still doesn't work.

---

### Post by shigalla on 2010-11-20
Yes, I have tried to close and reopen the terminal and it didnt work. I even reinstalled Ubuntu but the same error still appeared!

---

### Post by sisco311 on 2010-11-20
EDIT: never mind.

---

### Post by shigalla on 2010-11-20
...and the line has already been removed as well.

---

### Post by The Cog on 2010-11-20
I think that you need to log out and back in again. Closing the terminal and starting another one while still in the GUI seems to re-use bash settings that were in place when the GUI was started.

EDIT:
Oops - slow typing - other answers have already invalidated mine. I'm out of ideas now.

---

### Post by shigalla on 2010-11-20
*Unalias matlab *

gives 

*bash: unalias: matlab: not found*

---

### Post by CharlesA on 2010-11-20
Post the output of this please:
```
alias
```

It sounds like a problem with matlab tbh, since you said you reinstalled Ubuntu.

---

### Post by shigalla on 2010-11-20
> **The Cog said:**
> I think that you need to log out and back in again. Closing the terminal and starting another one while still in the GUI seems to re-use bash settings that were in place when the GUI was started.

EDIT:
Oops - slow typing - other answers have already invalidated mine. I'm out of ideas now.
This doesnt work either

---

### Post by shigalla on 2010-11-20
> **CharlesA said:**
> Post the output of this please:
```
alias
```

It sounds like a problem with matlab tbh, since you said you reinstalled Ubuntu.
shigalla@mahongo:~$ alias
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'
shigalla@mahongo:~$

---

### Post by CharlesA on 2010-11-20
Yep, there's no alias for it. It's trying to run matlab directly and failing apparently.

---

### Post by sisco311 on 2010-11-20
***exec: 1:** /usr/local/matlab6/....: not found. *

is not a bash error. 

How did you install matlab and how do you invoke it?

---

### Post by shigalla on 2010-11-20
> **sisco311 said:**
> ***exec: 1:** /usr/local/matlab6/....: not found. *

is not a bash error. 

How did you install matlab and how do you invoke it?
I invoke matlab by typing matlab. I installed by following all the installation instructions for matlab6.

---

### Post by CharlesA on 2010-11-20
> **shigalla said:**
> I invoke matlab by typing matlab. I installed by following all the installation instructions for matlab6.

A link to the instructions you used would be nice. :)

---

### Post by shigalla on 2010-11-21
> **CharlesA said:**
> A link to the instructions you used would be nice. :)
```
shigalla@mahongo:~$ cd /usr/local/matlab
shigalla@mahongo:/usr/local/matlab$ sudo ./install_matlab
                     Welcome to MATLAB  R12  NORMAL Install
Be prepared to provide MATLAB system configuration information for the tasks:
    ---------------------------------------------------------------------
    |   ALWAYS DONE -                                                   |
    |  A1. Create scripts in $MATLAB/bin directory                      |
    |  A2. Install M-files in $MATLAB/toolbox/local directory           |
    |                                                                   |
    |   OPTIONAL (asked first) -                                        |
    |  B1. Create symbolic links to scripts in $MATLAB/bin directory    |
    |  B2. Install the FLEXlm Network License Manager                   |
    |                                                                   |
    |   ALWAYS DONE (if license manager is installed) -                 |
    |  C1. Create scripts in $MATLAB/etc directory                      |
    |  C3. Create template license.dat file in $MATLAB/etc directory    |
    |                                                                   |
    |   OPTIONAL (asked first if license manager is installed) -        |
    |  C2. Build symbolic links /etc/lmboot_TMW12, /etc/lmdown_TMW12    |
    ---------------------------------------------------------------------
Continue? ([y]/n) y
                      Verify MATLAB root directory path
                      ---------------------------------
    -------------------------------------------------------------------------
    | The MATLAB root directory path has been determined to be:             |
        $MATLAB = /usr/local/matlab
    | This path affects filesystem changes made in the following steps:     |
    |                                                                       |
    |     A1. Create scripts in $MATLAB/bin directory                       |
    |     B1. Create symbolic links to scripts in $MATLAB/bin directory     |
    |     C2. Build symbolic links /etc/lmboot_TMW12, /etc/lmdown_TMW12     |
    |     C3. Create template license.dat file in $MATLAB/etc directory     |
    |                                                                       |
    | Check the MATLAB root directory path carefully! If it is part of:     |
    |     1. An AUTOMOUNTED filesystem - the path must force a mount        |
    |     2. An AFS filesystem         - the path must be read-write        |
    | Press <return> if OK. Otherwise, provide the correct pathname below.  |
    -------------------------------------------------------------------------
MATLAB root directory? ([/usr/local/matlab])
--------------------->   /usr/local/matlab

                                Update MATLAB
                                -------------
Working . . .

Continue? ([y]/n) y
 A1. Create scripts in $MATLAB/bin directory
              -------------------------------------------
Creating MATLAB path . . .

Creating $MATLAB/bin scripts . . .
    Script         Changed?       Old Copy in bin/old
    ------         -------        ------------------- 
    cxxopts.sh       No
    engopts.sh       No
    gccopts.sh       No
    matlab           No
    matopts.sh       No
    mex              No
    mexopts.sh       No
    optsetup.sh      No
    .matlab6rc.sh    No
  A2. Install M-files in $MATLAB/toolbox/local directory
          -----------------------------------------------------
Creating $MATLAB/toolbox/local M-files . . .
    M-file         Changed?       Old Copy in toolbox/local/old
    ------         -------        -----------------------------
    matlabrc.m       No
    printopt.m       No
    docopt.m         No
 
Continue? ([y]/n) y
 B1. Create symbolic links to scripts in $MATLAB/bin directory
       -------------------------------------------------------------
 
    ------------------------------------------------------------------------
    | To make 'matlab' and 'mex' valid commands on your system you have    |
    | a choice of:                                                         |
    |                                                                      |
    | [a] Creating symbolic links to the $MATLAB/bin scripts in a          |
    |     directory of your choice that is already on your UNIX search     |
    |     path, or                                                         |
    |                                                                      |
    | [b] Adding the $MATLAB/bin directory to your UNIX search path.       |
    ------------------------------------------------------------------------
 
Do you want to create symbolic links to $MATLAB/bin scripts? ([y]/n) n
  B2. Install the FLEXlm Network License Manager
             ----------------------------------------------
    License manager scripts are missing . . .
    License manager installation skipped . . .
    To install the license manager scripts try:
    CD-ROM: Reinstall the item: FLEXlm 
    FTP:    Download the matlab.common file and reinstall.
Continue? ([y]/n) y
    ---------------------------------------------------------------------
    | Finished! This completes the:                                     |
    |                                                                   |
    |                  NORMAL install                                   |
    |                                                                   |
    |           for this host.                                          |
    ---------------------------------------------------------------------
shigalla@mahongo:/usr/local/matlab$
```

---

### Post by CharlesA on 2010-11-21
Try creating the symbolic links in step B1.

---

### Post by shigalla on 2010-11-24
> **CharlesA said:**
> Try creating the symbolic links in step B1.
The problem still persists even after creating a symbolic link.

---

### Post by shigalla on 2010-11-24
> **CharlesA said:**
> Try creating the symbolic links in step B1.
The problem still persists even after creating the symbolic link

---

### Post by shigalla on 2010-11-24
The problem still persists even after creating the symbolic link

---

### Post by shigalla on 2010-11-25
I have partly solved the problem after installing 32-bit java (sun-java6-jre) which I guess might be compatible to matlab6 that I have installed (Version 6.0.0.88 Release 12). The OS is ubuntu 64-bit and I have already installed 64-bit java. However during installation, I had changed the matlab root folder from matlab6 to matlab and now I am getting some warnings as shown below. But when I rename the matlab6 folder back to matlab, the matlab doesnt start at all. So how can I solve that?

 Warning: Directory access failure: /usr/local/matlab6/toolbox/Mexfiles.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 3
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 3
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
Warning: Directory access failure: /usr/local/matlab6/toolbox/m_map.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 4
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 4
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
Warning: Directory access failure: /usr/local/matlab6/toolbox/netcdf.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 5
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 5
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
Warning: Directory access failure: /usr/local/matlab6/toolbox/netcdf/ncfiles.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 6
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 6
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
Warning: Directory access failure: /usr/local/matlab6/toolbox/netcdf/nctype.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 7
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 7
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
Warning: Directory access failure: /usr/local/matlab6/toolbox/netcdf/ncutility.
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 8
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182
> In /usr/local/matlab/toolbox/matlab/general/path.m at line 116
  In /usr/local/matlab/toolbox/matlab/general/addpath.m at line 88
  In /usr/local/matlab/toolbox/local/startup.m at line 8
  In /usr/local/matlab/toolbox/local/matlabrc.m at line 182

---

