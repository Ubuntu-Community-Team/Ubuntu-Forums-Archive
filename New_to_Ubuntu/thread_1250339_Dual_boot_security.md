---
title: "Dual boot security"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Wehrdo on 2009-08-26
The more and more I read about Linux, the more and more I am leaning towards it.  I've already installed ubuntu on my dad's office machine, but it's not hooked to the internet.  

My computer currently has Windows XP, and there's only one thing holding me back from putting Ubuntu on a partition and using it as my main operating system.  I know that Windows viruses will not harm a Linux computer, but since I'll also have XP on the same hard drive, could a virus get on my hard drive, and when I boot up Windows, execute and destroy my computer?  I would prefer not running any virus protection, because it's such a system hog, but I don't want my computer to catch a virus.

Also, will there be some sort of boot manager when I start my computer?  I currently have the Windows 7 RC, and it starts a "Windows Boot Manager".  I would put Ubuntu on the Windows 7 partition, so would there be some sort of boot manager, or would I have to manually set it up in the BIOS?

Semi-related question
---------------
I've seen the article where somebody ran Windows viruses on WINE, and they copied themselves all over the system.  Could something like that accidentally happen if I installed WINE to run Windows programs, or would I actually have to specifically tell it to run before it would?

---

### Post by aysiu on 2009-08-26
I think if you lock down XP, you shouldn't have an issue:
[The 6 Best Ways to Secure Windows](http://www.psychocats.net/ubuntucat/windowssecurity/)

Antivirus doesn't figure into the picture, so don't worry.

---

### Post by achase79 on 2009-08-26
Ubuntu uses grub as its boot manager.  It usually sets up everything automatically upon install.

---

### Post by aysiu on 2009-08-26
> **Wehrdo said:**
> 
Semi-related question
---------------
I've seen the article where somebody ran Windows viruses on WINE, and they copied themselves all over the system.  Could something like that accidentally happen if I installed WINE to run Windows programs, or would I actually have to specifically tell it to run before it would? If you are planning to run viruses, I would suggest you do so in a virtualized environment (Windows in VirtualBox, in Wine in Ubuntu in VirtualBox) instead of on a production/entertainment installation of either Windows or Ubuntu.

If you have a program you want to run in Wine, and you're worried it has a virus in it, just ask around here. I'm sure we can tell you whether it's dangerous to run or not.

(Really, though, the chances of a Windows executable file for a program being designed to infest a Linux installation via Wine are pretty low.)

---

### Post by Wehrdo on 2009-08-26
> **aysiu said:**
> If you are planning to run viruses, I would suggest you do so in a virtualized environment (Windows in VirtualBox, in Wine in Ubuntu in VirtualBox) instead of on a production/entertainment installation of either Windows or Ubuntu.
 
If you have a program you want to run in Wine, and you're worried it has a virus in it, just ask around here. I'm sure we can tell you whether it's dangerous to run or not.
 
(Really, though, the chances of a Windows executable file for a program being designed to infest a Linux installation via Wine are pretty low.)
Sorry if I wasn't clear.  I don't plan on running viruses in Wine.  I was wondering if a virus could automatically run itself if wine was open at the same time?
 
[quote=aysiu]
**Re: Dual boot security**
I think if you lock down XP, you shouldn't have an issue:
[[COLOR=#000000]The 6 Best Ways to Secure Windows[/COLOR]]("http://www.psychocats.net/ubuntucat/windowssecurity/")

Antivirus doesn't figure into the picture, so don't worry. [/quote]
Here's what I meant: Say somehow a Windows virus gets on my computer while I was running Ubuntu.  I know that it won't do anything to my computer at the moment, besides just sit there.  Now say I start up Windows.  It's on the same computer.  Would the virus automatically run itself now that Windows is running, or since it being on a different partition, not make a difference?

---

### Post by aysiu on 2009-08-26
> **Wehrdo said:**
> Sorry if I wasn't clear.  I don't plan on running viruses in Wine.  I was wondering if a virus could automatically run itself if wine was open at the same time? You would have to run the program in Wine.

Wine isn't open or closed. It is a tool to run programs. If you use that tool to run a malicious program *designed to be run in Wine*, then it could destroy all your user data (and anything else you have access to).

But...

1. If you are in doubt as to whether a program is malicious or not, check it out with the forum first.

2. The likelihood of a Windows program designed to be malicious in Wine (and not in Windows) is pretty low at this point.

3. You have to *choose* to run a program in Wine. It is not a background process running all the time looking to automatically execute .exe files.

---

### Post by Wehrdo on 2009-08-26
> **aysiu said:**
> You would have to run the program in Wine.

Wine isn't open or closed. It is a tool to run programs. If you use that tool to run a malicious program *designed to be run in Wine*, then it could destroy all your user data (and anything else you have access to).

But...

1. If you are in doubt as to whether a program is malicious or not, check it out with the forum first.

2. The likelihood of a Windows program designed to be malicious in Wine (and not in Windows) is pretty low at this point.

3. You have to *choose* to run a program in Wine. It is not a background process running all the time looking to automatically execute .exe files.
Thanks, now the only question I have before I switch is if my ubuntu operating system somehow gets a windows virus put on it, then I boot windows, will the virus run and destroy my computer?  Or will a windows virus not even put itself on a ubuntu machine?

---

### Post by earthpigg on 2009-08-26
> **Wehrdo said:**
> Thanks, now the only question I have before I switch is if my ubuntu operating system somehow gets a windows virus put on it, then I boot windows, will the virus run and destroy my computer?  Or will a windows virus not even put itself on a ubuntu machine?

a windows virus contained in Microsoft Word .doc file someone e-mails you cannot infect your computer (unless you open it in MS Word inside of WINE) -- but you *can* pass it onto others if you subsequently e-mail that file to someone else.

you could also copy that file to your windows partition *or* otherwise open/access that .doc file in windows and *then* windows can get infected.

in short: a file with windows malware can be transfered onto or off of Ubuntu, but cannot directly infect Ubuntu or Windows itself when accessed in Ubuntu.

however - and aysiu's comments above got me thinking of this - a file containing windows malware opened in WINE on a dual boot computer ***specifically designed to execute on dual boot windows/ubuntu machines when opened in WINE inside of ubuntu***? i would imagine that yes, that could indeed theoretically attack your windows partition - unless you change your permissions so only root can access that partition from within Ubuntu.


the safest way to run Windows software in Ubuntu is probably to use VirtualBox.

how much RAM do you have, and what Windows software do you anticipate using?

---

### Post by Wehrdo on 2009-08-27
> **earthpigg said:**
> a windows virus contained in Microsoft Word .doc file someone e-mails you cannot infect your computer (unless you open it in MS Word inside of WINE) -- but you *can* pass it onto others if you subsequently e-mail that file to someone else.

you could also copy that file to your windows partition *or* otherwise open/access that .doc file in windows and *then* windows can get infected.

in short: a file with windows malware can be transfered onto or off of Ubuntu, but cannot directly infect Ubuntu or Windows itself when accessed in Ubuntu.

however - and aysiu's comments above got me thinking of this - a file containing windows malware opened in WINE on a dual boot computer ***specifically designed to execute on dual boot windows/ubuntu machines when opened in WINE inside of ubuntu***? i would imagine that yes, that could indeed theoretically attack your windows partition - unless you change your permissions so only root can access that partition from within Ubuntu.


the safest way to run Windows software in Ubuntu is probably to use VirtualBox.

how much RAM do you have, and what Windows software do you anticipate using?
Wine isn't my main concern, I just thought it would be nice in case I run across a Windows only program that I would like to use.  My main concern is accidentally getting a Windows virus on my ubuntu partition, then when I start Windows, will the virus take hold?  Or does a virus actually have to be specifically told to run, such as opening a file or starting a program?  If it just sits there, can it harm my computer?

I've heard that filesharing with a Windows computer, you'll need antivirus so the virus doesn't get onto your Windows machine, but does the same apply for a dual boot installation?

---

### Post by JohnRove on 2009-08-28
> **Wehrdo said:**
> Wine isn't my main concern, I just thought it would be nice in case I run across a Windows only program that I would like to use.  My main concern is accidentally getting a Windows virus on my ubuntu partition, then when I start Windows, will the virus take hold?  Or does a virus actually have to be specifically told to run, such as opening a file or starting a program?  If it just sits there, can it harm my computer?

I've heard that filesharing with a Windows computer, you'll need antivirus so the virus doesn't get onto your Windows machine, but does the same apply for a dual boot installation?


If I understand your question correctly, you are worried about getting a windows virus on your ubuntu partition and then it booting when you start windows.  If that is the case, then my understanding is that no, it is not an issue.  For example, on my dual boot system, Windows does not recognize the ubuntu partition and as such cannot execute files stored on it.  I hope that this helps, and if I am wrong that someone with more experience will correct me.

---

### Post by Wehrdo on 2009-08-28
> **JohnRove said:**
> If I understand your question correctly, you are worried about getting a windows virus on your ubuntu partition and then it booting when you start windows. If that is the case, then my understanding is that no, it is not an issue. For example, on my dual boot system, Windows does not recognize the ubuntu partition and as such cannot execute files stored on it. I hope that this helps, and if I am wrong that someone with more experience will correct me.
 Thank you! That is exactly what I was wanting.  I guess I'm ready to put ubuntu on my computer now, as soon as I'm done testing Windows 7.

---

### Post by 3rdalbum on 2009-08-28
Viruses are not magical, they are just computer programs. Like any computer programs, they need to be downloaded run first before they can do anything. Most of the ways that viruses get forced onto Windows computers simply aren't applicable in the Linux world; those that are, will not be able to reach Wine through osmosis. They will need to be run in Wine.

And viruses that you download on Ubuntu will not reach the Windows partition through osmosis either; you would literally need to place the Windows virus somewhere on your Windows partition where it will be executed on startup.

---

### Post by presence1960 on 2009-08-28
[a good security guide]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Wehrdo on 2009-08-30
> **3rdalbum said:**
> Viruses are not magical, they are just computer programs. Like any computer programs, they need to be downloaded run first before they can do anything. Most of the ways that viruses get forced onto Windows computers simply aren't applicable in the Linux world; those that are, will not be able to reach Wine through osmosis. They will need to be run in Wine.

And viruses that you download on Ubuntu will not reach the Windows partition through osmosis either; you would literally need to place the Windows virus somewhere on your Windows partition where it will be executed on startup.
Thank you.  I thought that viruses could automatically run themselves.  As long as I take precautions while browsing the web, reviewing programs before I download them, and using WOT add-on for Firefox(I love WOT) I should be safe without running antivirus.  Thank you again.

---

