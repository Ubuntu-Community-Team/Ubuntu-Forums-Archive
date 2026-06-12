---
title: "Mobloquer - A new MoBlock GUI"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by jimtb on 2008-02-21
Hi everybody!

I've been developing for some months a Graphical User interface for [_MoBlock_]("http://moblock.berlios.de/") in C++ using Qt4. The project's name is Mobloquer and the latest stable version is 0.5.

The program heavily relies on the moblock-control script written by jre, so the easiest way to get mobloquer working in Ubuntu/Debian at the moment is to install the packages from the [_moblock-deb repository_]("http://moblock-deb.sourceforge.net/").

Features:
[LIST][*] View the IPs which MoBlock blocks in realtime as well as some information about each one.
[*] Easily view whois information for each IP blocked.
[*] Easily configure moblock to stop blocking an IP.
[*] Add/Remove/Enable/Disable blocklists and tweak their settings.
[*] Quickly tweak moblock's settings such as automatic startup, blocklist format, automatic updates etc.
[*] Whitelist specific ports.
[*] Whitelist IPs/hostnames.
[*] Remove entries from the blocklists.
[*] View the state of moblock daemon.
[*] View some information about moblock such as the number of the loaded ranges, the last time the blocklists were updated etc.
[*] View the log produced by the moblock-control script in real time.
[*] View the current iptables rules to determine if moblock is working.
[*] Start/Restart/Stop/Reload/Update MoBlock with just one click.[/LIST]

Screenshots[Click for larger images]:
[[IMG]http://mobloquer.foutrelis.com/html/uploads/media/2/image/QMuo6MDKbG/thumb_QMuo6MDKbG.png[/IMG]]("http://mobloquer.foutrelis.com/media/view/logs_tab")[[IMG]http://mobloquer.foutrelis.com/html/uploads/media/2/image/Am03CGSGQJ/thumb_Am03CGSGQJ.png[/IMG]]("http://mobloquer.foutrelis.com/media/view/blocklists_tab2")[[IMG]http://mobloquer.foutrelis.com/html/uploads/media/2/image/AhjEbcY8t2/thumb_AhjEbcY8t2.png[/IMG]]("http://mobloquer.foutrelis.com/media/view/settings_tab2")[[IMG]http://mobloquer.foutrelis.com/html/uploads/media/2/image/kc76rsPFOF/thumb_kc76rsPFOF.png[/IMG]]("http://mobloquer.foutrelis.com/media/view/manage_tab2")

Links:
[_Official website_]("http://mobloquer.sourceforge.net/")
[_Sourceforge.net project page_]("http://sourceforge.net/projects/mobloquer")
[_Mobloquer on qt-apps.org_]("http://www.qt-apps.org/content/show.php/mobloquer?content=73608")

---

### Post by czer323 on 2008-02-21
The default block lists added by moblock are paranoid and block practically everything.  For example, imap gmail access is blocked.  It's not hard to goto the block log section of mobloquer and unblock the ip, but it'd be nice to know exactly which list is blocking that ip, since there are ranges of ips that are blocked.  Then I could disable the more paranoid lists.

I'm suggesting to add an additional column for the blocklist that was used to block a particular IP in the  "Logs" section.

Also, is there a better place to make suggestions or report bugs? Edit: Nevermind, I found the sourceforge page.

---

### Post by isaacj87 on 2008-03-04
First off, this is a fantastic program...:) It works well and has a clean, easy-to-use interface...

I only have a feature request! Is it possible to have an option to have MoBloquer start up on boot and be hidden to tray? I know MoBlock can start up automatically, I just would like to have the the GUI (aka MoBloquer) do the same. :)

Thanks!

---

### Post by jre on 2008-03-04
> **czer323 said:**
> I'm suggesting to add an additional column for the blocklist that was used to block a particular IP in the  "Logs" section.
The moblock daemon reads only one blocklists which consists of the cat'ted together single blocklists. So this is not possible until this behaviour is changed by the upstream author.

---

### Post by Crash90 on 2008-03-05
Woot! Thanks! Great program!

---

### Post by Dawa on 2008-03-05
lately mobloquer has been crashing on me.  the tray icon is totally unresponsive and i have to kill the program through System Monitor.  once i start it again, everthing is back to normal.  moblock is still running and mobloquer acts like it always does.

I've also noticed that timestamping has pretty much disappeared in the log display - it started with just saying "1" for pretty much every entry, the number has now increased to "5".  weird.

any advice?

---

