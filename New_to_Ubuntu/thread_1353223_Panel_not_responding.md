---
title: "Panel not responding"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by mikodo on 2009-12-12
Hello everyone,

When I started my computer this morning, the panels are blanked out on the desktop and are just showing white. To escape did Ctrl > Alt > Delete, and was told the an application or something was open and that "Panel is not responding". I have to let it shutdown or reboot anyways, as the panels do not respond after ~20 minutes of waiting. The icons appear Ie. Applications, Places, and System and my icons in panels after 20 minutes but remain unresponsive.

I let an update to the Kernel download last nite ( I believe). I don't know if this is related or not. I tried earlier versions of the Karmic Kernel and got the same results with panels though.

I use Karmic and update all updates as available.

I rebooted into Hardy on the same drive to be able to use Ubuntu with no problems with panels.

I have a Intel machine, and forget all the specs.

Good thing I don't keep a lot of stuff on my OS's, as I keep hosing them, as I try new things. LOL!

Is there anyone having any recent similar problems that can respond to as what the problem might be?

Thanks.

---

### Post by mikodo on 2009-12-12
Thanks for reading my post. I gotta go, I'll check later to see if anyone has seen similar problems.

Mike

---

### Post by wojox on 2009-12-12
Sounds like compiz. Do you have desktop effects enabled on that machine?

---

### Post by Shpongle on 2009-12-12
can you get to a terminal ? , on karmic , if so try reload the window manager, and see if that does it , it usually works for me the odd time i get a graphical glitch

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
You can also restart gnome-panel
you could try hitting Alt+f2 then typing:
```

kill gnome-panel

```
I don't know if you should select run in terminal or use gksudo on this command.

---

### Post by hobo14 on 2009-12-12
I had what may be a similar problem after I installed 9.10.

My panel (occasionally both) with the Window List on it would sometimes go berserk for no reason: all white, eat up about 60% CPU cycles, and wouldn't respond.
I didn't have compiz or anything running.

The problem went away when I removed the Window List from the panel and replaced it with [DockBarX]("http://gnome-look.org/content/show.php/DockbarX?content=101604") (looks much better too ;) )

---

### Post by mikodo on 2009-12-13
Well... I pretty much wasn't able to follow the advice of the other posters trying to offer assistance with this problem. I reconfigured Hardy on the same HD to my satisfaction and decided to use it for the time being.

This morning, I tried booting into Karmic "one more time" and it is back working a treat!!! The panels are back instantly upon booting up and all the icons etc., are responsive as before this problem.

I have absolutely no clue what happened and what changed to rectify the problem.

So for now, "so far so good".

Thanks.

---

