---
title: "Beginner's questions about security and hibernation"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by joeman225 on 2010-04-30
Hi Everyone,

I just started using Linux ubuntu and had a few questions.

1) I recently installed ClamTk Virus scanner, and was wondering, does it provide active protection against viruses/malware? Can it prevent infections?
(I know there aren't many viruses and malicious items out there for linux, but I'd like to have proactive preventative protection just in case)

2) Is there a program I can get from the official ubuntu software center that provides this kind of protection?

3)I also recently installed the gufw firewall and was wondering - under preferences ---> log  options, what does it mean to have your set level at "Full" vs. "Low"

4) When I attempt to hibernate my computer, the system does not actually hibernate, it simply asks for my password to log in again, is there anyway to fix it so I can hibernate?


Any help would be much appreciated! (Please be thorough in your responses :))

---

### Post by ScottinSoCal on 2010-04-30
> **joeman225 said:**
> 1) I recently installed ClamTk Virus scanner, and was wondering, does it provide active protection against viruses/malware? Can it prevent infections?
(I know there aren't many viruses and malicious items out there for linux, but I'd like to have proactive preventative protection just in case)

Sorry, never heard of it. And, being a complete, almost nonfunctional professional paranoid, I don't run AV software on either my work or home computers, both running Ubuntu. I've been running this way at home for a long while, and running this way at work for several months. No issues.

What's keeping me climbing the curtains these days is an upgrade to 10.04 while running ADS on Likewise-open.

> 2) Is there a program I can get from the official ubuntu software center that provides this kind of protection?

Not that I ever stumbled across.

> 3)I also recently installed the gufw firewall and was wondering - under preferences ---> log  options, what does it mean to have your set level at "Full" vs. "Low"

Full firewall logging is painful. Don't do it. You'll either fill up your hard drive with log files or, if the developer was smart, relegate yourself to having the last day or so available at any given time, with earlier entries deleted because the log file exceeded the size limit.

> 4) When I attempt to hibernate my computer, the system does not actually hibernate, it simply asks for my password to log in again, is there anyway to fix it so I can hibernate?

Hibernate? Or suspend? Two different activities. Is this a notebook computer, or a desktop?

---

### Post by cogier on 2010-04-30
As I understand it there are about 30 viruses out there for Linux. Most are VERY old, just created to prove a point and are now out of date and therefore of little danger.

Nothing is for certain but I have had no virus protection for years and have not come unstuck yet!

Regarding hibernation you will see that there are loads people that have issues with this. If it does not work for you don't use it. I have a Dell 1330 laptop that I swapped the 160GB hard drive for a 40Gb Solid State drive and using Ubuntu 10.04 it boots in 22 seconds to a usable desktop.

You are more likely to pick up a Windows virus that can't do your Ubuntu system any harm but you could pass it on to your Windows using friends.

---

### Post by lockalidiot on 2010-04-30
1. Never heard of ClamTK.

2. ClamAV from software center. read more from there:
[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)
But as everyone says, you don't really need it. It will be just waste of HD space.

3. I don't use it, so I don't know.

---

### Post by oldos2er on 2010-04-30
> **joeman225 said:**
> Any help would be much appreciated! 

You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by joeman225 on 2010-04-30
Thanks for all the responses.

> **ScottinSoCal said:**
> 


Hibernate? Or suspend? Two different activities. Is this a notebook computer, or a desktop?


I have a noteboook computer. And I definitely am looking to hibernate, not suspend. I'd like to shut off the computer completely, but have my session saved for the next time I boot up - similar to the hibernate function in Windows. Any ideas on how I can get the hibernate function to work properly?


@lockalidiot - Clamtk virus scanner can be downloaded from the Ubuntu software centre.  It says - ClamTk is a GUI front end for ClamAV using perl-Gtk2 (I have  no idea what that means.  

Is it true that pretty much anything from the Ubuntu software centre (at  the bottom of the applications menu) is safe to download?

---

