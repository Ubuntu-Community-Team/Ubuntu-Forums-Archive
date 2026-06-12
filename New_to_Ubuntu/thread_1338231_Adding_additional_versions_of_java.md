---
title: "Adding additional versions of java"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Master_Ne0 on 2009-11-26
Hi,

I'm new to Ubuntu and this forum. Tried to searching for solutions to this problem, but nothing seems to work.

I have done an install of java using ```
sudo apt-get install sun-java6-jdk 
``` this has installed java version "1.6...." though some of my development work needs to be done with version 1.5. I then used  ```
sudo apt-get install sun-java5-jdk 
``` to try and install the older version as well bu it cant seem to find and install the version "1.5...." that i need.

Can someone please advise me on how to install the other version of java and how to switch between using the different versions.

Thanks.

---

### Post by Jive Turkey on 2009-11-26
To select the version of java for your OS, use:
```
update-java-alternatives
```
It will offer a choice of which to use.

I'm not sure if your IDE (if any) overrides these or not but they usually want to know the path to your java stuff.

As far as installing multiple versions it seems like synaptic might be able to do it but I'm not sure if it can.

AFAIK sun-java5-jdk is version 1.5, they just have a funny numbering system.

---

### Post by Master_Ne0 on 2009-11-27
Thanks,

I have tried the synaptic but it doesn't have it as a package any more. I may have to try downloading the package manually if nothing else.

---

