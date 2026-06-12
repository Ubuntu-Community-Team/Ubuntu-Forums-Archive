---
title: "windows nt computer browser service"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by neorou on 2007-08-30
Hi guys,
I hope this is the right forum to post this question on.

I am seriously considering moving to using Ubuntu Linux as my main workstation at work. I've been using the Mac OS's for a decade and a half and use windows from time to time. 
I am certainly not a Windows expert and nowhere near being a linux expert. 

So, here's my question to those of you who have played on Windows networks for years and have had similar or working experience on this subject with linux.

My workplace currently uses a mix of Active Directory and the old NT domain for authentication. Every time some new person comes in with their Windows PCs, they always leave the 'computer browser' service turned on.
This Windows service messes with the NT domain server apparently. Anyway, is there something in Feisty or Dapper that would do the same thing? In other words, is there a daemon in Ubuntu linux that is turned on by default that would interfere with the NT domain? Is there or are there any daemons that may interfere with it that is not turned on by default?

I will use my ubuntu machine to do LAMP and LAPP (Postgresql) development & testing, as well as some basic video and audio editing, maybe some very basic software development using python and C/C++.

Any advice on this subject is greatly appreciated. Thanks in advance...

---

### Post by neorou on 2007-09-02
I asked people outside this forum, and apparently the quick answer is SAMBA. I haven't tested it out, because I didn't want to mess up our institute's domain controller :)
So, I'll just post the information that I got for now. If anybody else is even reading this post and wants to comment - please do. I would like to be corrected and be directed in the right direction (and, Thanks, in advance).

If you want to set-up a linux system inside a mix network where an NT domain browser exists, you will need to lower your browser priorities. In other words, in the samba configuration file, you need to select items like 

OS Level (determines the precedence of this server in master browser elections). 
The default value is 33 (higher than that of NT boxes, which are set to 32, I think). Setting it at a lower level would set the NT box to be of a higher value.

Domain Master specifies Samba to be the Domain Master Browser. You want to set this to 'No', otherwise you will make your linux machine compete with the local NT browser.

Preferred Master causes Samba to force a local browser election on startup and gives it a slightly higher chance of winning the election.
You want to set this to 'No'.

You want to set the domain logon as 'No'. This will not allow Win95 (etc.) computers to log on to your machine.

---

