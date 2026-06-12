---
title: "please help, Windows XP too slow turning off"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by oingk on 2010-01-10
:???:hi

I have a question more to do with Windows XP hope I don't make you angry, I asked in a "windows forum" already but no answer and besides you guys usually know better things even regarding windows. so hopefully someone here can help me.
So I didn't know which section I should write this, so I write it in the beginners talk.

I dual boot Windows XP and Ubuntu 9.10, with GRUB2 being the booter for both.

Windows is ok to sturt-up though it takes too long to shut down. Specifically it takes about 1 and a half minutes, this may not sound terrible but it can become quite annoying.

I have already tried these:
-Disbaled all unnecessary services and startup programs.
-Did a "check disk" with auto-repairing enabled.
-Defragmented.
-Checked all drivers separately for updates.
 
My computer is new. I can't track where the problem started, but things I did include changes in my windows registry and as I said the installation of Ubuntu.

Please if anyone can help me I will really appreciate it, or refer me somewhere to start looking, or at least let me know a place I can address this problem and get decent help.

Thanks,
oingk

---

### Post by John Bean on 2010-01-10
When I read "things I did include changes in my windows registry" it immediately triggered alarm bells. You need to be a bit more specific about that bit.

In general though, have a look in the system log and check for error messages; it sounds to me like something is failing to respond to the shutdown signal and causing a timeout. In most earlier versions of Windows it would have just hung for ever waiting, but XP adopts a strategy of (eventually) killing non-responding processes resulting in a successful if lengthy shutdown sequence.

PS: using a single fixed-size ("permanent") swap (paging) file significantly improves the shutdown speed. Just set the min/max size to be the same - typically 1.5 times RAM size - and make sure it's only enabled on one disk/partition if you have more than one.

---

### Post by sdowney717 on 2010-01-10
[http://www.ccleaner.com/](http://www.ccleaner.com/)

try running cc cleaner, it is free

---

### Post by oingk on 2010-01-10
thanks for replys.

-Changes I did to the "registry" include disabling one by one all services that seemed unnecessary, though I did this after careful consideration. I can't recall any other changes but I'm still trying to. Another thing I did though that gave me a strange response was that at one point I got the mania to remove Windows Media Player 10 and the more it wouldn;t remove the more I fighted back, so when I eventually managed to delete all its files, my laptop gave me a "blue screen" for some seconds, not long enough to read what it said. After that my computer showed no obvious dysfunction. I also tried to remove Windows Outlook with no success.

-Checking the Event Viewer, that seems to include events from the beginning of the laptop purchase, I see the following "errors":
[COLOR=DarkRed]1)[/COLOR] "Hanging application rundll32.exe BLAH BLAH".
[COLOR=DarkRed]2)[/COLOR] "Hanging application msmsgr.exe BLAH BLAH".
[COLOR=DarkRed]3) [/COLOR]"Microsoft .NET framework 1.1 - Update BLAH BLAH could not be installed."
[COLOR=DarkRed]4)[/COLOR] "The description of Event ID (5000) in Source (NativeWrapper) cannot be found. The local computer may not have the necessary registry informaion or message DLL files to display messages from a remote computer".
[COLOR=DarkRed]5)[/COLOR] Unable to update the performance counter strings of the 009 language ID. The Win32 status returned by thecall is the first DWORD in Data section". Source: LoadPerf.
[COLOR=DarkRed]6)[/COLOR] Instaling the performance counter strings for service Outlook failed.
[COLOR=DarkRed]7)[/COLOR] Hanging application OUTLOOK.EXE BLAH BLAH module hangup".
Hanging applicatin RainBrowser.exe hang module hangup" (NOTE:Rainbrowser is a part of rainmeter just a program I use)
[COLOR=DarkRed]9)[/COLOR] "Rejected Safe Mode action: Microsoft Office Outlook"
[COLOR=DarkRed]10)[/COLOR] The engine file has been modified or destroyed! Source: Avira Antivir (NOTE: I just saw this, but my antivirus seems to be working ok).
[COLOR=DarkRed]11)[/COLOR]  Hanging application Firefox
[COLOR=DarkRed]12)[/COLOR] Hanging application Shockwave Installer_Slim.exe
[COLOR=DarkRed]13)[/COLOR] Some Lavasoft Ad-Aware error (this is an antimalware i use)


