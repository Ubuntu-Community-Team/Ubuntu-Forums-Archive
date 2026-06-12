---
title: "Can't install MPlayer (broken packages)"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by erans on 2009-10-12
Hello,

I was trying to fix my Mplayer to work with Ninjavideo (it was working fine, and then it just stopped working--maybe another thread on this later) and now I can't seem to reinstall it. 

I'm running Ubuntu 8.04. 

Here is the message I get when I try to install Mplayer: 

```
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
  mplayer: Depends: libasound2 (> 1.0.17) but 1.0.15-3ubuntu4 is to be installed
           Depends: libggi2 (>= 1:2.2.2) but it is not going to be installed
           Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
           Depends: libmad0 (>= 0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
           Depends: libmp3lame0 (>= 3.98) but it is not installable
           Depends: libopenal1 (>= 1:1.3.253) but it is not installable
           Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1.1 is to be installed
           Depends: libspeex1 (>= 1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
           Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages

```

Thanks a lot.

---

### Post by QIII on 2009-10-12
If you want to use a GUI to help, you can do it from Synaptic:

[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages")

---

### Post by diesch on 2009-10-12
What does ```
apt-cache policy mplayer
``` say?

---

### Post by mc4man on 2009-10-12
Check your sources, the mplayer that's trying to be installed was built for intrepid 
Maybe you've added a ppa and added the intrepid sources....?

---

### Post by erans on 2009-10-12
> **mc4man said:**
> Check your sources, the mplayer that's trying to be installed was built for intrepid 
Maybe you've added a ppa and added the intrepid sources....?

Yes, this was the problem. Thanks a lot everyone.

---