### Post by isaacj87 on 2008-03-05
> **Dawa said:**
> lately mobloquer has been crashing on me.  the tray icon is totally unresponsive and i have to kill the program through System Monitor.  once i start it again, everthing is back to normal.  moblock is still running and mobloquer acts like it always does.

I've also noticed that timestamping has pretty much disappeared in the log display - it started with just saying "1" for pretty much every entry, the number has now increased to "5".  weird.

any advice?

I've had similar problems. The timestamp is always a single digit number for me as well. and I've had MoBloquer complete stop working. No error in terminal as well. I'm sure these bugs will be ironed out as new releases come :)

---

### Post by jimtb on 2008-03-05
Hello again!

To begin with, I would like to thank you all for your comments.


> **isaacj87 said:**
> I only have a feature request! Is it possible to have an option to have MoBloquer start up on boot and be hidden to tray? I know MoBlock can start up automatically, I just would like to have the the GUI (aka MoBloquer) do the same. :)

Thanks!

Of course, just go to System->Preferences->Sessions and add the following as a command to start mobloquer minimized every time gnome starts:
```
mobloquer --tray
```

I am already aware of the bug with the time stamping, and I have fixed it in subversion  In case you're wondering, the number which appears in the Time column right now is the current date. For example today's time/date string in moblock.log is: "Thu Mar  6 00:36:38" so 6 appears in mobloquer due to a problem in the function I used to get the time.
Mobloquer 0.4.1 will be released very soon in order to fix this and some other annoying bugs. 

After releasing 0.4.1, I'll start working on new features, so I guess that 0.5 may be ready sometime before easter, but I can't promise anything yet.

:-)

---

### Post by Dawa on 2008-03-08
another error I've noticed is that if i use the "update" button in mobloquer; i always get a "level1.gz - unexpected end of file" error in the mobloquer log display.  if i run moblock-control update; this doesn't happen.  sorry if this is already covered in the coming update - but you never know  :)

---

### Post by jimtb on 2008-03-09
> **Dawa said:**
> another error I've noticed is that if i use the "update" button in mobloquer; i always get a "level1.gz - unexpected end of file" error in the mobloquer log display.  if i run moblock-control update; this doesn't happen.  sorry if this is already covered in the coming update - but you never know  :)

Hi again!

I don't think that this has anything to do with mobloquer as the program simply executes moblock-control update when you press the "update" button. To verify if this is an issue with mobloquer, open two tabs(or two terminals) and execute the following commands, one into each terminal:
```
tail -f /var/log/moblock-control.log
```
```
sudo moblock-control update
```

Check the output of the first command and see if the same error message appears.

:-)

---

### Post by jimtb on 2008-03-10
**Mobloquer 0.4.1 is out!**

This is a bugfix release. Some annoying bugs are now fixed and the work on new features has begun.  

**ChangeLog **

Version 0.4.1 
---- 
FIXED: A bug which caused invalid values to appear in the "Time" column of the "Logs" tab when using moblock 0.9. 
FIXED: Improved the way the number of the currently loaded ranges is updated. Now, if the value does not exist in moblock's log, mobloquer will search for the value when moblock is started/restarted. 
FIXED: A bug in the way moblock's settings were exported which caused the IP_REMOVE function of the moblock-control script not to work. 
FIXED: Improved the mobloquer's behaviour when the temporary files used to store settings and lists are not writable by the program.

You can either [download it now]("https://sourceforge.net/project/platformdownload.php?group_id=211699&sel_platform=5985") or wait a couple of days for jre to package it.

:-)

---

### Post by isaacj87 on 2008-03-10
Seems to be working well! the timestamp bug is definitely fixed. Thanks for the new release and I can't wait to see some new features added :)

---

### Post by Dawa on 2008-03-11
> **jimtb said:**
> Check the output of the first command and see if the same error message appears.

:-)

i ran the -tail and did a moblock-control update; everything seemed to go just fine.  i have mobloquer 0.4.1 now; if i press the update button, the window greys out for a second, then the log in mobloquer stops at level1.gz.  however, after i press reload i no longer get the error message, and it seems to be blocking the correct amount of ip ranges - so apparently it's working.

---