### Post by herdivet on 2009-12-14
I had a problem where the panel simply locked up and never loaded.  I got a desktop, sometimes I got part of the panel (Applications, Places, System - although they didn't work) and the desktop responded but that was it.  The problem for me was the weather app on the panel.  Once I knew that, I found the solution here:

[http://ubuntuforums.org/showthread.php?p=8495431#post8495431](http://ubuntuforums.org/showthread.php?p=8495431#post8495431)

If you're running the weather app, and you have this lockukp problem, the solution is at that link.

Unfortunately, you have to stop running the weather app, and it's one of my favorites.  It does work in 9.10 on my two desktops, but not my laptop.

Your mileage may vary.

---

### Post by strange_cathect on 2009-12-14
Ok, but what if you really, really like your weather applet? You have to choose between the applet or a functioning panel? That isn't really a fix.

Does anyone know where this problem is? I didn't have this in 9.04, but it happens to me all the time in 9.10.

---

### Post by mikodo on 2009-12-14
Hello everyone,

I do not use the weather applet. Something else unknown was causing my panels to not load. I'm still in the dark here; Everything remains OK now. I've had no problems since that first day. Just thought you might want to know that this behaviour happens without the weather applet.

Wait a minute; I do have a desktop link that sends me to Environment Canada that provides daily weather and forecasts. Could this have something to do with it? I suppose not though, as it is not in a panel.

Thanks.

---

### Post by denzilmd on 2009-12-15
I've had 9.10 now for 1 day, This is my first day using any type of linux OS. and i am really struggling. 

Panels have frozen, gone all white, all icons missing, they do nothing. I accidentally found the internet. Followed above advice in this post as a i know i added the weather applet on my laptop. 

Im very close to re-installing ubuntu just so i can go back to exploring and playing. 

any ideas??

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
If you've just started using Ubuntu, and haven't installed much I'd say that reinstalling might be a good way to go... and if 9.10 has given you lots of problem you might be interested in trying 9.04 instead. If you enable the backports repositories you can get the newest software (firefox, etc.)

---

### Post by chamas on 2009-12-15
hello there, i have intalled 9.10 with no trouble, i then moved the top panel down and choose it to be hidden and boom... grey panel with nothing on them both and i can not access any commands.... all locked up..
 
i am new to linux and just started learning this language, is it possible to giude me to reinstall the the package that relate to the desktop layout?..
 
all i can is "ctrl+alt+f1" and then cd etc  and ls to list and see all the programs..i know  that ST3ALTHPSYCH0 has suggested to reinstall but is there anyone that can take tha challange to help us newbies....thank you very much...
 
reagrds
 
sam

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
You could try removing and reinstalling gnome-panel

---

### Post by chamas on 2009-12-15
ok, i will try the suggestion tonight.
 
can you gusee at the commands in need for:
 
download it from net if needed:
remove it:
install it:
 
 
 
note: at this point i dont care if i damage the operating system..so any suggestion is welcome.
 
 
thanks

---

### Post by ST3ALTHPSYCH0 on 2009-12-15
try 
```

sudo apt-get remove gnome-panel
sudo apt-get install gnome-panel
sudo reboot

```

---

### Post by mikodo on 2009-12-15
I removed the SOLVED from the title of the thread, as I see other posters having similar problems. For now the problem seems to have resolved itself for me, by no action on my part.

Thanks.

---

### Post by jamieleshaw on 2009-12-15
Hello, please do the following, these commands maybe risky-sih.

sudo apt-get purge gnome-panel
It will want to remove ubuntu-desktop so just let it.
then
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
Hope That helps ;)
P.S: If you want to reset your panels type  rm -f ~/.gconf/apps/panel
then sudo /etc/init.d/gdm restart

---

### Post by mikodo on 2009-12-15
Thanks for the reply(s).

Wouldn't you know it. Just turned my computer back on and booted into Karmic and the blank, unresponsive panels are back after ~4 days of everything working just keen. I haven't changed anything, except to allow updates since this started happening. Now I can't get into terminal, to try the most recent command suggestions.

I'm going to have to use Hardy again until something changes for now.

Thanks.

---

### Post by jamieleshaw on 2009-12-15
Boot into recovery mode select command shell with networking and then try those commands, or you can boot into it normally and bring up run by pressing ALT+F2 then typin in gnome-terminal

---

### Post by mikodo on 2009-12-15
hello, I ran the above codes  with recovery mode command shell with networking but got to a stage when after running 

sudo /etc/init.d/gdm restart it stated:

Since the script you are attempting to invoke has been converted to an Upstart job, you may use the restart (8) utility, eg. restart gdm 
gdm start/running, process 1622. That smiley face was supposed to be (8).

Smiley was supposed to be a 8 in brackets.

Then I tried,

root mikodo-desktop # sudo restart gdm

and was given:

restart: unknown instance

Then I tried: 

root mikodo-desktop # restart gdm

and was given:

restart: unknown instance
ENV must be Key=value pairs

Then tried

a command with ENV Key=value pairs (Sorry, I didn't write this down so I don't remember exactly what it was I exactly tried to run here) and was unsuccessful and pressed Ctrl>Alt>Delete. Rebooted into Karmic and found I still have the blank panels. Rebooted into Hardy and then made this long post.

Thanks.

---

### Post by mikodo on 2009-12-15
Hello, 

I tried the rm-f~/.gconf/apps/panel
then sudo /etc/init.d/gdm restart

and was unsuccessful.

I tried the repairing packages and reinstalled and installed a bunch of python stuff? and still am with blank and unresponsive panels.

This has been fun as a newbie, running all this code. I have to be up to get ready for work early in a too short nites' sleep, so thanks for the help and goodnite.

Mike

---

### Post by chamas on 2009-12-16
nothing that you guys suggested worked for me.
But here is what worked for me:
-right click on desktop and create a launcher/application in terminal option and save.
-open it and choose open terminal for left hand menu
-type : sudo open gnome-panel 
 
and voila it shows up as root bar and there is an extra grey bar is stuck on desktop and when i restart machine all is lost and i have to do it again to see panel...
 
so i made a new user and give him admin role and that solved the glitch for now...
 
note: you can tell i am a newbie from the way i discribe thing...lol.
 
regards
sam

---

### Post by jamieleshaw on 2009-12-16
> **chamas said:**
> nothing that you guys suggested worked for me.
But here is what worked for me:
-right click on desktop and create a launcher/application in terminal option and save.
-open it and choose open terminal for left hand menu
-type : sudo open gnome-panel 
 
and voila it shows up as root bar and there is an extra grey bar is stuck on desktop and when i restart machine all is lost and i have to do it again to see panel...
 
so i made a new user and give him admin role and that solved the glitch for now...
 
note: you can tell i am a newbie from the way i discribe thing...lol.
 
regards
sam
Running a panel as the root user isn't a good idea(in my opinion)
Please type rm -f ~/.gconf/apps/panel
and log out then in.
This will reset your gnome panel as one of the apps maybe making it unstable.

---

### Post by mikodo on 2009-12-16
> **jamieleshaw said:**
> Hello, please do the following, these commands maybe risky-sih.

sudo apt-get purge gnome-panel
It will want to remove ubuntu-desktop so just let it.
then
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
Hope That helps ;)
P.S: If you want to reset your panels type  rm -f ~/.gconf/apps/panel
then sudo /etc/init.d/gdm restart