Another thing in the event viewer i that there are many "Warning" signs (besides the Error ones) that say:
"Windows saved user OINGK registry while an application or service was still using the registry during log off. The memory used by the user's registry has not been freed. The registry will be unloaded when it is no longer in use. This is often caused by services running as a user account, try configuring the services to run in either the LocalService or NetworkService account".



-I run regularly CCleaner, and also use antimalwares and antivirus.

sorry for my boring messages

---

### Post by oingk on 2010-01-10
> **John Bean said:**
> 

PS: using a single fixed-size ("permanent") swap (paging) file significantly improves the shutdown speed. Just set the min/max size to be the same - typically 1.5 times RAM size - and make sure it's only enabled on one disk/partition if you have more than one.

What does this mean exactly?

---

### Post by oingk on 2010-01-10
> **oingk said:**
> 
Another thing in the event viewer i that there are many "Warning" signs (besides the Error ones) that say:
"Windows saved user OINGK registry while an application or service was still using the registry during log off. The memory used by the user's registry has not been freed. The registry will be unloaded when it is no longer in use. This is often caused by services running as a user account, try configuring the services to run in either the LocalService or NetworkService account".




Actually I just noticed that this Warning comes up in the Event Viewer every time I shut down my computer, so it is probably related to my prolem huh?

---

### Post by oingk on 2010-01-10
I tried turning it of again now and checking the event things again.
I got the aformentioned Warning thing, and also this image I am attaching. Maybe it has something to do with the problem?

---

### Post by oingk on 2010-01-10
please help me :cry:

---

### Post by John Bean on 2010-01-11
> **oingk said:**
> -Changes I did to the "registry" include disabling one by one all services that seemed unnecessary, though I did this after careful consideration. I can't recall any other changes but I'm still trying to. Another thing I did though that gave me a strange response was that at one point I got the mania to remove Windows Media Player 10 and the more it wouldn;t remove the more I fighted back, so when I eventually managed to delete all its files, my laptop gave me a "blue screen" for some seconds, not long enough to read what it said. After that my computer showed no obvious dysfunction. I also tried to remove Windows Outlook with no success.

Then all bets are off. It's not certain but very high probability that your registry modifications have broken something important that's affecting the whole system. I won't even attempt to make a guess what is broken since I have no idea what the changes you made actually were.

> -Checking the Event Viewer, that seems to include events from the beginning of the laptop purchase, I see the following "errors":
[COLOR=DarkRed]1)[/COLOR] "Hanging application rundll32.exe BLAH BLAH".
[COLOR=DarkRed]2)[/COLOR] "Hanging application msmsgr.exe BLAH BLAH".
...
[COLOR=DarkRed]7)[/COLOR] Hanging application OUTLOOK.EXE BLAH BLAH module hangup".
[COLOR=DarkRed]...
11)[/COLOR]  Hanging application Firefox
[COLOR=DarkRed]12)[/COLOR] Hanging application Shockwave Installer_Slim.exe
[COLOR=DarkRed][/COLOR]
which will explain some of the delays.

I would seriously consider a reinstall... and avoid unnecessary registry meddling next time around ;-)

---

### Post by John Bean on 2010-01-11
> **oingk said:**
> What does this mean exactly?

In all honesty I don't think there's any point in elaborating given the (broken) state of your system; changing the location and size of the paging file is a pretty routine operation in XP and can be used to fine-tune performance in a correctly functioning system in many cases. If you don't know what it is then leave it alone, it will have no affect on your current problem.

---

### Post by SirBismuth on 2010-01-11
Eh, after reading this thread, the only thing I can think of is a complete & clean reinstall of XP.  I dare say that you have broken something in your registry.  Next time, make a backup before fiddling with it.

B

---

### Post by oingk on 2010-01-11
But I;ve spend so much time downloading programs I like and removing the ones I don't like and making Firefox the way I like it and changing Windows settings and themes etc.

