---
title: "Fail Starting ISC DHCP IPv4 Server"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by MyDell1501 on 2014-02-04
Hello!

As seems to be quite common, I am brand-new to Linux and Ubuntu and have a question. (Yes, I am one of the Windows users who has the Wndows mentality, and I'm really trying to learn how to get rid of it!).

I just installed Ubuntu the other day, then I installed the Firestarter firewall, and Comodo Anti-Virus.  Thanks to this forum was able to get my wireless driver installed on my Inspiron 1501.  Initially I had to connect to the internet using my ethernet cable, but now my wireless works perfectly.  Last night I was checking to make sure my firewall and anti-virus were really installed and running, and I tried to run a Comodo scan last night.  Shortly after the scan started, I got a black screen with lots of stuff written on it, and I noticed one thing that said:

Fail *Starting ISC DHCP IPv4 Server.  

I tried again this morning and got the same error.  I'm wondering if this is because in my Firestarter firewall I only had the option of one internet connection type, and it was set as default to the ethernet, and I chose wireless, since that is how I will always be connecting to the internet.  

Is there something I can do to fix this, or do I need to remove something?  I am good at following directions, so if anyone can tell me what to do, step by step, I should be able to follow along and fix the errors.

I hope this all made sense and I am hoping someone will be able to help me.  Thank you in advance to everyone for reading this and your assistance!!

---

### Post by SeijiSensei on 2014-02-04
Are you intending to use this machine as a DHCP server for a local network?  Why do you need to run dhcpd?

You say you will be connecting wirelessly to the Internet.  The router to which you connect already has a DHCP server that gives an address to wlan0, the wifi interface.  Are you intending to connect a local network to the machine's Ethernet port?  Why not just connect the network to the LAN side of the router?

If you tell us what you're trying to accomplish, it will be easier to help.

---

### Post by MyDell1501 on 2014-02-04
Thanks for your quick response.  No, I do not intend to use the machine as a DHCP server.  I honestly didn't even know what that was (until I did a google search), so forgive my ignorance!  Sorry!

Hopefully I can clarify what I am trying to do.  I will be connecting my laptop wirelessly to the Internet.  I don't want to connect using an ethernet cable, I'm not connecting any other computers or anything like that.  I just want to connect my laptop using wifi.  I'm just your average person using the internet for typical things...nothing fancy.

What I am trying to do is install a firewall and an anti-virus, just to make sure I keep everything safe.  I know there are varying opinions on whether or not firewalls and anti-virus are really needed, but I'm on the paranoid side and would prefer to have the extra security measures in place.  I have installed the Firestarter Firewall and Comodo Anti-Virus for Linux, and when I try to run the Comodo Anti-Virus scan, that's when the problem arises.  I am wondering if I have some setting configured incorrectly, based upon your response to my initial message. 

Hopefully that gives you a better understanding of what I'm trying to accomplish.   Again, any additional assistance you can provide is sincerely appreciated.  Thank you for your help!

---

### Post by MyDell1501 on 2014-02-04
I'm not sure if this helps or not.  When I try to do a scan with the anti-virus, after a minute or so, the computer freezes up and there's a bunch of text on the page.  I was able to write down part of the code that comes up on the screen when the computer freezes up.  It says:

12161.903937 ---------------------cut here------------------------------------
12161.904051 kernel BUG at /build/buildd/linux-3.2.0/fs/dcache.c:474!
12161.904170 invalid opcode: 0000 [#1]SMP

and then there's a whole long list of modules.  I'm not sure if this information is helpful, but I thought it might be.  I'm going to look around the forum and see if I can find anything that talks about a kernel BUG, to see if that is what the problem is, and to see if I can find the way to fix it.  

Any thoughts, input, etc. is greatly appreciated.  

Thanks again!!!

---

### Post by brokenhachi on 2014-02-04
Seems like an issue with comodo: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/952398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/952398) 
[http://forums.comodo.com/comodo-antivirus-for-linux-cavl/problem-comodo-antivirus-for-linux-cavl-v112680251-t95837.0.html](http://forums.comodo.com/comodo-antivirus-for-linux-cavl/problem-comodo-antivirus-for-linux-cavl-v112680251-t95837.0.html)

Can you try upgrading the kernel? *sudo apt-get update && sudo apt-get dist-upgrade*, then reboot and try again?

---

### Post by MyDell1501 on 2014-02-04
I was wondering if it was an issue with Comodo as well.  I did a little looking around, and others have had a similar issue.  I will upgrade the kernel and reboot.  I have a few things to do and won't be able to continue working on this for about 2 hours, but I will report back as soon as it's done.  Thank you so very much for your response.  I'll post with my results as soon as I have them.

---

### Post by MyDell1501 on 2014-02-05
Ok, I'm back.  I did the upgrade as you suggested - thank you for writing the exact directions on what to type in!! - and then I tried to run the anti-virus scan and the system still crashed.  I am going to un-install Comodo Anti-Virus and try installing ClamAV since that seems to be the most popular.  I'll run the scan with Clam and report back.  Thanks again!!!

---

### Post by MyDell1501 on 2014-02-05
I just installed ClamAV and did a scan, and it worked fine.  But, I think I might prefer using AVG Anti-virus since I'm more familiar with it, so tomorrow I may un-install Clam and try installing AVG.  But it seems that the computer crashing has stopped, so I guess it did have something to do with Comodo.  Thank you so much for your help!

---

### Post by SeijiSensei on 2014-02-05
Remember that scanning with an antivirus program only makes sense if you have a Windows partition on the machine.  There are few pure-Linux viruses and most are just proofs-of-concept.  I guess AV might detect browser attacks that leave little javascript bits behind, but I've only ever had that problem once, when the NY Times site sent me a copy of the Antivirus 2010 script.  When the script showed me a window claiming I had infected DLLs on a pure-LInux system, I laughed out loud.

---

### Post by MyDell1501 on 2014-02-05
Oh, I did not realize that!  Being new to Ubuntu and Linux, I find I have a LOT to learn!  Too funny about the Times sending you a copy and getting a virus notification!!  I'm sure that's a story that doesn't get old!  

So, is there any anti-virus that I should run, or is it really unnecessary?  And, if you don't mind me asking, what about a firewall?  I'm so used to the Windows mentality of having to keep your system secured and guarding it with your life, that I feel like not having a firewall and anti-virus is like leaving the front door to my house wide open with a bucket of cash sitting on the table!!

Thanks again for your response.  

And, do you think I should mark this thread as Solved?  I'm not sure if technically it is solved, but since I removed the problem application, I havent had any other issues.

Thanks!!

---

### Post by brokenhachi on 2014-02-05
No please don't mark it as solved, since we haven't reached a solution! If you will just uninstall comodo then maybe we dont need to continue this but at least it will not show in google as solved!

Also, to add on to SeijiSensei's post.. yes it is true that there are few linux malware, but they are not non-existant.. meaning that there are some. The main concern for me is that linux will become a carrier. Think of the rats carrying the bubonic plague, or mosquitoes carrying malaria! i.e. the linux system carries some malware which propagates across the network but does not infect the linux machine and infects windows machines. Please consider this. If you want an open-source alternative, please look at CLAMAV for virus scanning on Linux (it is in the repo so you can apt-get install) [http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/).

---

### Post by SeijiSensei on 2014-02-05
Frankly I don't see that scenario as very likely unless the Linux machine is acting as a file store for Windows machines.  Scanning network shares that Windows users can access makes good sense, though.

MyDell, I recommend the [security articles at the Ubuntu wiki]("https://help.ubuntu.com/community/Security") as a starting point. There are discussions covering firewalls, antivirus, and other security concerns.

---

### Post by MyDell1501 on 2014-02-06
Thank you both for your responses.  I will definitely not mark this as solved.  I did uninstall Comodo and I installed ClamAV (thanks so much for providing the link!).  I certainly feel better knowing there is some form of anti-virus on my computer.  

I did look at the Ubuntu wiki site, but in all honesty, a lot of what is written there is well beyond my knowledge and understanding, so it's going to take me a while of reading it to understand fully what I actually need to do.  I will keep at it, though, because it is important.

Thank you both for your assistance!  It is very much appreciated!

---

