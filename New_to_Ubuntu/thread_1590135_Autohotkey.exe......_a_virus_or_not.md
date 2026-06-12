---
title: "Autohotkey.exe...... a virus or not?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Greg Mueller on 2010-10-07
I have avast for Linux and every time I run it, it identifies autohotkey.exe as a virus. Is it a known virus or is this a false virus identification? I don't use it and so I delete it, but it keeps reappearing in the next scan. Is it because of the ubuntu updates I do almost every morning?

:confused:

---

### Post by gandaran on 2010-10-07
> **Greg Mueller said:**
> I have avast for Linux and every time I run it, it identifies autohotkey.exe as a virus. Is it a known virus or is this a false virus identification? I don't use it and so I delete it, but it keeps reappearing in the next scan. Is it because of the ubuntu updates I do almost every morning?

:confused:
where do you find this autohotkey.exe file? pen drive, wine drive or where?

---

### Post by Greg Mueller on 2010-10-07
It's a pretty long string but it starts out with 

/USR/SHARE/WINE-DOORS/BASE.REPO/AUTOHOTKEY-1.04.46-08/

and winds up with AUTOHOTEKEY.EXE

I've looked with the file manager but I can't find anything (at least it does not show anything) past AUTOHOTKEY-1.04.46-08

I have avast move it to a folder where it renames it adding a "vir" suffix to the file name. I can delete it there (with the file manager) but not with avast, where it says it is located (which I can't see when I look).

Can I un-install the whole autohokey program (since I don't use it anyway)?

---

### Post by Locke_99GS on 2010-10-07
It is a Windows application that is used to automate the interface. You installed it via wine-doors for some reason. The application is opensource and has legitimate uses, though I can easily imagine a virus or other type of malware using it (or something that functions similarly) to steal or wreak havoc.

Just uninstall it via wine-doors if the AV message bothers you.

---

### Post by gandaran on 2010-10-07
> **Greg Mueller said:**
> It's a pretty long string but it starts out with 

/USR/SHARE/WINE-DOORS/BASE.REPO/AUTOHOTKEY-1.04.46-08/

and winds up with AUTOHOTEKEY.EXE

I've looked with the file manager but I can't find anything (at least it does not show anything) past AUTOHOTKEY-1.04.46-08

I have avast move it to a folder where it renames it adding a "vir" suffix to the file name. I can delete it there (with the file manager) but not with avast, where it says it is located (which I can't see when I look).

Can I un-install the whole autohokey program (since I don't use it anyway)?
can you uninstall the autohotkey program? ins't it part of wine-doors?
well the AUTOHOTEKEY.EXE file is a microsoft windows system file but sometimes it can be a fake infected file (virus) maybe theres nothing wrong with this file if it belongs to the wine-doors installation, in this case it would be a false positive.
I would recommend uninstall the whole wine-doors application and install playonlinux instead which is much better the wine-doors, wine-doors is old! and is it still supported?

---

### Post by Greg Mueller on 2010-10-07
I uninstalled it via wine-doors and rebooted and now I scan clean.

I feel better now.
Thanks guys

---

### Post by Greg Mueller on 2010-10-10
Well I guess I didn't uninstall it. It's back.
So I uninstalled Wine and tried attacking it that way.
I will look into playonlinux, thanks

Is there a cleaner program that will go through and delete uninstalled program files and old bits?

---

### Post by Locke_99GS on 2010-10-10
I've heard BleachBit is supposed to be pretty decent at that sort of thing, though I've never used it.

apt-get autoremove, autoclean, and clean, and Ubuntu Tweak have always been good enough for *my* needs.

---

### Post by degarb on 2011-01-03
Autohotkey is arguably one reason not to use linux.  It is a basic like programming language and macro recorder.  You can compile exes that are distributable.  Like ftp.exe, some antivirus programs flag autohotkey and compiled scripts--erroneously--as viruses or keyloggers.  But many freeware programs are increasingly written in ahk (autohotkey), like magicblock.

I guess the language is too easy and too powerful, so must be a viral.  You will scan with differing versions of Avast, I bet the latest will not flag it. Take any 14 and 3 or 4 will flag. and if upx packed, at least 5.

BTW. no av can actually see signatures, as most exes are compressed and encypted.  Furthermore, they have no idea what routines the programmer is doing. You are best off having a good firewall, application firewall, secure browser, windows updater turned on.  Commercial AV is largely a scam to get your $60 a year, and ineffective at best for above reason, also seldom is anything they scan for, actually in the wild. They all do certainly slowdown the system. I have got barely used 2 gighz systems for free because they cannot run the modern resident scanners without totally bogging down.

---

### Post by degarb on 2011-01-03
More than likely the reason the autohotkey.exe is reappearing is some other exe of this language on which you are relying on and running, is extracting the autohotkey.exe .  Now, ahk scripts can be fed to the autohotkey.exe via the commandline,  which allows a ton more power and to spawn paralleling processes, since ahk cannot multithread.  Kinda like the power of the python engine in only 200k. This also allows an end user to have an open source program, that they can inspect and modify.

i recommend not going to AV people who are clueless and goto autohotkey.com and post the exe in their forum.  They could tell you if it is the real thing and what version it is.

---

### Post by tgm4883 on 2011-01-03
> **degarb said:**
> Autohotkey is arguably one reason not to use linux.  It is a basic like programming language and macro recorder.  You can compile exes that are distributable.  Like ftp.exe, some antivirus programs flag autohotkey and compiled scripts--erroneously--as viruses or keyloggers.  But many freeware programs are increasingly written in ahk (autohotkey), like magicblock.

I guess the language is too easy and too powerful, so must be a viral.  You will scan with differing versions of Avast, I bet the latest will not flag it. Take any 14 and 3 or 4 will flag. and if upx packed, at least 5.

**BTW. no av can actually see signatures, as most exes are compressed and encypted.  Furthermore, they have no idea what routines the programmer is doing. You are best off having a good firewall, application firewall, secure browser, windows updater turned on.  Commercial AV is largely a scam to get your $60 a year, and ineffective at best for above reason, also seldom is anything they scan for, actually in the wild. They all do certainly slowdown the system. I have got barely used 2 gighz systems for free because they cannot run the modern resident scanners without totally bogging down.**

Please do not post about what you do not know about.

---

### Post by degarb on 2011-01-03
[http://www.autohotkey.com/forum/topic31975.html](http://www.autohotkey.com/forum/topic31975.html)

You will see here some others with same issue.  Compile hello world and get false positives.
  I found using latest avast to cure one false positive with tag.exe which is said to be a threat because it modified other files.  It is very powerful dos commandline mp3 tagger!

---

### Post by bodhi.zazen on 2011-01-03
> **degarb said:**
> [http://www.autohotkey.com/forum/topic31975.html](http://www.autohotkey.com/forum/topic31975.html)

You will see here some others with same issue.  Compile hello world and get false positives.
  I found using latest avast to cure one false positive with tag.exe which is said to be a threat because it modified other files.  It is very powerful dos commandline mp3 tagger!

These things (AV detection) are tools, you need to understand how to use them.

First you start by scanning your system from a fresh install, you need a "known good" baseline.

Second you need to know what is "normal" for your usage on your computer. Obviously it goes without saying normal activity on your OS may be abnormal on mine.

Third you need to understand how these tools work. They are based on rules. If foo.exe can modify other files it might be a problem and an alert will be generated. It is then up to you to determine if this is a problem or not. If not it is a false positive. You need to understand that these tools will always err on the side of false positives as false negatives (missing an "infected" file) is by far more unacceptable then a false positive.

Last you need to understand that running these tools on linux is an exercise in false positives as there are no known active viruses for Linux (you system was patched long ago to the known viruses) and these tools can not protect you against zero day exploits.

Thus the tool is functioning normally and PEBKC in that you are not understanding the tool, it's use, and it's limits.

---