Won't all these be lost if I do a clean install?

:(

---

### Post by Jackzor on 2010-01-11
You could put the windows xp disc in while the computer is running and try upgrading.

I've done it before. I had problems like this when I was 15 years old... Playing with stuff too often...  
Anyways. Try the upgrade. It should keep all of your programs.

---

### Post by yeats on 2010-01-11
Of course you *could* just make Ubuntu your main OS and reinstall Windows in VirtualBox.  Hey - you are asking on a Linux forum after all! ;-)

> But I;ve spend so much time downloading programs I like and removing the ones I don't like and making Firefox the way I like it and changing Windows settings and themes etc.

Won't all these be lost if I do a clean install?

Regarding Firefox, your profile folder is portable (you could even move it to Ubuntu if you want) and lives in C:\Documents and Settings\*[your username]*\Application Data\Mozilla\Firefox\Profiles and will be called *[some random string]*.default.  If you want that in Ubuntu, copy it to your Ubuntu partition, find out your current Firefox profile name, located in ~/.mozilla/firefox/ and will also be in the *[some random string]*.default format.  Rename your Windows profile to that name, rename your Ubuntu profile by add *.orig* or something to the end, move the Windows profile to ~/.mozilla/firefox and you'll start Firefox in what was your Windows profile.

---

### Post by Hello Kitty on 2010-01-11
Like chrissharp123 said, you can back up your Firefox profile, and maybe a few other things; but the rest will be lost if and when you reinstall Windows. You could always back up the setup files for the programs you've installed though.
 
 As others have done, I would recommend a fresh install of Windows and less fiddling with things that can damage the system. ;) It's hard removing a lot of the things that come with Windows, but there's really no need to remove them either, as you can just make other applications open files these applications open by default.

Sorry I couldn't be of more help, but too many things could have gone wrong for anyone to be able to help you (at least without access to your computer) in any other way.

---

### Post by sliketymo on 2010-01-11
You say that you disabled services using the windows registry.Why ? It is easier to manipulate the windows services functions using the "Manage Computer" utility located in Administrative tools.I would suggest a re-install,and a quick read at BlackViper.com for a pretty complete list,and explanation of windows services,and there functions.Good luck.

---

### Post by cascade9 on 2010-01-11
You _might_ be able to repair XP. You wil probably still lose soem settings, etc, but it saves a full reinstall. Directions here cause I'm to lazy to type it out, and copy/paste looks U-G-L-Y from that page

[http://www.michaelstevenstech.com/XPrepairinstall.htm](http://www.michaelstevenstech.com/XPrepairinstall.htm)

Scroll down to 'XP repair install' 

BTW, if you really want to remove unwanted junk form XP, use nLite. You'll have to reinstall though.

---

### Post by oingk on 2010-01-11
thanks for your replies.
they contain a lot of valuable information

I have a question before trying the XP reinstall (or the upgrade).

My laptop is a Thinkpad and provides a utility called Rescue and Recovery. This restores your operating system to a previous state.

In the event that I have damaged something in the registry of my windows, should this utility repair the damage?

---

### Post by warfacegod on 2010-01-11
> **oingk said:**
> thanks for your replies.
they contain a lot of valuable information

I have a question before trying the XP reinstall (or the upgrade).

My laptop is a Thinkpad and provides a utility called Rescue and Recovery. This restores your operating system to a previous state.

In the event that I have damaged something in the registry of my windows, should this utility repair the damage?

Unlikely. Before you do a new install, go here and see if you can get your services back to default.

[http://www.blackviper.com/](http://www.blackviper.com/)

There maybe other useful guides for you there as well.

---

### Post by oingk on 2010-02-24
I've tried everything and as most people suggest here a complete reinstall of Windows is necessary (I've even spend a lot of money talking to Lenovo technicians and they suggest the same thing). The reason I couldn't do the reinstall was that I was sold the computer without the install CDs. I've ordered installation CDs from Lenovo (they do this for free) but now I'm thinking of just installing Ubuntu and see how this goes for a while.  I'm just writing this in case someone has a similar problem, to let them know they should probably reinstall Windows.  Ok thanks for all of your help.

---