Just a little more information. I ran the following code one more time last nite and found my desktop with panels working great this morning:

sudo apt-get purge gnome-panel
It will want to remove ubuntu-desktop so just let it.
then
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

When it came to the information that stated: Since the script you are attempting to invoke has been converted to an Upstart job, you may use the restart 8 utility, eg. restart gdm 
gdm start/running, process 1622; I then ran:

gdm start/running


and was rebooted in gnome without the panels. I then shutdown the computer and went to bed. As I stated above, in the morning upon restart of my computer with booting in Karmic, my panels were back, and again now, when I started my computer in Karmic.

This may be the solution I was looking for; or just a coincidence as the panels have come back for me before after shutting down and restarting in the A.M.

I hope this is the solution.

Thank you jamieleshaw and all other posters for your kind and knowledgeable help.

Mike

---

### Post by jamieleshaw on 2009-12-16
> **mikodo said:**
> Just a little more information. I ran the following code one more time last nite and found my desktop with panels working great this morning:

sudo apt-get purge gnome-panel
It will want to remove ubuntu-desktop so just let it.
then
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

When it came to the information that stated: Since the script you are attempting to invoke has been converted to an Upstart job, you may use the restart 8 utility, eg. restart gdm 
gdm start/running, process 1622; I then ran:

gdm start/running and was rebooted in gnome without the panels. I then shutdown the computer and went to bed. As I stated above, in the morning my panels were back, and again now, when I started my computer in Karmic.

This may be the solution I was looking for; or just a coincidence as the panels have come back for me before after shutting down and restarting in the A.M.

I hope this is the solution.

Thank you jamieleshaw and all other posters for your kind and knowledgeable help.

Mike
Glad to hear there working.

---

### Post by jamieleshaw on 2009-12-16
PS. The gdm restart is only for when you have the gui already loaded.

---

