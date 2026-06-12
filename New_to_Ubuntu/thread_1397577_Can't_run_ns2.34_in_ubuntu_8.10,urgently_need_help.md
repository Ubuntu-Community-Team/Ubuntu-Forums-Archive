---
title: "Can't run ns2.34 in ubuntu 8.10,urgently need help"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by ritoban on 2010-02-03
I am using ubuntu 8.10.I have installed ns-2.34.It has shown the message that installation is successful.I did the validation which at last showed that all tests have passed.Before validation i changed the bash file.the changes are,i added the following lines at the end of the bash file(please note that i extracted my ns-allinone-2.34 folder at /home/ritoban)-

# LD_LIBRARY_PATH
OTCL_LIB=/home/ritoban/ns-allinone-2.34/otcl-1.13
NS2_LIB=/home/ritoban/ns-allinone-2.34/lib
X11_LIB=/usr/X11R6/lib
USR_LOCAL_LIB=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB:$X11_LIB:$USR_LOCAL_LIB

# TCL_LIBRARY
TCL_LIB=/home/ritoban/ns-allinone-2.34/tcl8.4.18/library
USR_LIB=/usr/lib
export TCL_LIBRARY=$TCL_LIB:$USR_LIB

# PATH
XGRAPH=/home/ritoban/ns-allinone-2.34/bin:/your/path/ns-allinone-2.34/tcl8.4.18/unix:/your/path/ns-allinone-2.34/tk8.4.18/unix
NS=/home/ritoban/ns-allinone-2.34/ns-2.34/
NAM=/home/ritoban/ns-allinone-2.34/nam-1.14/
PATH=$PATH:$XGRAPH:$NS:$NAM

after this i ran the command 

$ source ~/.bashrc

from the terminal & then restarted my machine.Then when i entered ns-2.34 directory & tried to run ns by typing the command "ns",instead of showing "%" at the terminal it showed the following. 

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-x server [name ...]]

I can't make out what is this,why is this being shown.Please help me sum1.I need it in my final year project.

Thanx in advance.

---

### Post by cariboo on 2010-02-03
What is displayed is the help menu, showing what options you need in order to get any output. The program you have is obviously command line only. I would suggest you have a look at the man page for an explanation of the command line options.

I don't have ns installed, but if you type:

```
man ns
```

you should see the man pages.

---

