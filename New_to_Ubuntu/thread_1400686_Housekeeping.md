---
title: "Housekeeping"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by BobJam on 2010-02-07
When I used to use Windows, there was a routine I went through for housekeeping which was primarily to  delete temp files, defrag, and to remove multiple restore points (there were a few other things I did, but I can't remember).

This was particularly helpfull when my machine slowed down.  Most of the time, this "housekeeping" would improve performance . . . and if performance was so bad, a complete and fresh reinstall always made things better then.

Lately, my Ubuntu has been slowing down.  Let me be specific about the meaning of "slowing down".  Sometimes screen redraws are noticeably painted.  And sometimes, response times are just a few seconds off.

None of this is a showstopper or an indication that I think anything is terribly wrong.  More bothersome than anything.

I have 4GB of RAM, so a shortage of RAM shouldn't be the problem.

My understanding is that Ubuntu doesn't suffer from fragmented files like Windows did, so fragmentation shouldn't be an issue.

I have more than double the same allocation of free space in my / and /home partitions.  (For example, my / consumes 10GB of space, and the / partition still has 30GB of unused space.)  Swap file is 9.5GB.

I see there is a "Computer janitor" selection, but I'm wary of removing anything for fear of screwing something else up.  I mean I've seen this Computer janitor list a lot of lib files, but I'm afraid of messing up some dependency of an active program.

Are the lib files listed by Computer janitor safe to remove?

So, what housekeeping efforts should I take?

I realize "housekeeping" may not necessarily remedy my slight "slow down" issues (as I said, they are not dealbreakers and maybe I'll just have to live with the slight irritation).

But I've never done any housekeeping in the year+ that I've had Ubuntu (BTW, this is NOT a dual boot machine . . . it is completely Ubuntu) and it's probably about time I did some, "slow down" or not.

---

### Post by da burger on 2010-02-07
The programs computer janitor lists were installed as dependencies and are no longer needed (because the program they were installed with has been uninstalled) so I think they should be safe to remove.

---

### Post by 3rdalbum on 2010-02-07
> **da burger said:**
> The programs computer janitor lists were installed as dependencies and are no longer needed (because the program they were installed with has been uninstalled) so I think they should be safe to remove.

+1, but libraries sitting on your system will not slow it down.

If screen redraws are slow, check the output of the "top" and "iotop" commands - is there a program using a lot of your CPU time or I/O capacity?

---

### Post by OrangeCrate on 2010-02-07
** HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by jward3010 on 2010-02-07
Also if you want a full performance Ubuntu system, making sure proprietary drivers are installed can help. Go into System Menu > Admnistration > Hardware Drivers and see if there are any available to install.

Having a 10GB used root partition means you've either a lot of programs or you have a pile of different files sitting there (video's, pictures, music, documents etc.). If the first one is true (that it's all programs), well there's a good chance that a few them like to run in the background. Do you regularly install and uninstall programs?

---

### Post by Sir Jasper on 2010-02-07
Hi,

I suggest that if you do not have a clone or image just prior to any removal  using Computer Janitor then do not use it without further investigation or seeking more advice here.

My regards

PS I would also suggest saving a screen print so any/all deletions are known.

---

### Post by 311005901 on 2010-02-07
Hey BobJam.
Your problems might come from a few things:
[LIST=1]
[*]These slowdowns may be a program freezing up. Check 'System>Administration>System Monitor' and select the tab 'Processes' when your computer hangs. You might be able to simply end the program. Usually when my computer hangs, it's because I have Desktop Effects enabled. (Desktop Effects will be called "compiz" in System Monitor)
A program acting up will have close to 100% under the CPU column.
[*]You may actually have a problem with your hard drive. :( If you have an older computer, this might be the cause of the slowdowns. I can help you if you think this is the problem.
[/LIST]

---

### Post by ikt on 2010-02-07
> **BobJam said:**
> Lately, my Ubuntu has been slowing down.  Let me be specific about the meaning of "slowing down".  

It would be nice to know what internally is causing the slow down, I understand this is not something you can look into with windows rot but with ubuntu being open source and all.

I don't generally have my system slow down but I am installing fresh every 6 months :x

---

### Post by oldos2er on 2010-02-07
> **BobJam said:**
> Are the lib files listed by Computer janitor safe to remove?


Without knowing what packages you've installed, and which lib files Janitor wants to remove, it's impossible to say. A safer alternative would be to run **sudo apt-get autoremove**, which will remove dependencies that are no longer needed.

Slow screen redraws sounds like a video driver problem. Which video card do you have, and are you running the latest drivers for it?

---

### Post by BobJam on 2010-02-07
Watching SuperBowl right now (well . . . pre-game shows), but see a lot of replies here that need some thought in a response.  So, since I want to give this my undivided attention, will compose and post replies to all after the SuperBowl is over.

Thanks for all the ideas, btw.

Stay tuned . . .

---

### Post by 311005901 on 2010-02-07
:lol:
A man with priorities! :popcorn:

---

### Post by BobJam on 2010-02-08
OK . . . let's see if I can reply to each.  Here goes:

> **da burger said:**
> The programs computer janitor lists were installed as dependencies and are no longer needed (because the program they were installed with has been uninstalled) so I think they should be safe to remove.While some agree with you (3rdalbum, though h/she indicates that removing libraries no longer needed won't have any effect on my issue), some recommend caution (Sir Jasper and oldos2er).

Not being that confident in my skills with Ubuntu, I am inclined to be more cautious, consequently the Computer Janitor option is out right now 'till I get more responses and investigate more.


> **3rdalbum said:**
> +1, but libraries sitting on your system will not slow it down.Then that pretty much rules out Computer Janitor as a solution to my issue, though I may eventually use it just to get rid of useless debris.

> **3rdalbum said:**
> If screen redraws are slow, check the output of the "top" and "iotop" commands - is there a program using a lot of your CPU time or I/O capacity?Here I think is a partial display of what I got when I ran the "top" command:[INDENT]```
top - 04:18:14 up  2:05,  3 users,  load average: 0.12, 0.11, 0.09
Tasks: 174 total,   4 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.2%us,  4.2%sy,  0.0%ni, 83.0%id,  0.5%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   3577020k total,  1168916k used,  2408104k free,   106156k buffers
Swap:  9936160k total,        0k used,  9936160k free,   722884k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1520 root      20   0  140m  49m  14m S    8  1.4  16:55.95 Xorg               
 2707 rbjamie   20   0 42732  18m  14m S    8  0.5  12:40.91 gnome-system-mo    
 2486 rbjamie   20   0  137m  33m 7892 S    2  1.0   1:12.47 compiz.real        
 4866 root      20   0  2468 1096  800 R    2  0.0   0:00.08 top                
    1 root      20   0  2640 1536 1128 S    0  0.0   0:01.19 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.33 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:02.47 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.07 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns
```[/INDENT]It looks similar to the output of the GUI "System Monitor".

However, I don't really know how to read top (For example, what is "zombie"? And while I understand %CPU and %MEM, I don't get some of the more cryptic column headings, like "SHR".)  And, when I hit the Enter key, it seems to toggle through listings (which is why I'm showing a partial list only).  I got it to stop polling long enough to copy and paste by putting in the delay switch (-d) for 120 seconds.  I'm reading the manual, but it's going to take several reads to get my arms around it.

In any case, whether in "top" or "System Monitor", it **DOESN'T look** like anything is consuming CPU or Memory that would cause my symptom.

I installed iotop and ran it, but I have absolutely no idea what I'm looking at:[INDENT]```
Total DISK READ: 0.00 B/s | Total DISK WRITE: 0.00 B/s
  TID  PRIO  USER     DISK READ  DISK WRITE  SWAPIN     IO>    COMMAND          
    1 be/4 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % init
    2 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kthreadd]
    3 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/0]
    4 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/0]
    6 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [migration/1]
    7 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ksoftirqd/1]
    8 rt/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [watchdog/1]
    9 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [events/0]
   10 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [events/1]
   11 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [cpuset]
   12 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [khelper]
   13 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [netns]
   14 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [async/mgr]
   15 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd/0]
   16 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kintegrityd/1]
   17 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd/0]
   18 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kblockd/1]
   19 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpid]
   20 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpi_notify]
   21 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [kacpi_hotplug]
   22 be/3 root        0.00 B/s    0.00 B/s  0.00 %  0.00 % [ata/0]
