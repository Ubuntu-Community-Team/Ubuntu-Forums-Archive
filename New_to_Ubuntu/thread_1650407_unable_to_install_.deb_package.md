---
title: "unable to install .deb package"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by beew on 2010-12-21
Hi,

I am trying to install a .deb package.  First tried gdebi and it is apparently not installed. I then tried the command line in the terminal. Here is the output. 

> monkeybrain@monkeybrain:~$ sudo dpkg -i odf-converter-integrator-chocolate_0.2.3_i386.deb
[sudo] password for monkeybrain: 
dpkg: error processing odf-converter-integrator-chocolate_0.2.3_i386.deb (--install):
 parse error, in file '/var/lib/dpkg/tmp.ci/control' near line 6 package 'odf-converter-integrator':
 duplicate value for `Package' field
Errors were encountered while processing:
 odf-converter-integrator-chocolate_0.2.3_i386.deb

Does anyone have an idea how to fix this? Thanks.

---

### Post by bodhi.zazen on 2010-12-21
> **beew said:**
> Hi,

I am trying to install a .deb package.  First tried gdebi and it is apparently not installed. I then tried the command line in the terminal. Here is the output. 



Does anyone have an idea how to fix this? Thanks.

I would file a bug report with whoever built the .deb =)

---

### Post by rburkartjo on 2010-12-25
be yes that happens sometimes whomever complies the deb makes a mistake. maybe do another google search and see if you can find another deb install of the same program. i have had luck doing that

---

### Post by tushar maroo on 2010-12-25
Report a bug with that deb file.:popcorn:

---

