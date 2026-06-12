---
title: "tar error?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by dakota367 on 2009-03-18
When I try and install this file I get this output:

```
dakota@server:~/Desktop/SProtectLinux-3.0$ sudo ./SProtectLinux-3.0.bin
[sudo] password for dakota: 
tar: SProtectLinux-3.0-1171.0.i686.bin: Not found in archive
tar: Error exit delayed from previous errors
chmod: cannot access `/tmp/install.splx.tmp.single.14654/SProtectLinux-3.0-1171.0.i686.bin': No such file or directory
chown: cannot access `/tmp/install.splx.tmp.single.14654/SProtectLinux-3.0-1171.0.i686.bin': No such file or directory
./SProtectLinux-3.0.bin: 175: /tmp/install.splx.tmp.single.14654/SProtectLinux-3.0-1171.0.i686.bin: not found
```

I have tried to change permissions, I tried to run it from root terminal even logging in as root from SSH same thing every time.

Thanks for you help.

---

### Post by bodhi.zazen on 2009-03-18
md5 sum the file to make sure the download is not corrupt.

If the md5sum is OK, contact the developer.

---

### Post by dakota367 on 2009-03-18
> **bodhi.zazen said:**
> md5 sum the file to make sure the download is not corrupt.

If the md5sum is OK, contact the developer.

The MD5 was okay

---

### Post by dakota367 on 2009-03-18
Contacted the developer and they said they don't support ubuntu.

---

### Post by Rocket2DMn on 2009-03-18
Well that could be a problem!  What is this program that you are trying to install?  What is it for?  Perhaps we can help you find an alternative that is supported in Ubuntu.

---

### Post by dakota367 on 2009-03-18
> **Rocket2DMn said:**
> Well that could be a problem!  What is this program that you are trying to install?  What is it for?  Perhaps we can help you find an alternative that is supported in Ubuntu.

Its a server for a client server trend micro product.

---

### Post by bodhi.zazen on 2009-03-18
> **dakota367 said:**
> Contacted the developer and they said they don't support ubuntu.

Well tell him that is a lame excuse for his sloppy coding / packaging / .bin :)

j/k

the lack of ubuntu support should not affect the .bin, it should install

Now post install some things may be broken, or not work, that is different.

As Rocket said, what are you installing ?

---

### Post by Rocket2DMn on 2009-03-18
Ah, hmmm.  Well if you are running Ubuntu servers but need to run this product, I bet they support Red Hat which means you could install CentOS either on hardware, or inside a virtual machine.  Is that an option that is feasible for you?

---

### Post by sandyd on 2009-03-18
ive taken a look at it, and it should **technically** install on Ubuntu

however, i do have an interesting question.

why is that .bin file trying to untar itself???

---

### Post by sandyd on 2009-03-18
FYI, hes trying to isntall this

[http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/](http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/)

which, in my opinion, is a piece of junk

---

### Post by dakota367 on 2009-03-18
[http://www.trendmicro.com/download/product.asp?productid=20](http://www.trendmicro.com/download/product.asp?productid=20)

This is the product. I dont want to run a vm because the ram is less then a 1 GB.

---

### Post by dakota367 on 2009-03-18
> **carlee said:**
> ive taken a look at it, and it should **technically** install on Ubuntu

however, i do have an interesting question.

why is that .bin file trying to untar itself???

I was thinking the same thing??? I was just following there install instructions.

---

### Post by sandyd on 2009-03-18
P.S.

just found a interesting fact that will solve your problem

TrendMicro UK claims support for Debian, which means it will 99% isntall on ubuntu

[http://uk.trendmicro.com/uk/products/enterprise/serverprotect-for-linux/system-requirements/index.html](http://uk.trendmicro.com/uk/products/enterprise/serverprotect-for-linux/system-requirements/index.html)

WHile trend micro US claims no support for DEbian based distros

[http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/system-requirements/index.html](http://us.trendmicro.com/us/products/enterprise/serverprotect-for-linux/system-requirements/index.html)

maybe use the UK version? :D:D

---

### Post by sandyd on 2009-03-18
just download the version from Trandmicro UK and you get to complain all they wish because they claim support for Debian based distros

---

### Post by dakota367 on 2009-03-18
> **carlee said:**
> just download the version from Trandmicro UK and you get to complain all they wish because they claim support for Debian based distros

When I try and download the UK version it redirects me to the .com download center.

---

### Post by dakota367 on 2009-03-18
Do I need to change the directory permissions or anything?

---

### Post by dakota367 on 2009-03-19
I even tried to change the temp directory in the bin file and it still comes back with errors.

---

### Post by dakota367 on 2009-03-19
Here is the begigning of the file:

```

#!/bin/sh
Platform=$?
PackageInstalled=$?
splx_version=3.0
splx_release=1171
#ARCH=@@ARCH@@
PID=$$
tmpDir="/tmp/install.splx.tmp.single.$PID"
arg=""
onlyExtractSpecificPackage=0
installByCustomerChoice=0
customized_platform=""
customized_arch=""
listContent="You could use '-RedHat' to extract single package for redhat. And using 'SuSE' format to extract single package for SuSE."
serial_number=""
wtcSetings=""
set+wtc=0
set_serial_number=0



```

---

### Post by dakota367 on 2009-03-20
Any ideas?

---

### Post by dakota367 on 2009-03-23
Nothing

---