```[/INDENT]> **OrangeCrate said:**
>  HOWTO: Cleaning up all those unnecessary junk files...

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)Thanks for the link.  Am reading through it (21 paqes!).  Will follow that regardless of whether or not I solve my issue.


> **jward3010 said:**
> Also if you want a full performance Ubuntu system, making sure proprietary drivers are installed can help. Go into System Menu > Admnistration > Hardware Drivers and see if there are any available to install.None to install.  It lists my "Broadcom STA wireless driver" (the only one listed) as "this driver is activated and currently in use", which I assume means the driver is installed.  And the machine wireless works just fine.

> **jward3010 said:**
> Having a 10GB used root partition means you've either a lot of programs or you have a pile of different files sitting there (video's, pictures, music, documents etc.). If the first one is true (that it's all programs), well there's a good chance that a few them like to run in the background. Do you regularly install and uninstall programs?Yes, I do indeed "regularly install and uninstall programs", so I'm sure I have a lot of useless leftover debris.  But according to 3rdalbum, leftover (dangling?) libs wouldn't have any effect on my issue.  Do you agree? Could there be other leftover elements besides libs?

I have a long list of startup applications as shown in System>Preferences>Startup Applications.  Are these TSR's ("daemons"?).  Is there a TTY line for listing Startup Apps or do I have to post screenshots from the GUI?  Some of the listings are pretty cryptic and I have no idea what they are, but maybe some of them are running in the background and I don't need them.  I'd like to show them here and get some opinions, but I don't know how to do it other than with screenshots or tediously listing them manually . . . which is why I'm asking if there's a command line that will do it . . . inserting the TTY output in a post would be a lot easier.


> **Sir Jasper said:**
> I suggest that if you do not have a clone or image just prior to any removal using Computer Janitor then do not use it without further investigation or seeking more advice here.Good advice, which, since I'm not confident of my Ubuntu skills, I will take.  I do have a humongous tarball file of my / and /home folders (I have these folders on different partitions) according to this HOW TO:  [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) (an old thread), but I've never tried the restore.  I have no idea if that can be considered a bootable image, but I assume I can at least restore my /home folder in a clean install from the LiveCD.  I'd rather not have to try that, which is why I'll probably stay away from this "Computer Janitor" right now.  Is there a TTY command I can use that will give the same output as "Computer Janitor"?  That way I can easily post it for advice.

> **Sir Jasper said:**
> PS I would also suggest saving a screen print so any/all deletions are known.On removable media I assume.  I mean, if I end up wiping out my system, I would need to have these screenprints on a USB stick to retrieve them.  But, it's highly unlikely I'm going to delete ANYTHING until I get my arms around this stuff . . . and I'm not there yet.


> **311005901 said:**
> Hey BobJam.
Your problems might come from a few things:

   1. These slowdowns may be a program freezing up. Check 'System>Administration>System Monitor' and select the tab 'Processes' when your computer hangs. You might be able to simply end the program. Usually when my computer hangs, it's because I have Desktop Effects enabled. (Desktop Effects will be called "compiz" in System Monitor)
      A program acting up will have close to 100% under the CPU column.My computer is NOT hanging at all.  It's just a bothersome slow repaint that's intermittent (seems pretty much random).  My System Monitor doesn't show any abnormal CPU or Memory use (see above)

I do have the CompizConfig Settings Manager installed, but my graphics card (VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller) doesn't support very many effects.

My suspicion at the moment is a TSR . . . jward3010's suggestion.  I did one time observe a 100% CPU draw on the "Resources" chart that remained at that level 'till I restarted, but I didn't see anything close to that on the listed "processes" (which was very baffling).  Unfortunately, I didn't have the presence of mind to run top or iotop, which might have given me a better clue.  Have been unable to duplicate that condition, but I'm running System Monitor while I'm composing this and checking it now and then.  So far, nothing.

> **311005901 said:**
> You may actually have a problem with your hard drive. If you have an older computer, this might be the cause of the slowdowns. I can help you if you think this is the problem.I have a Dell Inspiron 15N laptop that's barely a year old, so I don't think the HDD is the problem.  Thanks for the offer anyway.


> **ikt said:**
> I don't generally have my system slow down but I am installing fresh every 6 months From a LiveCD or an image?  If it's from a LiveCD, do you restore your /home folder so that you retain your app settings?  Or do you just flat out start over from scratch every time?


> **oldos2er said:**
> Without knowing what packages you've installedSee .odt.zip attachment.  Is a listing from ```
dpkg --get-selections > installed-software
```> **oldos2er said:**
> and which lib files Janitor wants to removeThat's why I'm looking for a tty output of Computer Janitor.  Otherwise I'm going to have to post multiple screenshots.

> **oldos2er said:**
> A safer alternative would be to run sudo apt-get autoremove, which will remove dependencies that are no longer needed.Ran it.  Here's the output:[INDENT]```
rbjamie@rbjamie-laptop:~$ sudo apt-get autoremove
[sudo] password for rbjamie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdb4.7-dev libldap2-dev libmysqlclient-dev libmysqlclient15off
  libopal3.6.4 libpcre3-dev libpt2.6.4 libpt2.6.4-plugins libqt4-assistant
  libqt4-help libqt4-scripttools libqt4-test libqt4-xmlpatterns
  odbcinst1debian1 python-qt4 python-sip4 ttf-wqy-zenhei unixodbc uuid-dev