### Post by jre on 2008-03-11
I had the "unexpected end of file" error with level1.gz, too. The list had only 700kB here instead of 3MB.
The error messages appeared both in mobloquer and moblock-control.log and caused the update to abort (that's the correct behaviour, otherwise you would get an incomplete new blocklist instead of a complete old blocklist).
Maybe bluetack accidentally uploaded a malformed blocklist or otherwise "wget" somehow thought it downloaded the file successfully although it didn't!?
So, I doubt this is a bug in mobloquer. But I also can't find a bug in moblock-control.
Anyway, I changed the code in moblock-control (not released, yet) to delete blocklists if they can't be unpacked. This way a new download will happen with the next "moblock-control update".

---

### Post by lebabyg on 2008-03-11
Hey, 

First just wanted to say thanks for developing Mobloquer.  It's fantastic.  However i do seem to have some issues with it on Gutsy with Qt4.  Whenever i right click and try to restart/stop/start it crashes x completely.  Also If i try to unblock an Ip for instance the dialogue box pops up saying i need to restart mobloquer for this to have an affect, but then the app becomes unresponsive and i have to kill it using system monitor.  These are the only issues i have now, aside from this it's perfect as a monitor.  

Cheers

---

### Post by jimtb on 2008-03-11
> **lebabyg said:**
> Hey, 

First just wanted to say thanks for developing Mobloquer.  It's fantastic.  However i do seem to have some issues with it on Gutsy with Qt4.  Whenever i right click and try to restart/stop/start it crashes x completely.  Also If i try to unblock an Ip for instance the dialogue box pops up saying i need to restart mobloquer for this to have an affect, but then the app becomes unresponsive and i have to kill it using system monitor.  These are the only issues i have now, aside from this it's perfect as a monitor.  

Cheers


Hi, thanks for your comments. 

To begin with, I have no idea why the XServer crashes but I don't think that this is directly connected to mobloquer. It is probably a bug in the Qt library and I can't reproduce it. You can check the Xorg.0.log to see if you can find any useful indications to why this happens. 

Your second problem is not really a bug. In order to prevent multiple kdesu/gksu windows from appearing, mobloquer waits for the gksu/kdesu process to start. If your system is busy at the moment this may take a while, in some occasions I had to wait up to 10 seconds for the password prompt to appear. During this time the main loop of the program stops waiting for the process to start and as a result it seems as if mobloquer has stopped working. 
Unfortunately there is little I can do to improve this situation. You can either wait, or start mobloquer as root( gksu mobloquer/kdesu mobloquer) whenever you want to change a setting. 

Hope I helped.

:-)

---

### Post by jimtb on 2008-03-11
I don't have the time to start working on new features yet but I've started adding some documentation inside Mobloquer:
[[IMG]http://img181.imageshack.us/img181/7880/moprevzw9.th.png[/IMG]](http://img181.imageshack.us/my.php?image=moprevzw9.png)
[[IMG]http://img187.imageshack.us/img187/1632/addbbz5.th.png[/IMG]](http://img187.imageshack.us/my.php?image=addbbz5.png)

I also changed the date format to dd/mm/yyyy. It is easier for me to read but I would like to hear from the users:
[[IMG]http://img142.imageshack.us/img142/1072/modatehd0.th.png[/IMG]](http://img142.imageshack.us/my.php?image=modatehd0.png)

That's it for now, more updates coming sometime soon I hope.

:-)

PS. There is one bug you should know about in 0.4.1, fixed in SVN. Log entries containing the pipe character in their "name" section will not be shown in mobloquer, e.g. "Scammers|FutureCreditConsultingLimited". There are only about 600 in my guarding.p2p file out of the 270.000+ ranges so you may never come across one of those, but if any problems arise, check the contents of the moblock.log just in case, until the next version of mobloquer is released.

---

### Post by ryukent on 2008-03-12
Have been using this software for a few weeks now. Can I just say it is great!! Many thanks for your hard work!!!

---

### Post by raffytaffy on 2008-03-12
NVM - solved own problem, good gui program.

---

### Post by isaacj87 on 2008-03-16
Hi, I carelessly hit "Stop blocking this IP" when I was looking at the blocked IP info...is there any way to reverse this? thanks

---

### Post by jimtb on 2008-03-17
> **isaacj87 said:**
> Hi, I carelessly hit "Stop blocking this IP" when I was looking at the blocked IP info...is there any way to reverse this? thanks

Until I add the "WhiteList IPs" dialog which will allow you to add/remove IPs in the whitelist you can't do it through the GUI.

Open the moblock.default file with a text editor:
```
gksu gedit /etc/default/moblock
```

There will probably be a line starting with "WHITE_IP_IN" or "WHITE_IP_OUT" containing the IP you whitelisted. Just remove the IP from there, save the file and restart MoBlock.

:-)

---

### Post by isaacj87 on 2008-03-17
> **jimtb said:**
> Until I add the "WhiteList IPs" dialog which will allow you to add/remove IPs in the whitelist you can't do it through the GUI.

Open the moblock.default file with a text editor:
```
gksu gedit /etc/default/moblock
```

There will probably be a line starting with "WHITE_IP_IN" or "WHITE_IP_OUT" containing the IP you whitelisted. Just remove the IP from there, save the file and restart MoBlock.

:-)

