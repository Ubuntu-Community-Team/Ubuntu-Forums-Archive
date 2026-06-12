---
title: "Synapic fails to install package- proken package"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by paul leo on 2009-04-24
Synaptic can't install 

libcurl4-gnutls-dev
because it can't find libgnuls-dev OR libdap2-dev

apt-get also fails ! - broken package!
#################

$ sudo apt-get install libgnutls-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgnutls-dev: Depends: libgnutls26 (= 2.4.1-1ubuntu0.2) but 2.4.1-1ubuntu0.3 is to be installed
E: Broken packages
################################

I need these since I want  want to get some R and bioconduction packages working but can't install Rcurl :

libcurl and curl are installed but I think I need libcurl4-gnuls-dev to fix this

Any ideas what to do next?

---

### Post by blazemore on 2009-04-24
try
```
sudo apt-get install libgnutls26
```

---

### Post by Big_Croc7 on 2009-04-24
No, it needs a different version.
```

libgnutls-dev: Depends: libgnutls26 (= 2.4.1-1ubuntu0.2) but 2.4.1-1ubuntu0.3 is to be installed
```
You'll have to find and install the older version of libgnutls26 (2.4.1-1ubuntu0.2).

---

### Post by omycron on 2010-01-22
So I think if you want to install RCurl (and other Bioconductor-Packages) you need this package:

libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)

```
sudo apt-get install libcurl4-openssl-dev
```

Mine is working :D

Hope it helped ...

---

