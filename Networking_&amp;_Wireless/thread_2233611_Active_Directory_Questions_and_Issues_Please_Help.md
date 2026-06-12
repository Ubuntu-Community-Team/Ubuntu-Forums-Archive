---
title: "Active Directory Questions and Issues Please Help"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by juliemprokes on 2014-07-09
Let me start off by saying that I have done quiet a bit of searching and was able to figure out a few things on my own but other still allude me. I am using ubuntu 14.04 and have the pbis software installed and configured the computer is able to access the domains users and allow them to log on but I am having issues with administrative rights for domain admins. When ever a domain admin attemps to run the sudo command from the terminal they get an error saying "User is not in the sudoers file. This incident will be reported." In addition to that when the computer asks a user to authenicate administrative rights before opening software like Synaptic Package Manager it only allows authenication with local admins not domain admin accounts. I have put some info below but if you need me to pull info from any other files or do anything else please let me know.

Our domain is INT.putstuffhere.com

Following the instructions from other posts I found online I made the changes to the files listed below:

[INDENT]/etc/sudoers 
[/INDENT]
[INDENT=2]Added
[/INDENT]
[INDENT=2]%INT\\domain^admins ALL=(ALL) ALL
[/INDENT]
[INDENT=2]%domain^admins ALL=(ALL) ALL
[/INDENT]

[INDENT]/etc/pam.d/common-session[/INDENT]
[INDENT=2]Changed
[/INDENT]
[INDENT=2]session sufficient pam_lsass.so
[/INDENT]
[INDENT=2]To
[/INDENT]
[INDENT=2]session [success=ok default=ignore] pam_lsass.so
[/INDENT]

---

### Post by slooksterpsv on 2014-07-10
Try some of these ones:

[http://ubuntuforums.org/showthread.php?t=867774](http://ubuntuforums.org/showthread.php?t=867774)

They used:
%DOMAIN\\domain^admins ALL=(ALL) ALL

Notice the all caps %DOMAIN

They also mention changing winbind so you don't have to prefix the domain.

---

