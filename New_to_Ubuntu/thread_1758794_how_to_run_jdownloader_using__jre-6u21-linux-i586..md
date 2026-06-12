---
title: "how to run jdownloader using  jre-6u21-linux-i586.bin"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by mr.akik on 2011-05-15
I downloaded  jre-6u21-linux-i586.bin and installed it in my home directory.now when I try to install jdownloader it says java is not installed.Please tell me how I can solve this problem.I don't want to install jre from synaptic.I know how to do that.I just want to know how to do that using the bin file.

---

### Post by manishraj2011 on 2011-05-15
> **mr.akik said:**
> I downloaded  jre-6u21-linux-i586.bin and installed it in my home directory.now when I try to install jdownloader it says java is not installed.Please tell me how I can solve this problem.I don't want to install jre from synaptic.I know how to do that.I just want to know how to do that using the bin file.
Delete the jre folder in your home directory.... it won't work from there ( I don't know why but I had the same problem )

Follow these instructions :

# Steps to install Sun jre :

1) Download the bin file ( You have the bin file ... right ???? )

2) make the file executable :

chmod u+x <file>

3) sudo -s # To gain root access #

4) cd /usr

5) mkdir java

6) cd java

7) /<download path>/<downloaded file>
     
    e.g.   /home/username/Downloads/jre-6u21-linux-i586.bin

I think this should solve your problem...

---

### Post by mr.akik on 2011-05-15
wow.... it works perfectly.u r a genius. thank u very much.

---

