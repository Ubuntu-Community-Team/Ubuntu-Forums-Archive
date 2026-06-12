---
title: "Screen resolution too low, again!"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by VgnStirfry on 2009-05-21
After all this:
[http://ubuntuforums.org/showthread.php?t=1156934](http://ubuntuforums.org/showthread.php?t=1156934)
my newly installed version of Ubuntu 9.04 was working properly.  Although my monitor remained listed as "unknown", I had the highest resolution physically possible with my monitor at the highest refresh rate, and all was well.

I installed it several days ago and have shut down and started up quite a few times since then.  This morning, I look and my monitor's resolution is much lower, and there are no options to make it higher.

*Hardware:*
Monitor: Sony Trinitron Multiscan 420GS
Video card: EVGA Nvidia GeForce 6200

*Software*
OS: Ubuntu 9.04 (Jaunty)
Video card: Nvidia X Server, using version 180 (the newest one as of a few days ago)

Please help!  I really don't want to have to reinstall my OS again!

---

### Post by unutbu on 2009-05-21
Please post the output of 
```

ls -l /etc/X11
```
(You might have a backup copy of xorg.conf which we could use...)

---

### Post by Brutus2006 on 2009-05-21
I always thought it was my video card, but it was my monitor that wasnt configured correctly. What I did was in Terminal I typed gtf 1680 1050 60 ( numbers from my monitor manual) then it brings up a modeline I opened up xorg and pasted it in my monitor section. Saved and has worked perfectly ever since.

Hope this helps for you did for me

---

### Post by Talon2 on 2009-05-21
I recently had a friend have what appears to be the same exact problem.  His system has a Nvidia graphics card and a 17" CRT monitor.  He finally just went back to v8.10 as he needs a stable system he can count on for work over the next few months.

Please do report this bug if it hasn't already been reported.

---

### Post by CatKiller on 2009-05-21
[http://ubuntuforums.org/showpost.php?p=7272155&postcount=50](http://ubuntuforums.org/showpost.php?p=7272155&postcount=50)

Or just reboot with the monitor on, since it's worked previously.

---

### Post by VgnStirfry on 2009-05-21
> **unutbu said:**
> Please post the output of 
```

ls -l /etc/X11
```
(You might have a backup copy of xorg.conf which we could use...)

Here it is:

total 52
drwxr-xr-x 2 root root 4096 2009-04-20 10:08 app-defaults
drwxr-xr-x 2 root root 4096 2009-04-20 10:08 cursors
-rw-r--r-- 1 root root   14 2009-04-20 10:07 default-display-manager
drwxr-xr-x 6 root root 4096 2009-04-20 10:04 fonts
lrwxrwxrwx 1 root root   13 2009-05-16 18:59 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root 4096 2009-04-20 10:08 xinit
drwxr-xr-x 2 root root 4096 2009-04-20 09:59 xkb
-rw-r--r-- 1 root root 1137 2009-05-16 20:16 xorg.conf
drwxr-xr-x 2 root root 4096 2009-04-20 10:00 Xresources
-rwxr-xr-x 1 root root 3730 2008-06-24 22:05 Xsession
drwxr-xr-x 2 root root 4096 2009-05-16 19:37 Xsession.d
-rw-r--r-- 1 root root  265 2008-06-24 22:05 Xsession.options
-rw-r--r-- 1 root root   13 2007-07-24 05:59 XvMCConfig
-rw------- 1 root root  614 2009-04-20 10:00 Xwrapper.config

---

### Post by VgnStirfry on 2009-05-21
> **Brutus2006 said:**
> I always thought it was my video card, but it was my monitor that wasnt configured correctly. What I did was in Terminal I typed gtf 1680 1050 60 ( numbers from my monitor manual) then it brings up a modeline I opened up xorg and pasted it in my monitor section. Saved and has worked perfectly ever since.

My monitor is old and I do not have a manual for it.  Anyone know how to get the appropriate numbers?

---

### Post by VgnStirfry on 2009-05-21
> **CatKiller said:**
> [http://ubuntuforums.org/showpost.php?p=7272155&postcount=50](http://ubuntuforums.org/showpost.php?p=7272155&postcount=50)

Or just reboot with the monitor on, since it's worked previously.

Rebooting with the monitor on did not work (I tried it twice before posting this thread), but putting:

```
HorizSync    30-96
VertRefresh    48-120
```

... in the monitor section of my xorg.conf *did* resolve the issue.  Thank you again, CatKiller, for helping me, I greatly appreciate it.

---

### Post by unutbu on 2009-05-21
Glad you found a solution! :)

---

### Post by Didius Falco on 2009-05-21
> **VgnStirfry said:**
> My monitor is old and I do not have a manual for it.  Anyone know how to get the appropriate numbers?

Hi,

Are you still using the Sony Trinitron Multiscan 420GS? Here is the manual for it, with the resolution and refresh rates settings:

[http://www.docs.sony.com/reflib/docget.asp?manualid=19315&template_id=1&region_id=1&DL=](http://www.docs.sony.com/reflib/docget.asp?manualid=19315&template_id=1&region_id=1&DL=)


If you are using a different model now, what is it, and I'll see what I can find....

Regards,

Didius

On Edit: Typing slow **sucks**!!!

---

### Post by VgnStirfry on 2009-05-21
> **Talon2 said:**
> I recently had a friend have what appears to be the same exact problem.  His system has a Nvidia graphics card and a 17" CRT monitor.  He finally just went back to v8.10 as he needs a stable system he can count on for work over the next few months.

Please do report this bug if it hasn't already been reported.

Please be sure to tell your friend about the fix that worked for me.  

Honestly, I am too overworked at the moment to learn how to properly submit a bug report.

---

### Post by VgnStirfry on 2009-05-22
Forgive me for forgetting, Didius; I was helping a friend deal with a really terrible crisis for the past two weeks and my attention has been elsewhere.

Yes, it is the same monitor.

However, the fix that CatKiller offered only worked for two reboots; now the problem has **reappeared**.  I am very confused as to why this is happening and as editing xorg.conf resulted in a heinous mess last time, I'm skittish.  Any ideas?

---

### Post by Didius Falco on 2009-05-22
> **VgnStirfry said:**
> Forgive me for forgetting, Didius; I was helping a friend deal with a really terrible crisis for the past two weeks and my attention has been elsewhere.

Yes, it is the same monitor.

However, the fix that CatKiller offered only worked for two reboots; now the problem has **reappeared**.  I am very confused as to why this is happening and as editing xorg.conf resulted in a heinous mess last time, I'm skittish.  Any ideas?

I've never used an nVidia card under Ubuntu, so I'm a bit hesitant to start throwing out suggestions myself. 

I'll monitor the thread, and throw out anything I can find, but that's about all I can do.

I hope your friend has come through the crisis okay...

Regards,

Didius

---

### Post by CatKiller on 2009-05-22
I second Didius Falco's comment; I hope your friend is doing OK.

> **VgnStirfry said:**
> However, the fix that CatKiller offered only worked for two reboots; now the problem has **reappeared**.  I am very confused as to why this is happening and as editing xorg.conf resulted in a heinous mess last time, I'm skittish.  Any ideas?

So the monitor works sometimes, but sometimes when you boot (even if you boot with the monitor turned on) the resolution isn't right?

Has your xorg.conf been changed by anything (upgrades or whatnot) between it working and it not?

The log file for X is at /var/log/Xorg.0.log. You could have a look at that to see what it has to say for itself. In particular, I'd probably be looking for a line that says that xorg.conf.failsafe is being used for some reason. But any indication of why the modes aren't being used would be good, I guess.

---

### Post by MrChainBlueLightnin on 2009-05-23
I have a DELL D1028L CRT and I am having the same trouble.  If I need to add sync, etc. to xorg.conf file.  What commands do I type to access it to add that code?

---

### Post by CatKiller on 2009-05-24
> **MrChainBlueLightnin said:**
> I have a DELL D1028L CRT and I am having the same trouble.  If I need to add sync, etc. to xorg.conf file.  What commands do I type to access it to add that code?

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```According to [this page]("http://support.dell.com/support/edocs/monitors/84779/specs.htm"), the values that you want are

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-69
        VertRefresh     50-120
EndSection

```

---

### Post by MrChainBlueLightnin on 2009-05-24
After I add the code, just save and close the file?  Then what?  Will the new options for resolution show up under System>Pref>Display

---

### Post by DarinB on 2009-05-24
what worked for me was booting into recovery mode
and removing all the drivers except the basic nvidia core
when i when to a new system with a nvidia 8600gt i have been fine. it is a nightmare and hair pulling experience.
one thing that helped was going to a cheap 15" lcd i picked up for 15 dollars. 
it worked great and i didn't have the problem, while i waited for my new system to be built.
i think it is a monitor incompatibility issue but i can't find any corroborating evidence to prove it.
good luck i suffered through this for two years with my old system but i had a geforce 440mx it is shocking to hear about it with a 6200 but i would try an lcd monitor before chucking it all out or replacing the video card.

---

### Post by CatKiller on 2009-05-24
> **MrChainBlueLightnin said:**
> After I add the code, just save and close the file?  Then what?  Will the new options for resolution show up under System>Pref>Display

After you've restarted X. The simplest way for you to do that is probably to just reboot the machine.

---

### Post by MrChainBlueLightnin on 2009-05-25
Thanks guys.  You were right on the money Cat Killer. I can go all the way up to 1680 x 1050.   Unfortunately now it goes to a black screen with an icon at the bottom right.  It says "username" will log in in 10 seconds, and it has a window to type a different username.  When I go back to 800 x 600 it does not do it. I also tried different refresh rates, to no avail. Perhaps the problem is that it says "unknown monitor" in the preferences?

---

### Post by CatKiller on 2009-05-25
It sounds to me like your GDM login window is now at 1680×1050 (as it should be) but the resolution of the monitor at that point is much lower (I'd guess at 800×600, since you said that they line up at that resolution). I'm afraid that I don't know how to fix that, but now that you know what the problem is, a search might yield something.

The "Unknown Monitor" is the reason why you had to enter the refresh rate ranges manually. Monitors should identify them with EDID and present that information automatically. Yours doesn't, which is why you entered the information X needs to configure the monitor.

EDIT: Some people have reported that changing the login window theme, logging out and logging back in, and then changing the theme back fixes the login window resolution problem. I've not had this problem, so I can't say that it will definitely work for you. Doesn't take long, though, so it's probably worth a try.

---

### Post by unutbu on 2009-05-25
molom reports that unplugging the DVI cable and power cable from the monitor and then plugging them back in again solved his problem. ([http://ubuntuforums.org/showpost.php?p=7342247&postcount=10](http://ubuntuforums.org/showpost.php?p=7342247&postcount=10))

Along with what CatKiller suggests, that's another easy thing you could try.

---

### Post by Didius Falco on 2009-05-26
I just had a thought - I didn't see any mention by VgnStirfry of having run nvidia-settings to set up his card...

I haven't seen any new posts by him lately either - Hey, VgnStirfry, have you tried that?


Regards,

Didius

---

### Post by VgnStirfry on 2009-06-03
Hi, Didius and CatKiller, things on my end are borked at the moment, and my computer issues have had to go by the wayside for the time being.  Thanks for your help so far, I'll be back in a bit, hopefully this week.  Maybe I'll be able to offer someone else some help.  :)

---

