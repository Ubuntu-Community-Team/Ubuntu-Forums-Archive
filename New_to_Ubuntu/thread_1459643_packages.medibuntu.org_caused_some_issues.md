---
title: "packages.medibuntu.org caused some issues"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by sprinj76 on 2010-04-21
Hi all,
I am running Ubuntu x86 9.10 karmic.
I tried to install the program devede, not knowing that packages.medibuntu.org was down. I did this via synaptic package manger. During the download of the dependencies the download failed because medibuntu was unvailable, and the installation of devede could not be completely. 

Now that packages.medibuntu.org is back up, when I try to install devede via synaptic i get errors. I tried installing through the terminal and I also get errors. 
```
~$ sudo apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  devede: Depends: mencoder but it is not going to be installed
          Depends: mplayer-nogui but it is not going to be installed
          Depends: libavcodec-extra-52 but it is not going to be installed
          Depends: libavformat-extra-52 but it is not going to be installed
E: Broken packages

```

can anyone help me? I'm not familiar enough with ubuntu/linux to know what has broke, or how to fix it.

---

### Post by ed-koala on 2010-04-21
See this thread - [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=947124")

---

### Post by sprinj76 on 2010-04-21
I checked out that thread, which was interesting but it didn't help my situation. I ended up trying to install mencoder which gave me a bunch of errors, i took one of the dependencies there and tried to install it, which gave me errors, I tried one more dependency which finally installed. 

Once I got this installed I went to synaptic and checked devede which installed fine, and actually removed the dependency that I just installed before . . . but either way its working now. 

I can't believe the difficult problems that arise from a server being down . . .

---