0 upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
After this operation, 73.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 288490 files and directories currently installed.)
Removing libdb4.7-dev ...
Removing libldap2-dev ...
Removing libmysqlclient-dev ...
Removing libmysqlclient15off ...
Removing libopal3.6.4 ...
Removing libpcre3-dev ...
Removing libpt2.6.4-plugins ...
Removing libpt2.6.4 ...
Removing python-qt4 ...
Removing libqt4-assistant ...
Removing libqt4-help ...
Removing libqt4-scripttools ...
Removing libqt4-test ...
Removing libqt4-xmlpatterns ...
Removing unixodbc ...
Removing odbcinst1debian1 ...
Removing python-sip4 ...
Removing ttf-wqy-zenhei ...
Updating fontconfig cache for /usr/share/fonts/truetype/wqy
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
Removing uuid-dev ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
rbjamie@rbjamie-laptop:~$
```[/INDENT]> **oldos2er said:**
> Slow screen redraws sounds like a video driver problem. Which video card do you have, and are you running the latest drivers for it?My onboard graphics card is "VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller".  Wouldn't that already be compiled in my kernal (2.6.31-19-generic)?  That's what my xlog says.

> **311005901 said:**
> 
A man with priorities!Head was with Colts, heart was with NO.  Just goes to show that logic doesn't always apply.

Actually, my heart was more with the Colts too, so the outcome wasn't what I would have preferred.  That interception that Manning threw, much like Favre's, really did them in.

I knew there was going to be a turnover . . . was just that I was hoping the Colts would intercept Brees.  As time wore on, the suspense in waiting for the inevitable turnover was killing me.  Every time Manning threw, especially in the fourth quarter, I tightened up.  Wonder how it would have gone if Manning had not thrown that interception?  Was a close game up until then, but NO got a lot of momentum out of that.

Have to admit now that Brees deserves to be mentioned as a great QB just as much as Manning does.  Well . . . let's see if he does similarly over the next few years . . . THEN he will be in Manning's class.  Good start though.

But now I have to suffer withdrawal for 6 months.

---

### Post by oldos2er on 2010-02-08
"VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller"

The Intel video may be the source of your slow-downs. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1130582&page=18](http://ubuntuforums.org/showthread.php?t=1130582&page=18)

It starts out talking about Jaunty (9.04), but toward the end of the thread Karmic is discussed.

---

### Post by da burger on 2010-02-08
> **BobJam said:**
> OK . . . let's see if I can reply to each.  Here goes:

While some agree with you (3rdalbum, though h/she indicates that removing libraries no longer needed won't have any effect on my issue), some recommend caution (Sir Jasper and oldos2er).


I didn't think computer janitor was a solution to your problem. Just telling you that it should be safe.

If you want a terminal computer janitor run ```
sudo computer-janitor find
``` to list everything computer janitor would remove.

Use ```
sudo computer-janitor cleanup CRUFT
``` to remove one of the things computer janitor lists where CRUFT is what you want to remove.

Finally use ```
sudo computer-janitor cleanup --all
```to remove everything computer janitor lists.

To read more about computer janitor run ```
man computer-janitor
```

This shouldn't do much though because ```
sudo apt-get autoremove
``` would have removed any unneeded dependencies.

Sorry I don't have an answer to your main question, just spotted a couple of things I had responses for.

Angus.

---

### Post by Sir Jasper on 2010-02-08
Hi,

That was a very thorough response. After a quick read there are 2 points:

a) sudo apt-get autoremove was definitely good advice, but it is unlikely to speed up your system though it should safely make more space on your HD.
b) You can remove any Zombies without any ill effects.

My regards and best wishes

Added:
It may be worth choosing safe mode on a reboot and trying the options and perhaps the memory test on a further reboot. 

I think you are correct about having plenty of RAM but you might have a look in gnome-system-monitor under the Resources section just to check if you have any substantial Swap usage (you may still have a small usage as I have read that the Kernel sometimes make use of Swap).
Also, even if you hibernate, I think 6 GB Swap size would be plenty (for 4 GB of RAM);  but perhaps someone can either confirm that or suggest an alternative figure.

It sounds a strange test, but if you leave every opened program running (or minimised to the panel) does your system still slow?

---

### Post by chewit on 2010-02-08
I am tweaking/cleaning addict! I have picked up a few ideas...

> **OrangeCrate said:**
> ** HOWTO: Cleaning up all those unnecessary junk files...**

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Strongly recommend you follow this guide, will save you 100s of MBs of data!

Second,

I tool which I have recently discovered is called Bleachbit, information about it is here: [http://www.edhewitt.co.uk/2009/12/08/bleachbit-clear-out-the-junk-from-linux/](http://www.edhewitt.co.uk/2009/12/08/bleachbit-clear-out-the-junk-from-linux/)

Basically is like CCleaner for Windows, cleans out all your old files.

---

### Post by BobJam on 2010-02-08
> **oldos2er said:**
> The Intel video may be the source of your slow-downs. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1130582&page=18](http://ubuntuforums.org/showthread.php?t=1130582&page=18)

It starts out talking about Jaunty (9.04), but toward the end of the thread Karmic is discussed.Lookimg at it, but it's 131 pages long and bounces back and forth between my "VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller" and the Intel965 chipset.  So have to root through and "extract" what not only applies to my Intel chipset, but also, as you said, how it applies to Karmic.

Have read some already, and have questions already . . . so I'll probably post in that thread about it.

Thanks for the link.  More "homework".

---

### Post by BobJam on 2010-02-08
Working on responses to the most recent posts . . . I'm a response freak.  Since someone took the time to respond to me, I figure it's only courteous to respond back (and, NO, I don't expect to get into an endless loop of responses, so I'm not saying everyone needs to respond back to me).

Eventually, I hope to end this thread as "Solved" in some manner.

---

### Post by mikechant on 2010-02-09
You mentioned that your video card "doesn't support many effects" - I assume that means you've got some effects enabled. Have you tried running with them all turned off (the 'no effects' option - can't remember where this is since I'm not at my Ubuntu PC)?

---