### Post by mikodo on 2009-12-16
> **jamieleshaw said:**
> PS. The gdm restart is only for when you have the gui already loaded.

OK!

Thanks

---

### Post by mikodo on 2009-12-24
Since following the code as quoted below, the panels have continued to work great in Karmic. I have had no problems and have made no changes since then. Since there has been no further posts with difficulties in this thread for some time, and everything has continued to work a treat for me, I am going to mark this thread as SOLVED. 

Thank you, everyone.

Mike

> **mikodo said:**
> Just a little more information. I ran the following code one more time last nite and found my desktop with panels working great this morning:

sudo apt-get purge gnome-panel
It will want to remove ubuntu-desktop so just let it.
then
sudo apt-get install gnome-panel
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

When it came to the information that stated: Since the script you are attempting to invoke has been converted to an Upstart job, you may use the restart 8 utility, eg. restart gdm 
gdm start/running, process 1622; I then ran:

gdm start/running


and was rebooted in gnome without the panels. I then shutdown the computer and went to bed. As I stated above, in the morning upon restart of my computer with booting in Karmic, my panels were back, and again now, when I started my computer in Karmic.

This may be the solution I was looking for; or just a coincidence as the panels have come back for me before after shutting down and restarting in the A.M.

I hope this is the solution.

Thank you jamieleshaw and all other posters for your kind and knowledgeable help.

Mike

---

### Post by mikodo on 2009-12-28
Well, I received another Karmic update this afternoon, from 2.6.31-16 generic pae to 2.6.31-17 generic-pae and the disappearing and unresponsive panel problem is back.

I ran the code that uninstalled and reinstalled the gdm, panels and desktop, to no avail. I'll run it again and shutdown after for the nite, and see what happens in the morning. Maybe I'll be lucky and have them back then; as before.

This is getting annoying!

Maybe someone, WHO KNOWS MORE THAN I, about what the heck is going on here, should file a bug report in Launchpad.

See ya,

Mike


Intel microprocessor 32 bit, integrated graphics, 2.39 mghz quad, 4gig ram, no router, just wired connection to modem.

---

