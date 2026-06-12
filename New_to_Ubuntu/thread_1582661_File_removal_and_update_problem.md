---
title: "File removal and update problem"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Zaiaku on 2010-09-26
Hey...Im still kinda new to Ubuntu but not entirly anymore.
The problem is I installed some software(DJPlay and JACK) along with libdjconsole_0.1.2=2_i386.deb.  Both installed fine but JACK wouldnt run...I think I installed it wrong.  I tryed to remove it threw Ubuntu software center and it gave me an error:  The package system is broken.  Check if you are using third-party repositories. If so, disable them, because they are a common source of problems.
Furthermore, run the following command in a Terminal: apt-get install -f


I tryed that and nothing...Still couldnt remove eather JACK or DJPlay. both gave me the same message.

Second problem with "libdj..." I want to remove it but not sure how also Update manager gives me: You have 1 broken package on your system!
Use the "Broken" filter to locate it.
Followed by: An error occurred
The following details are provided:
E: /var/cache/apt/archives/libdjconsole-data_0.1.3-1ubuntu1_all.deb: trying to overwrite '/usr/share/libdjconsole/06f8-b000.buttons', which is also in package libdjconsole 0
E: /var/cache/apt/archives/libdjconsole0_0.1.3-1ubuntu1_i386.deb: trying to overwrite '/usr/lib/libdjconsole.so.0.0.0', which is also in package libdjconsole 0

I want to remove the programs and those files and I dont know how...Well I know how I can remove the files rm -r in the directory in a terminal...but I mean uninstall them...I dun wanna go threw every file and do it manually despite thats what I may have to do the the lib files....

---

### Post by Zaiaku on 2010-09-28
Ok so I'm an idiot...And the ubuntu software center told me wrong

I found out what was wrong with the command I was trying to use....Was using "apt-get install -f"  when i was suspose to use "apt-get -f install"  Used that and the DJplay problem was solved....

That being said, the other part, the Broken part...still remains...i'll make sure that a restart dont fix this but ya....

---

### Post by Paqman on 2010-09-28
Go to System > Admin > Synaptic Package Manager and click on the filter for "broken" on the left. It'll show you the broken packages and give you the option to fix them.

---

### Post by Zaiaku on 2010-09-28
Restarted and this came in
An error occurred

The following details are provided:
E: /var/cache/apt/archives/libdjconsole-data_0.1.3-1ubuntu1_all.deb: trying to overwrite '/usr/share/libdjconsole/06f8-b000.buttons', which is also in package libdjconsole 0
E: /var/cache/apt/archives/libdjconsole0_0.1.3-1ubuntu1_i386.deb: trying to overwrite '/usr/lib/libdjconsole.so.0.0.0', which is also in package libdjconsole 0


And ya I did the Broken filter thing but under Broken it only has one thing there and its installed.

Also thanks for helping me find that

---

### Post by Paqman on 2010-09-29
> **Zaiaku said:**
> 
And ya I did the Broken filter thing but under Broken it only has one thing there and its installed.


If you right click on it, what options do you get?

---

### Post by Blook on 2010-09-29
It seems a little strange!

---

