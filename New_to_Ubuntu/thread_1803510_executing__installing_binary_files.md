---
title: "executing / installing binary files"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by margaux on 2011-07-13
Hi, 

I'm trying to install several programs including MACH 1.0, plinkseq, Merlin, and minimac. I am brand new to the Linux OS and all the associated jargon, and just need a very simple step by step explanation of how to get this things up and on my system.

I think if I can figure one out, I can figure out the rest, so I'll just copy the code line I'm using when trying to install plinkseq. Now, the website has this information:

PSEQ is a statically-compiled Linux binary. Download with curl:


  curl -O [http://atgu.mgh.harvard.edu/plinkseq/dist/pseq-0.05-x86_64.tar.gz](http://atgu.mgh.harvard.edu/plinkseq/dist/pseq-0.05-x86_64.tar.gz) 

  or 


 
   wget [http://atgu.mgh.harvard.edu/plinkseq/dist/pseq-0.05-x86_64.tar.gz](http://atgu.mgh.harvard.edu/plinkseq/dist/pseq-0.05-x86_64.tar.gz)

  Unpack: 
  tar -xvzf pseq-0.05-x86_64.tar.gz   
chmod +x plinkseq-x86_64-0.05/pbrowse

 Finally, copy the files to somewhere in your command path:


  cp plinkseq-x86_64-0.05/* /usr/local/bin

 You then should be able to start PSEQ by typing    pseq.


Here is where my issues begin. I get as far as the 2nd to last step (cp plinkseq-x86_64-0.05/* /usr/local/bin) with no problems, but when I type pseq, I get this error message:

bash: /usr/local/bin/pseq: cannot execute binary file

GAH. I am convinced there is a very easy solution to this problem. Any assistance would be greatly appreciated.

---

### Post by oldos2er on 2011-07-13
Try making pseq executable ```
sudo chmod +x /usr/local/bin/pseq
```

---

### Post by seawolf167 on 2011-07-13
Double check if the file is executable. Also, is your installation an 64 bit install or 32 bit install? It looks like the package file is for a 64 bit system (*x86_64).

If you don't know, you can find out from entering this at a terminal

```
uname -a
---or---
file /sbin/init
```

---

### Post by margaux on 2011-07-13
Thanks for your replies. Those commands give me the same error messages. 

sudo chmod +x /usr/local/bin/pseq
pseq

I get

bash: /usr/local/bin/pseq: cannot execut binary file

Entering
pseq /sbin/init 

gives me the same error message.

Entering 
uname -a 

gives me:
Linux margaux-laptop 2.6.32-32-generic #62 Ubuntu SMP time stamp i686 GNU/Linux

Any ideas?

---

### Post by seawolf167 on 2011-07-13
> **margaux said:**
> 
Entering 
uname -a 

gives me:
Linux margaux-laptop 2.6.32-32-generic #62 Ubuntu SMP time stamp** i686** GNU/Linux


Looks like you are using x86 (32 bit machine) but want to execute an x86_64 package (64 bit - from the filename "plinkseq...-**x86_64**.tar.gz")

---

### Post by margaux on 2011-07-13
A-ha. Well, at least it's not personal.

Is there anything I can about this? PlinkSeq is only offered on the x86_64 platform.

---