Thank you! worked like a charm. :)

---

### Post by jimtb on 2008-03-21
It took me a while but I've almost finished the "WhiteList IPs" dialog. It is working pretty well in the latest svn revision although there are some things I want to fix/improve before starting to add more new features. 

Here's a screenshot:
[[IMG]http://img410.imageshack.us/img410/2791/mscreennc4.th.png[/IMG]](http://img410.imageshack.us/my.php?image=mscreennc4.png)
And here's a second screenshot after some changes I made:
[[IMG]http://img178.imageshack.us/img178/6880/screenshotwhitelistipspr7.th.png[/IMG]](http://img178.imageshack.us/my.php?image=screenshotwhitelistipspr7.png)

:-)

---

### Post by isaacj87 on 2008-03-22
> **jimtb said:**
> It took me a while but I've almost finished the "WhiteList IPs" dialog. It is working pretty well in the latest svn revision although there are some things I want to fix/improve before starting to add more new features. 

Here's a screenshot:
[[IMG]http://img410.imageshack.us/img410/2791/mscreennc4.th.png[/IMG]](http://img410.imageshack.us/my.php?image=mscreennc4.png)
And here's a second screenshot after some changes I made:
[[IMG]http://img178.imageshack.us/img178/6880/screenshotwhitelistipspr7.th.png[/IMG]](http://img178.imageshack.us/my.php?image=screenshotwhitelistipspr7.png)

:-)

This is shaping up really nicely :)

I'm getting the latest from SVN as we speak.

---

### Post by chunchengch on 2008-04-02
Mobloquer blocks the internet connection, if I stop it then the connect is back, is the setting wrong? thanks for help!

[ATTACH]64778[/ATTACH]

---

### Post by chunchengch on 2008-04-03
I just installed mobloquer 0.4.1-1 from Synaptic in my Ubuntu Gusty, but it blocked everything by default, I enabled allowed connections of both incoming and outgoing of HTTP and HTTPS, but it didn't work. any comment? thanks a lot!

BTW, I wonder if it is possible to set mobloquer not to block everything by default, so it can just works after installation, this will be much helpful for those who just want something to protect their Linux system but not very familiar with the setting of moblock.

---

### Post by chunchengch on 2008-04-03
1. I re-install mobloquer and moblock, then edit /etc/moblock/moblock.conf and Uncomment WHITE_TCP_OUT="80 443", now I can connect to the internet, but when I ping 168.95.192.1, I find "100% packet loss" in the output, although I am not quite familiar with this message, but I guess it means "not safe".

[COLOR="Red"]PING 168.95.192.1 (168.95.192.1) 56(84) bytes of data.

--- 168.95.192.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms[/COLOR]


then I stop the Mobloquer, and ping 168.95.192.1 again, the output is "0% packet loss" 

[COLOR="Red"]PING 168.95.192.1 (168.95.192.1) 56(84) bytes of data.
64 bytes from 168.95.192.1: icmp_seq=1 ttl=242 time=36.8 ms
64 bytes from 168.95.192.1: icmp_seq=2 ttl=242 time=41.7 ms

--- 168.95.192.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1023ms
rtt min/avg/max/mdev = 36.881/39.335/41.789/2.454 ms[/COLOR]


2. I remove mobloquer and moblock, and then install moblock-nfq, and ping 168.95.192.1 again, the output is "0% packet loss" 


can anyone tell me why this happens? thanks a lot!

---

### Post by jre on 2008-04-03
Same answer as at [phoenixlabs.org:]("http://forums.phoenixlabs.org/showthread.php?p=115207#post115207")

I guess 168.95.192.1 is not present in the single blocklist nipfilter.dat. Explanation: The moblock-nfq package contains MoBlock 0.8 - in this version one single blocklist (nipfilter.dat) from bluetack is used. This list is used as /etc/moblock/ipfilter.dat
The moblock package contains MoBlock 0.9RC2 where a bug relating to the blocklist is fixed. Therefore this version uses multiple lists (see /etc/moblock/blocklists.list). These lists  are used as /etc/moblock/guarding.p2p.

Further mobloquer is only a frontend, but it doesn't affect if moblock is blocking or not.

About the default settings for whitelisted ports: We have discussed this and I came to the following conclusion:
The outgoing port 80 might be used by some other (not webserver) application - therefore there is always a drawback if you open ports. However how big this risk really is is disputed. But it's better to have full protection by default then to just think to have it while some ports are open.
With the GUI mobloquer it is easy to open ports. [I guess you missed to restart MoBlock after you did this whitelisting in mobloquer. Here this function works flawlessly).
Further I plan to make some debconf questions which allow to do some basic configuration during the installation.

---

### Post by chunchengch on 2008-04-03
jre,

Thanks for your explanation, but there are two things I don't understand, would you please explain for me? thanks a lot!

1. when I use moblock package, I have to uncomment WHITE_TCP_OUT="80 443" in  /etc/moblock/moblock.conf , otherwise I can not connect to the internet, but if I use moblock-nfq package, I don't need to uncomment anything in /etc/moblock/moblock.conf.

2. I don't really care if 168.95.192.1 is in the blocklist or not, I just worry about the difference of outputs "100% packet loss" and "0% packet loss", which one is normal when moblock is enabled?

---

### Post by jre on 2008-04-04
answered in the phoenixlabs thread, see link above

greets
jre

---

### Post by jimtb on 2008-04-06
***News update***

Well, due to the fact that as I student my free time is limited at the moment, I haven't been able to do much. However, I almost finished the "Remove IPs" dialog. I don't think that I will be able to add a diagnostics dialog before releasing 0.5, so I guess that this will have to wait until 0.6. I want however to try to use separate threads in some occasions, especially when executing commands, so that the main program doesn't have to stop working when these tasks need to be executed. If and when I manage to do this, I'll release 0.5.  

Here's a screenshot of the new dialog:
[[IMG]http://img169.imageshack.us/img169/3396/screenshotremoveipsmo1.th.png[/IMG]](http://img169.imageshack.us/my.php?image=screenshotremoveipsmo1.png)

:-)

---

### Post by jimtb on 2008-04-10
**Multithreading support has been added** in all parts of Mobloquer in the latest svn revision. The GUI no longer freezes when executing shell commands, such as when saving settings, resolving hostnames etc. 
I just finished coding this and I didn't even have time to test it long enough but it seems to be working pretty good. Report any bugs you find either here or at the sourceforge.net page.

Hope you like it!

:-)