### Post by mikodo on 2009-12-28
I FILED A BUG REPORT!   [https://bugs.launchpad.net/bugs/500958](https://bugs.launchpad.net/bugs/500958)

bug #500958 in  gnome-panel (Ubuntu)

Binary package hint: firefox-3.5

Last week, after receiving a kernel update (2.6.31-16-generic-pae), the panels became unresponsive. After doing a terminal un-install of gdm, panels, and desktop and re-installing them a fix was not acquired. Upon restarting the computer in the A.M., the panels returned in gnome and were responsive as always.

This afternoon, I received a new kernel update to 2.6.31-17-generic-pae, and seemingly, everything was working with the panels and eventually I shut down. Upon restarting the computer, and gnome opening, the panels were white initially, with no icons and eventually after 10 to 20 minutes the icons appeared, but remained unresponsive; (just as in the previous kernel update). I tried the un-installing and re-installing as before to no avail.

In both instances I had to use Ctrl > Alt > Delete and received notifications "panel is unresponsive" and did I want to continue with the "dirty shut down"; as the panels were still running.

My installation of Karmic was via live CD ~ Oct 30, and I have had no other noticeable problems.

ProblemType: Bug
Architecture: i386
Date: Mon Dec 28 00:40:26 2009
DistroRelease: Ubuntu 9.10
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
Package: firefox-3.5 3.5.6+nobinonly-0ubuntu0.9.10.1
ProcEnviron:
 LANG=C
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 2.6.31-17.54-generic-pae
SourcePackage: firefox-3.5
Uname: Linux 2.6.31-17-generic-pae i686
XsessionErrors:
 (gnome-settings-daemon:2654): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
 (gnome-settings-daemon:2654): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
 (polkit-gnome-authentication-agent-1:2777): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
 (nautilus:2752): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
 (firefox:2886): GLib-WARNING **: g_set_prgname() called multiple times
 CancelOk


Thank you.

---

### Post by mikodo on 2009-12-28
Say, from the bug report information from my computer, when it read:

Uname: Linux 2.6.31-17-generic-pae i686

Should it have read at the end as: i386?

Or, does that not matter?

Thank you.

---

### Post by mikodo on 2009-12-28
Well, after ~ 3 hours the panels started working. I rebooted and they are white again with no icons. Go figure!

I guess I wait and see what the folks at Launchpad can find out.

Thank you.

---

### Post by mikodo on 2010-01-04
Here is a response from Bubba, in the thread from the bug report I filed in Launchpad. I haven't had to try it, as there has not been a kernel update since the response and for now my panels are working again. It may helpful to someone else with the freezing panels.

See below:


I have a similar (identical?) problem with intermittent panel freezes at boot. I have found ten other bugs with nearly identical trouble.
I have also discovered that I can recover my panel functionality with two steps that you may wish to try. This works 100% of the time on my machine.

Access a terminal (Ctl-Alt-F1) and execute the following command;

 $ killall gnome-panel

The second step is to return to the desktop (Ctl-Alt-F7) and open a "Run application" window (Alt-F2) and execute the command;

 $ gnome-panel --replace

My panels and system are completely functional now (except for missing weather apps). Do not use a desktop terminal for the second command - the process will hang in a terminal. See Bug #466118 for more comments.

Hope this works for you too...

---

### Post by fishnuke on 2010-02-19
Similar problem.

New installation of 9.10, upgraded to latest versions after install.

User modifications to panel layout:
- Had just added a terminal button to bottom panel using mouse menu right click from Applications->Accessories->Terminal.
- Set main panel (the one with Applications|Places|System and date/time) to autohide, set properties to bottom.
- Set properties on the taskbar panel (shows running applications and the desktop switcher) to bottom.

Immediate blank white panel after last step.  Desktop unresponsive (ie no response to right clicks, etc), even after reboot.  Same behavior in failsafe Gnome.

After ctrl-alt-F2, and sudo killall gnome-panel, and returning to ctrl-alt-F7, had complete hang, not even a moving mouse, or ability to ctrl-alt-F2 again.

Hard rebooted, ctrl-alt-F2 again, top:

command            CPU        memory
gnome-panel         62.9%      8.1%         and climbing
Xorg                   ~14%         2.2%
gnome-settings-    ~2%         1.6%
nautilus                    .7%       3.7%
top                           .3%         .2%

Obviously some weird bug in there, what could possibly be eating that much CPU from a few buttons on a panel?!

Tried:

rm -rf ~/.gconf/apps/panel
sudo /etc/init.d/gdm restart

Logged back in and panels seem responsive and back to default state.  Won't mess with them again!!!

---------------------------------------------------

I suggest the bug is hanging when reading the panel configuration files.  It seems the read routine is hanging and spinlocking the CPU, instead  of failing graciously when it gets bad input config.  Maybe there is also another bug writing screwy configuration files.

Perhaps a quick workaround would be putting the read panel configuration in a new thread, if it doesn't return in a reasonable timeout, kill the thread and load the default panel.  That way we users are at least guaranteed a (default) interface without jumping through hoops.

Seriously, looking at the dates on these threads, and googling "ubuntu unresponsive panel", this is a common problem that has been ongoing for over a year, over several versions of ubuntu.  It's not like it's caused by some special configurations, just very standard gnome in a default install.

Developers, please help!

---

### Post by venividibitchy on 2010-03-21
Seriously...why isn't this issue getting any attention?

I've personally been experiencing this since January, and the only thing that helps is ctrl+alt+f1 and typing "killall gnome-panel". The panel loads and works perfectly then -- though often my weather applets won't show (but then will mysteriously appear a few boots later).

It is very annoying to do this BS every few boots.

---

### Post by krisrose on 2012-04-09
The bug is back with linux-image 2.6.32-41.88
(at least on 10.04 LTS with pre-unity panels).

---

### Post by oldos2er on 2012-04-09
Closed, necromancy. Please start a new thread.

---

