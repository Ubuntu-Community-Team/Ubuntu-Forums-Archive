---
title: "Is my Ubuntu secure?"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by luciduser on 2010-03-24
I am a non-technical user. I have installed ubuntu. I have removed some software and added some more using the Ubuntu Software Center. I have visited the forum's security pages and that's where the trouble begins!

The security pages suggest installing intrusion detection software, reading logs, checking for rootkits... these tasks are all beyond my current Ubuntu skills. I'm a beginner, these are all beyond me.

As a beginner user I have added and removed software BUT I haven't installed intrusion detection software, checked logs, or checked for rootkits.

Is my Ubuntu secure?

Is it safe for me to use Ubuntu without taking all these security precautions OR, as a non-technical user, should I be using Windows instead?

---

### Post by Surkow on 2010-03-24
If you only install programs from trusted sources (Ubuntu repositories) there is nothing to worry about. Ubuntu is reasonable secure by default.

---

### Post by J V on 2010-03-24
> Is it safe for me to use Ubuntu without taking all these security precautions OR, as a non-technical user, should I be using Windows instead?This made me laugh :)

As the above poster said, as long as you don't go around the interwebz downloading and installing everything you can see, you will be fine.

Don't even need a virus scanner or firewall, everything is secure from the get-go...

Windows however...

---

### Post by 2hot6ft2 on 2010-03-24
I think you may be confusing the server edition with the desktop edition. When running a server then you would want and possibly need intrusion detection software but for a normal desktop user you shouldn't need to worry about it unless you start installing things like ssh, vnc etc...

You should be fine unless there's some special reason why you're concerned that you haven't mentioned.

---

### Post by kaldor on 2010-03-24
Ignore the security warnings unless you are a server host.

If you share files frequently with Windows users, a virus scanner may help; but I never use one.

If you are a non-technical user, I recommend Ubuntu. For a few reasons...

1) Copy-paste commands into a command line to do things. People can simply tell you what to copy/paste, and you can just paste things in without having to do much at all.

2) Learn more without problems; with Ubuntu, you may need some technical knowledge in *some* areas. 

3) Easier file system to use. The /home/yourname setup is much simpler than Windows' C:/ nonsense.

4) Repository; don't need to go to sites for stuff as much, can just use the Software Centre

5) As a non technical user, you can relax knowing you won't mess up your computer unless you specifically make something happen.

6) Can keep updating it forever. Free. 

etc.

Nice job trying Ubuntu. Don't give up, you're getting the hang of it :)

---

### Post by luciduser on 2010-03-24
No special reason for my concern. I'm a desktop user.

JV said... Don't even need a virus scanner or firewall...

Do I need to enable the firewall? There's an 'Enabled' checkbox in Gufw. Does installing Gufw and 'enabling' it improve my security?

Thanks for the replies. :P

---

### Post by kaldor on 2010-03-24
> **luciduser said:**
> No special reason for my concern. I'm a desktop user.

JV said... Don't even need a virus scanner or firewall...

Do I need to enable the firewall? There's an 'Enabled' checkbox in Gufw. Does installing Gufw and 'enabling' it improve my security?

Thanks for the replies. :P

Only really needed if you're paranoid/hosting a server. If you want, enable it. But, it won't really do much. I haven't used a firewall on my laptop in the few years I used Ubuntu.

---

### Post by sixthwheel on 2010-03-24
I'm running Nortons Linux Security Version 0.0:p
Sorry, couldn't help myself.

---

### Post by jd65pl on 2010-03-24
The kernel already contains a firewall there are tools available to configure it such as [iptables]("http://en.wikipedia.org/wiki/Iptables") but it will do the job its self without any manual configuration

---

### Post by QIII on 2010-03-24
Installing a virus in Windows is a single step process:  Go to an infected website without a condom.

It is somewhat more of a challenge in Linux.  It is best not to be overconfident, because I keep saying that it is possible that some PFY in Des Moines is at this very moment uploading something that will destroy us all.