---

### Post by jimtb on 2008-04-24
After about one month of development, **mobloquer 0.5** is finally here! 

This new release brings some really important features I've been planning since I starting creating the program such as the new dialogs which allow the user to easily whitelist IPs through the GUI or remove specific entries from the blockliss. 

This is also the first version of mobloquer to have multithreading support. As the program now uses separate threads to execute shell commands the user interface will still remain responsive when these commands are being executed.

_**Changelog**_
[I]**ADDED:** Multithreading support. From now on, when mobloquer executes a shell command it uses a separate thread to do so. As a result the GUI will no longer freeze when doing specific tasks such as saving the settings or resolving a host.
**ADDED:** "WhiteList IPs" dialog which allows the user to easily add IP addresses/ranges or hostnames into the whitelist or remove any whitelisted entry.
**ADDED:** "Remove IPs" dialog which allows the user remove IP ranges with specific names/addresses from the blocklist.
**ADDED:** The ability change the default front-end for sudo through the GUI.
**FIXED:** Improvements in the way the program reacts when various tasks are taking place. When moblock-control executes a task the widgets which allow the user to change settings will be temporarily disabled and vice versa.
**FIXED:** Improved documentation withing the program to help new users understand what each option does.
**FIXED:** Reduced CPU usage by changing the way mobloquer checks if the moblock daemon is running.
**FIXED:** Changed the date's format in the moblock-control log to be easier to read.
**FIXED:** A bug which caused moblock log entries containing the pipe character in their "name" section to be ignored.[/I]

---

### Post by SZF2001 on 2008-04-26
> **jimtb said:**
> After about one month of development, **mobloquer 0.5** is finally here! 

This new release brings some really important features I've been planning since I starting creating the program such as the new dialogs which allow the user to easily whitelist IPs through the GUI or remove specific entries from the blockliss. 

