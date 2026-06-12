---
title: "problem runing jason , if: Badly formed number"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by iageoscience on 2011-05-08
I have a program called jason I installed it correctly and when I run it 
in terminal I have the following error if: Badly formed number .
I installed csh and tcsh and tried to run it from both shells plus bash also .
I have the same error .
I installed this program on centos 5 before and it was working very great .
I googled this error and I found the reason to be 
if this is the case so why it was working on centos ?
is there any reason for that error ?
by the way this is not a script of mine it is a geophysics software  .

here is the output I have when I run csh -x jason

ibrahim@geo:~/jason$ csh -x jason
setenv JG_TOPDIR /home/ibrahim/jason
setenv VERSION 8.0
setenv JLM_CO_VER 8.000
setenv JG_LOCAL_SCRIPT /home/ibrahim/jason/local/bin/machind
setenv JG_SCRIPT /home/ibrahim/jason/bin/machind
setenv JGECHO printf
setenv JG_APPLOGFILE /home/ibrahim/JASON_LOGS/Jg_AppLogfile
setenv JGARCH `uname -s`
uname -s
foreach CLIENT_SCRIPT ( /home/ibrahim/jason/local/bin/machind/jwclient.csh /home/ibrahim/jwclient.csh )
if ( -f /home/ibrahim/jason/local/bin/machind/jwclient.csh ) then
source /home/ibrahim/jason/local/bin/machind/jwclient.csh
unsetenv JG_CACHEDIR
unsetenv JG_PLOTDIR
unsetenv JG_SNAPDIR
unsetenv JG_HOME_DIR
unsetenv JGW_NO_PBUFFER
unsetenv JGW_NO_SNAPSHOT
unsetenv JG_CGM_PREVIEWER
endif
end
if ( -f /home/ibrahim/jwclient.csh ) then
end
set LL========================================================================
switch ( `uname -s | awk '{print $1}'` )
uname -s
awk {print $1}
if ( -f /etc/SuSE-release ) then
if ( -f /etc/redhat-release ) then
setenv metalinversion Unknown
if ( `uname -r | cut -c 1-3` = 2.0 ) then
uname -r
cut -c 1-3
if: Badly formed number.

---

### Post by gmargo on 2011-05-08
> **iageoscience said:**
> 
```

if ( `uname -r | cut -c 1-3` [COLOR=Red]=[/COLOR] 2.0 ) then

```
I can't explain why it works on CentOS, but this C-shell expression is invalid. Like the C language, it should use "==" and not "=".  Try this instead:
```

if ( `uname -r | cut -c 1-3` [COLOR=Red]==[/COLOR] 2.0 ) then

```

---

### Post by iageoscience on 2011-05-10
Thank you very much I edited the lines and the program started successfully ,
in centos I enter these commands to enable visual selections of files in the program 

cd /usr/X11R6
mkdir lib ; cd lib 
ln -s /usr/share/lib .

in ubuntu there is not /usr/X11R6 directory 
is there any alternative to the above commands in ubuntu ?

---