And don't discount the very real danger of "social engineering" and allow yourself to be fooled into installing something you shouldn't.  Stick with the repos and trusted sources.  Some trusted sources are places like Sun, VirtualBox.org, etc.  If you don't know, come here and ask.

But, a bit of humor from the email archives of the GNU Project:


evilmalware 0.6 (beta)
  Copyright 2000, 2001, 2003, 2005 E\/17 |-|4><0|2z Software Foundation, Inc.
  This is free software; see the source for copying conditions. There is NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra spams to people accross the world).
  **Basic Installation**

  Before attempting to compile this virus make sure you have the correct version of glibc installed, and that your firewall rules are set to &#8216;allow everything&#8217;.
  
[LIST=1]
[*]Put the attachment into the appropriate directory eg. /usr/src.
[*]Type &#8216;tar xvzf evilmalware.tar.gz&#8217; to extract the source files for this virus.
[*]&#8216;cd&#8217; to the directory containing the virus' source code and type &#8216;./configure&#8217; to configure the virus for your system.  If you're using &#8216;csh&#8217; on an old version of System V, you might need to type &#8216;sh ./configure&#8217; instead to prevent &#8216;csh&#8217; from trying to execute &#8216;configure&#8217; itself.
[*]Type &#8216;make&#8217; to compile the package. You may need to be logged in as root to do this.
[*]Optionally, type &#8216;make check_payable&#8217; to run any self-tests that come with the virus, and send a large donation to an unnumbered Swiss bank account.
[*]Type &#8216;make install&#8217; to install the virus and any spyware, trojans pornography, penis enlargement adverts and DDoS attacks that come with it.
[*]You may now configure your preferred malware behaviour in /etc/evilmalware.conf.
[/LIST]

---

### Post by luciduser on 2010-03-24
Thanks for all the replies. 

I'm now quite happy that my Ubuntu IS secure. :D

But I'm still confused as to whether 'enabling' Gufw improves my already secure Ubuntu or makes no difference.

Checking logs is definitely beyond me, but I can select a checkbox like a pro! :p

---

### Post by bodhi.zazen on 2010-03-24
> **luciduser said:**
> Thanks for all the replies. 

I'm now quite happy that my Ubuntu IS secure. :D

But I'm still confused as to whether 'enabling' Gufw improves my already secure Ubuntu or makes no difference.

Checking logs is definitely beyond me, but I can select a checkbox like a pro! :p

For the vast majority of Desktop users who are using a router to connect to the internet enabling your firewall is on almost no benefit.

There is the small chance one would accidentally install a server, such as VNC, and accidentally forward a port from your router in which case it *might* help, although such a user is also likely to accidentally open a port in his or her firewall as well, so questionable.

See this post : [Ubuntu Forums - View Single Post - General Security ?]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236")

I would not suggest you ignore security, but security on any OS is complex and you need to understand how the OS works and how networking protocols work.

As you become more familiar with linux, read this thread:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by quadproc on 2010-03-24
To check the main logs in your system, use System > Administration > Log File Viewer.  Logs tend to grow pretty rapidly and are usually not interesting unless you are chasing down a specific problem.

You can also look in the file system for logs.  Most are found in /var/log.  To see a list of these, try
```
ls /var/log
``` in a terminal.  You'll note that the same logs as the System > Admin selection are present, plus a lot more.  Most of the extra ones are old logs which the system has saved and compressed for you, so that you can go back a ways in time if necessary.  Eventually the system discards such old logs so please don't count on them being around forever.

I find it easier to examine alog with an editor, so I often copy the log of interest to a temporary file and then use an editor to examine and search it.

quadproc

---

### Post by tekkidd on 2010-03-24
linux in general is really secure because unlike windows who in the name of "convinence" gives the user automatic root rights. this means that once a person has access to your comp he can mess things up really bad. linux on the other hand instead of giving the user direct root rights gives him premission to get root rights so if a hacker gets in he cant do crap because he does not have premission.

---