This is also the first version of mobloquer to have multithreading support. As the program now uses separate threads to execute shell commands the user interface will still remain responsive when these commands are being executed.

_**Changelog**_
[I]**ADDED:** Multithreading support. From now on, when mobloquer executes a shell command it uses a separate thread to do so. As a result the GUI will no longer freeze when doing specific tasks such as saving the settings or resolving a host.
**ADDED:** "WhiteList IPs" dialog which allows the user to easily add IP addresses/ranges or hostnames into the whitelist or remove any whitelisted entry.
**ADDED:** "Remove IPs" dialog which allows the user remove IP ranges with specific names/addresses from the blocklist.
**ADDED:** The ability change the default front-end for sudo through the GUI.
**FIXED:** Improvements in the way the program reacts when various tasks are taking place. When moblock-control executes a task the widgets which allow the user to change settings will be temporarily disabled and vice versa.
**FIXED:** Improved documentation withing the program to help new users understand what each option does.
**FIXED:** Reduced CPU usage by changing the way mobloquer checks if the moblock daemon is running.
**FIXED:** Changed the date's format in the moblock-control log to be easier to read.
**FIXED:** A bug which caused moblock log entries containing the pipe character in their "name" section to be ignored.[/I]

\\:D/

Sorry to be a dick, but will jre update this or is this not stable? Either way I can only anticipate the fixes and such. Oh happy day!

---

### Post by jre on 2008-04-28
> **SZF2001 said:**
> but will jre update this or is this not stable? Either way I can only anticipate the fixes and such. Oh happy day!

Yes, but you have to wait some time. I'm currently setting up my new amd64 laptop ;-)
So the new mobloquer will be available as i386 and amd64.

---

### Post by jimtb on 2008-05-10
**News update** from [moblock-deb.sourceforge.net]("http://moblock-deb.sourceforge.net/"):
> 
**Repository redesigned, amd64 packages added**
Yay, now I can build amd64 packages natively and test them myself. So here you go, get i386 or amd64 packages from moblock-deb.sf.net.
I used this occasion to also make a software change: Now the repository is made with reprepro instead of debarchiver. Therefore the repository now finally has the pool structure (no changes needed on your side). The packages are still built with cowbuilder (i386 is emulated, for Debian Etch and Ubuntu Feisty i386 packages I have to use pbuilder). Because Debian Sid failed to bootstrap I use the Lenny packages there, too. At least currently the dependencies are satisfied on both dists.
**New MoBlock (0.8-41 and 0.9~rc2-11) and *mobloquer (0.5-1)* packages**
Only minor changes with MoBlock but really nice upstream changes with mobloquer - get it!

:-)

---

### Post by baudelaire on 2008-06-26
How exactly do I prevent Mobloqer from popping up when I log in?  Is there a way to quiet it so that it just appears in the system tray?

---

### Post by jre on 2008-06-27
> **baudelaire said:**
> How exactly do I prevent Mobloqer from popping up when I log in?  Is there a way to quiet it so that it just appears in the system tray?

I think the answer is in this post: [http://ubuntuforums.org/showpost.php?p=4460380&postcount=8](http://ubuntuforums.org/showpost.php?p=4460380&postcount=8)

---

### Post by tenjin1 on 2008-07-11
> **czer323 said:**
> The default block lists added by moblock are paranoid and block practically everything.

I agree. This is probably the main reason over all the users who complain about errors and internet being blocked upon first installation of the program. I think that by default there should only be 3-4 blocklists and the option to uncomment/add the others if paranoid. But to include ALL the major blocklists by default doesn't seem logical.

Great program BTW!

---

### Post by zackiv31 on 2008-07-16
Recently my mobloquer got updated.. and ever since... nothing is showing up in the whitelist IP's section... I try to add things, and it prompts and they never show up (and the IP's are still getting blocked).

What's going on?

I tried uninstall mobloquer, moblock, and iptables --flush...

And then a reinstall... still whitelists refuse to work... what can i do?

Mobloquer 0.5

---

### Post by jre on 2008-07-17
Fixed in moblock 0.9~rc2-14. I'm just doing the upload.
Note that your problem origined by a update of "moblock", not "mobloquer". 

To solve it manually you have to readd the lines
```
WHITE_IP_IN=""
WHITE_IP_OUT=""
WHITE_IP_FORWARD=""
```
to /etc/moblock/moblock.conf.

You can also use the new allow list (/etc/moblock/allow.p2p) instead. This will completely replace the WHITE_IP_ entries some day.

Greets
jre

---

