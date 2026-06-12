---
title: "help please XBMC installation"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by artoflife10 on 2010-08-10
this is my first day with ubuntu. i installed ubuntu 10.04 then upgraded it to ubuntu studio (as i am a bit into graphics and stuff). now i want to install XBMC media center on my laptop. i am using lenovo y550P ideapad.
but when i try and use the standard process i get an error that XBMC not found. i really want this is there any way i can get this or should i switch to ubuntu 9.10? please suggest me.

---

### Post by thatguruguy on 2010-08-10
> **artoflife10 said:**
> this is my first day with ubuntu. i installed ubuntu 10.04 then upgraded it to ubuntu studio (as i am a bit into graphics and stuff). now i want to install XBMC media center on my laptop. i am using lenovo y550P ideapad.
but when i try and use the standard process i get an error that XBMC not found. i really want this is there any way i can get this or should i switch to ubuntu 9.10? please suggest me.

I am not entirely sure what you mean when you state that you used the "standard process."  You may want to follow the instructions listed here (if you have not already done so): [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)

---

### Post by viditgoyal3009 on 2010-08-10
> **artoflife10 said:**
> this is my first day with ubuntu. i installed ubuntu 10.04 then upgraded it to ubuntu studio (as i am a bit into graphics and stuff). now i want to install XBMC media center on my laptop. i am using lenovo y550P ideapad.
but when i try and use the standard process i get an error that XBMC not found. i really want this is there any way i can get this or should i switch to ubuntu 9.10? please suggest me.
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

check out this link

---

### Post by artoflife10 on 2010-08-10
i have done it before but this is the message i get at the end when i follow the steps

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbmc

thanks for the timely reply.

---

### Post by bergfly on 2010-08-10
artoflife10

XBMC is not in the standard list of software that Ubuntu accesses (what we call repositories) Hence in order to get it, you need to add additional sources for your package manager (installer) to look at or simply install from a different location 

The link provided above will take you step by step through this. The quick way to do it would be the section entitled 

Installing XBMC Ubuntu 9.10 Karmic or higher

You will need to cut and paste this into a terminal window one line at a time. Terminal is under Applications -> accessories

---

### Post by papibe on 2010-08-10
Same problem here. After doing this successfully:

```
$ sudo apt-get install python-software-properties pkg-config
$ sudo add-apt-repository ppa:team-xbmc
$ sudo apt-get update

```

and, checking both "Community-maintained open Source software (universe)" and "Software restricted by copyright or legal issues (multiverse)" on Administration -> Software Source

I have problem with the install:

```

pablo@vaughan:~$ sudo apt-get install xbmc xbmc-standalone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbmc


```

---

### Post by LowSky on 2010-08-10
follow the instructions from here first
[http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step#Adding_the_XBMC_Repo](http://wiki.xbmc.org/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step#Adding_the_XBMC_Repo)

---

### Post by papibe on 2010-08-10
Same result. Besides:

```
pablo@vaughan:~$ apt-cache search xbmc
texlive-latex-extra - TeX Live: LaTeX supplementary packages
libnfo1 - an NFO file parser/writer library
xbmc-ppa-keyring - GnuPG archive keys for the XBMC PPA

```

So, the only package added was xbmc-ppa-keyring.

---

### Post by papibe on 2010-08-10
It looks like the ppa is NOT working these days. Check these posts from the XBMC's forums:

[INDENT][PPA wiped]("http://forum.xbmc.org/showpost.php?p=582147&postcount=893")

[PPA fuxxored]("http://forum.xbmc.org/showpost.php?p=582413&postcount=2") (is that even a word?)[/INDENT]

 :(  ...bad luck today.

---

### Post by SLamontagne on 2010-08-10
Hi
I am currently experiencing the same problem.
It is not the first time I install Ubuntu on a Zotac MAG but for some reason today XBMC seems to be vanished from the ppa:team-xbmc.

Like the previous poster I only get the xbmc-keyring package

> sudo apt-cache search xbmc
texlive-latex-extra - TeX Live: LaTeX supplementary packages
libnfo1 - an NFO file parser/writer library
xbmc-ppa-keyring - GnuPG archive keys for the XBMC PPA

---

### Post by Jamikest on 2010-08-10
:grumble: :grumble:

I just had the bright idea a few days ago to wipe my old Mythbuntu build and try out xbmc...  lol

This is not a good start to my changing projects, with the ppa borked and all. 

Verified that both 32 and 64 bit ppas are down.

---

### Post by artoflife10 on 2010-08-11
i have gone through the xbmc forum and found that ppa is not working so any body know when it can be back or is it broken permanently??

thanks for all the replies.

---

### Post by Jamikest on 2010-08-22
If you are still following this thread, 

The PPA is up and working! yay!

Successfully built XBMC, and the children are happily watching a movie as I type this.

---

