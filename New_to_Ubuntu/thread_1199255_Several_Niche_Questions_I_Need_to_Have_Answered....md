---
title: "Several Niche Questions I Need to Have Answered..."
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Groucho Marxist on 2009-06-28
... Prior to Purchasing a System 76 Linux Laptop.

My mom, awesome woman that she is, is considering purchasing a System 76 laptop for me as a reward for maintaining my +3.5 college GPA :D

However, she wanted to know several answers to important questions; she is a fairly advanced computer user (i.e. she immediately started asking about Linux's GUI and things of that nature) but is unfamiliar with Linux. Here are her questions:

[LIST=1]
[*]Will we have problems with hackers if we do not use I.E. (Internet Explorer)? (She says that "Firefox is one of the worst when it comes to security.")
[*]Will we have to use McAfee or Norton for anti-virus protection?
[*][I explained to her that there are no viruses, malware... etc] Why is it that these unwanted applications do not affect Linux?
[*]If Ubuntu is free of charge, how does it [Cannonical] earn revenue?
[*]
[/LIST]

---

### Post by WRDN on 2009-06-28
1) No. Firstly, Firefox is more secure than IE, but more importantly, the firewall installed by default (iptables) opens no ports by default, meaning it is very hard to hack into the system.

2) No, there are no virus 'in the wild' for Linux, so no antivirus software is needed. The only reason you may want it is if you are sharing files with Windows users, and/or dualbooting. Ubuntu cannot be infected by virus', but it can pass them on.

3) Most viruses are made for Windows and are .exe's. These do not run on Linux by default, which uses the ELF executable format (Executable and Linkable Format). You can run exe's in Ubuntu using WINE (Wine Is Not an Emulator), which provides libraries, allowing some programs to run. Even if you run a virus in WINE, you will still get no virus. For more info, see [http://www.linux.com/archive/feature/42031](http://www.linux.com/archive/feature/42031)
As well as this, Linux implements a very secure permissions system. To change/add/remove any file outside the your personal home folder (/home/username), you need to enter your password and have administrative rights (i.e. ability to use sudo).
To ensure you have the most secure system though, I would recommend only installing software from a trusted source (if possible, install from the official repositories), and keep the system up to date.

4) Canonical make money through support etc.

---

### Post by Locutus_of_Borg on 2009-06-28
1: lol...IE is the worst, security wise, browser next to Safari.  Firefox is probably the most secure.  Firefox + NoScript = safest browser available.  But if you insist, you can still use IE on Linux (though the prospect is painful to envision)

2: You will not need any virus protection unless you plan on sharing files with Windows computers.  There do not exist Viruses for Linux (at least none ever reported caught in the wild)  

3: These malware do not affect Linux due to the security structure Linux implements.  Firstly, nothing a user executes can have any affect on the system without first giving that executable root permissions.  Secondly, to install software on Linux, you do not search around on Google for shady looking warez and cracked applications, you install from a certified repository of software.  Thirdly, so long as you do not download unknown applications, do not modify their permissions, and do not specifically allow the program to affect outside of the user's home directory, there is no such way for malware to infect a Linux host.  And if somehow it did, the removal of such software would be as simple as deleting some files as there is no such registry for malware to hide in and re-install itself.  The only Linux malware around are rootkits.  Ubuntu does not have a root account enabled by default, nor does it have services listening on any ports through which the rootkit would have to operate by default.  So long as you do not set yourself up for infection, you will not be infected.

4: The dude who owns Canonical is like a billionaire.  Canonical is not a profit oriented business although they do sell some services.

---

### Post by jerome1232 on 2009-06-28
Will we have problems with hackers if we do not use I.E. (Internet Explorer)? (She says that "Firefox is one of the worst when it comes to security.")

Well you have several browsers to choose from, Opera and Firefox being the major browsers. IE's track record is much worse when it comes to security compared to Firefox ;) There are a few addon's that make firefox a very secure browser, like addblock, no script, and flashblock.

Will we have to use McAfee or Norton for anti-virus protection?
[I explained to her that there are no viruses, malware... etc] Why is it that these unwanted applications do not affect Linux?[/quote]

I think this is a good start for reading about Linux and Security [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

If Ubuntu is free of charge, how does it [Cannonical] earn revenue?


I think the best place to find out about Canonical is their website [http://www.canonical.com/aboutus](http://www.canonical.com/aboutus)
I know they sell support for Ubuntu systems.

---

### Post by RequinB4 on 2009-06-28
> **Groucho Marxist said:**
> 
Will we have problems with hackers if we do not use I.E. (Internet Explorer)? (She says that "Firefox is one of the worst when it comes to security.")

Not as long as you don't purposefully screw up your system, which is unlikely.  Firefox is much more secure than IE. 

(As a moot point since you'll be running ubuntu, real-life "hackers" as it were aren't really a threat to desktops, since you're probaly not a target, hence the trojan problem on windows.)  

If you were for some reason worried about a malicious person manually gaining control of your computer I'd be less worried about your browser and more worried about what services and ports you're using.  Ubuntu by default has none running and none open, unlike windows.

> 
Will we have to use McAfee or Norton for anti-virus protection?


No.

> 
[I explained to her that there are no viruses, malware... etc] Why is it that these unwanted applications do not affect Linux?


[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

Not mentioned in the article: perceived lack of users on gnu/linux systems, and general computer literacy with people who use gnu/linux.

> 
If Ubuntu is free of charge, how does it [Cannonical] earn revenue?


Cannonical doesn't *make* the vast majority of software on an ubuntu system, it does provide merchandice and technical support.  Much FLOSS software is created by volunteers and hobbyists.

---

### Post by QIII on 2009-06-28
It's "Canonical", BTW.

You can read up all you want here:

[http://www.canonical.com/](http://www.canonical.com/)

---

### Post by Groucho Marxist on 2009-06-29
> **QIII said:**
> It's "Canonical", BTW.

You can read up all you want here:

[http://www.canonical.com/](http://www.canonical.com/)


:) Yeah, I was under a time crunch and realized I misspelled it after I posted it (I was taking a break from remodeling a room). At any rate, thanks everyone for the help!

---

