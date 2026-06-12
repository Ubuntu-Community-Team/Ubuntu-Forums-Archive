---
title: "redrat drivers problem"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by campetto on 2009-02-07
Hi everyone!
I'm trying to install drivers for redrat(infrared encoder/decoder) on kubuntu 8.04 kernel 2.6.24-19-generic. I'm doing exactly as said [here ]("http://www.redrat.co.uk/software/linux/lirc-rr3-0.4.txt") and after i execute ./autogen.sh it returns me:

...
tools/Makefile.am:56: HAVE_PYTHON does not appear in AM_CONDITIONAL
autoreconf: automake failed with exit status: 1
tools/Makefile.am:56: HAVE_PYTHON does not appear in AM_CONDITIONAL
Creating setup-driver.sh ...

after executing ./setup.sh it returns me:

...
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in

and cannot execute make, it's missing.
So if anyone can please help me and try to do it yourself as in link and tell me what am I doing wrong. I'm not very expirienced in Linux and I'm doing this voulentery for one hospital and people who need it, so please  help.
pardon my english.

---

### Post by blueridgedog on 2009-02-07
Do you have python on your system?  I think it is included by default:

```
sudo apt-get install python
```

Otherwise, try dropping the author a note.  His email is here:

[http://www.speakeasy.org/~schmerge/](http://www.speakeasy.org/~schmerge/)

---

### Post by kiddjmadd on 2010-09-22
i had a similar issue. I think one of the updates to LIRC CVS code subsequent to the redrat3 instruction getting published  must have broken the instructions. To work around it i had to copy & paste bits & pieces between the stable LIRC code and latest code from CVS. Nothing too sophisticated / 31337, just getting it set so autogen.sh would run in the stable LIRC code top level. this refreshes setup.sh to recognize the redrat3 driver added to the replacement setup.data file. Once it's in as a menu selection and you get through the autogen errors (for me the configure.ac file was missing some needed declarations) you're home free.
I'm spoiled with "apt-get" & previously "yum" so it took me a couple hours to run through the scripts, try different things and get it going. Back in my slackware days it would have taken 15 minutes. Oh well.
Suffice it to say, it is a good driver & can work as attached image shows. unfortunately it's not officially in the LIRC package so users may need to apply effort if the LIRC dev's break any of the interfaces the original instructions from redrat's site rely on. 
If anyone runs into this & needs more detailed instruction, reply to post & I'll see if I can assist.

cheers,
Jesse

---

