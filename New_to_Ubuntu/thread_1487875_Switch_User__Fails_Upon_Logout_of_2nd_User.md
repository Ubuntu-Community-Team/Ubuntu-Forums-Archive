---
title: "Switch User  Fails Upon Logout of 2nd User"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by GregA on 2010-05-19
Just checking to see if anyone else is seeing this issue with Lucid . . when the 1st user switches to a second user, the second user session works fine, . . . but, after the second user "logs out",  the screen that's presented is blank (no cursors, no gui, etc. - - just a black/blank screen).

Is there a way to get the gui back, or even a command line session, without going through a full hardware-shutdown and restart???

By the way, that hardware shutdown also creates a host of other problems with the system, such as hangup with the "power mgmt" application, and mount issues with peripheral USB drives etc.

The method (or workaround) I used to get the system back to normal was to pull out all usb sticks, media players, etc., then hot-plug each so the system registers the devices, then doing a full "soft" shut-down - - waiting a couple minutes, and restarting the PC.  

Also, as info, the above problem can be prevented by user1 "logging out", and then user 2 logging in the normal way.  

Your thoughts appreciated.

*********************************************************

Note:  my PC is an older, desktop (HP A250N), 512 mb ram, on board nvidia nForce2, pretty vanilla with an HPf1905 lcd monitor.

---

### Post by Oilarrak on 2010-05-21
I am experiencing the same problem. I read it had to do with gnome-screensaver and that installing instead xscreensaver should fix it, but in my hands it didn't. 
I have just come across this other "solution"

[http://chanflee.com/?p=1682](http://chanflee.com/?p=1682)

But I haven't had time to reach home and test it. I don't plan to do it in the next 5 to 6 hours:(. You are welcome to try first :P.

Hope this helps,

O.

---

### Post by louieb on 2010-05-21
Same problem here.  I use Ctrl+Alt+F1 - that opens tty1 - you can then login and  restart X. 

```
sudo service gdm restart
```

that will get you back to the login screen. 

or shutdown from there

```
sudo shutdown -h now 
```

---

### Post by bodhi.zazen on 2010-05-21
I ran into this with gallium

At the blank screen you can enter the password of the second user and log back in.

When you switch users, log out of the second account rather then switch user back to the first. 

I know it is not the way it should work, but better then restarting GDM =)

Has anyone filed a bug report yet ?

---

### Post by louieb on 2010-05-21
> **bodhi.zazen said:**
> ...At the blank screen you can enter the password of the second user and log back in...

Tried that ... cursor changes to a circle for a moment - goes back to an arrow but the rest of screen remains black. 

> When you switch users, log out of the second account rather then switch  user back to the first. 

When I logout of the 2nd account thats when the screen goes black - with just a cursor.  Same thing  happens sporadically  when using the fast user switch to change user. 

The way I have found to switch users successfully - use the finger command to find which tty session the users are logged into - then use Ctrl+Alt+F# to  switch back and forth.       
> Has anyone filed a bug report yet ? 	

Did a search of  [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")  for "user switcher"  - 79 hits - none were a good match. 

This has been an off and on problem Some releases worked correctly for me (Hardy and Jaunty did work).   Some of the others - (Karmic) have the same problem. 

@Oilarrak - If that fix works - would you mind translating?

---

### Post by bodhi.zazen on 2010-05-21
> **louieb said:**
> Tried that ... cursor changes to a circle for a moment - goes back to an arrow but the rest of screen remains black. 



When I logout of the 2nd account thats when the screen goes black - with just a cursor.  Same thing  happens sporadically  when using the fast user switch to change user. 

The way I have found to switch users successfully - use the finger command to find which tty session the users are logged into - then use Ctrl+Alt+F# to  switch back and forth.       


Did a search of  [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")  for "user switcher"  - 79 hits - none were a good match. 

This has been an off and on problem Some releases worked correctly for me (Hardy and Jaunty did work).   Some of the others - (Karmic) have the same problem. 

@Oilarrak - If that fix works - would you mind translating?

Now that sounds painful =(

I think the suggestion in the linked blog is to use xscreensaver rather then gnome-screensaver.

I will at least try that.

---

### Post by memphisrich on 2010-07-01
This happens 2 different ways on my system (amd64 k8tneo from 2004). Sometimes I get a washed out looking fuzzy screen upon pressing logout of 2nd user. In this case, I can ctl-alt-f1 and get to a console. Then, ctl-alt-f7 shows a console with info that I haven't copied or noted yet. Ctl-alt-f8, takes to a restored login x console.
Other times, after pressing logout, I get a completely blank screen, no cursor, no nothing. The monitor has a feed, because it doesn't go blank, but no display is shown. No input is accepted via keyboard, so the only thing left to do is hard-shutdown, which sucks.

This problem is similar to Bug532047, so I tried the fix to rename plymouth-splash.conf, but it had no effect. I have not tried to switch to xscreensaver, because this happens whether a screensaver has been active or not.

I am running Lucid, but original upgrade from alternate failed, so I formatted root drive with ext3, and did a fresh installation, keeping the old info on my /home and /backup partitions. After adding the users back in, this has been fairly seamless except for the logout issue.

Here are the relevant logs from logviewer clipped at the last time this happened:

daemon.log
Jul  1 16:59:26 biglebowski console-kit-daemon[806]: WARNING: Couldn't read /proc/1771/environ: Failed to open file '/proc/1771/environ': No such file or directory
Jul  1 16:59:26 biglebowski gdm-simple-slave[2409]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul  1 16:59:26 biglebowski acpid: client 1021[0:0] has disconnected
Jul  1 16:59:26 biglebowski acpid: client 1021[0:0] has disconnected
Jul  1 16:59:26 biglebowski acpid: client connected from 2411[0:0]
Jul  1 16:59:26 biglebowski acpid: 1 client rule loaded
Jul  1 16:59:26 biglebowski acpid: client connected from 2411[0:0]
Jul  1 16:59:26 biglebowski acpid: 1 client rule loaded


messages:
Jul  1 16:59:26 biglebowski kernel: [ 1060.825645] __ratelimit: 3 callbacks suppressed
Jul  1 16:59:26 biglebowski kernel: [ 1060.825658] python[1778]: segfault at 21 ip 0000000000000021 sp 00007fffee72ddb8 error 14 in python2.6[400000+21c000]

auth.log
Jul  1 16:59:26 biglebowski gdm-session-worker[1377]: pam_unix(gdm:session): session closed for user rich
Jul  1 16:59:26 biglebowski polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.41, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)

kern.log
Jul  1 16:59:26 biglebowski kernel: [ 1060.825645] __ratelimit: 3 callbacks suppressed
Jul  1 16:59:26 biglebowski kernel: [ 1060.825658] python[1778]: segfault at 21 ip 0000000000000021 sp 00007fffee72ddb8 error 14 in python2.6[400000+21c000]
Jul  1 16:59:34 biglebowski kernel: [ 1069.750024] NVRM: Xid (0001:00): 8, Channel 00000000
Jul  1 16:59:35 biglebowski kernel: [ 1070.750023] NVRM: Xid (0001:00): 16, Head 00000000 Count 0001e0e2
Jul  1 16:59:42 biglebowski kernel: [ 1077.750021] NVRM: Xid (0001:00): 8, Channel 0000001e
Jul  1 16:59:43 biglebowski kernel: [ 1078.750013] NVRM: Xid (0001:00): 16, Head 00000000 Count 0001e0e3

Hopefully, there is enough info here that someone can figure out what is causing this.

---

### Post by bodhi.zazen on 2010-07-01
> **memphisrich said:**
> This happens 2 different ways on my system (amd64 k8tneo from 2004). Sometimes I get a washed out looking fuzzy screen upon pressing logout of 2nd user. In this case, I can ctl-alt-f1 and get to a console. Then, ctl-alt-f7 shows a console with info that I haven't copied or noted yet. Ctl-alt-f8, takes to a restored login x console.
Other times, after pressing logout, I get a completely blank screen, no cursor, no nothing. The monitor has a feed, because it doesn't go blank, but no display is shown. No input is accepted via keyboard, so the only thing left to do is hard-shutdown, which sucks.

This problem is similar to Bug532047, so I tried the fix to rename plymouth-splash.conf, but it had no effect. I have not tried to switch to xscreensaver, because this happens whether a screensaver has been active or not.

I am running Lucid, but original upgrade from alternate failed, so I formatted root drive with ext3, and did a fresh installation, keeping the old info on my /home and /backup partitions. After adding the users back in, this has been fairly seamless except for the logout issue.

Here are the relevant logs from logviewer clipped at the last time this happened:

daemon.log
Jul  1 16:59:26 biglebowski console-kit-daemon[806]: WARNING: Couldn't read /proc/1771/environ: Failed to open file '/proc/1771/environ': No such file or directory
Jul  1 16:59:26 biglebowski gdm-simple-slave[2409]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jul  1 16:59:26 biglebowski acpid: client 1021[0:0] has disconnected
Jul  1 16:59:26 biglebowski acpid: client 1021[0:0] has disconnected
Jul  1 16:59:26 biglebowski acpid: client connected from 2411[0:0]
Jul  1 16:59:26 biglebowski acpid: 1 client rule loaded
Jul  1 16:59:26 biglebowski acpid: client connected from 2411[0:0]
Jul  1 16:59:26 biglebowski acpid: 1 client rule loaded


messages:
Jul  1 16:59:26 biglebowski kernel: [ 1060.825645] __ratelimit: 3 callbacks suppressed
Jul  1 16:59:26 biglebowski kernel: [ 1060.825658] python[1778]: segfault at 21 ip 0000000000000021 sp 00007fffee72ddb8 error 14 in python2.6[400000+21c000]

auth.log
Jul  1 16:59:26 biglebowski gdm-session-worker[1377]: pam_unix(gdm:session): session closed for user rich
Jul  1 16:59:26 biglebowski polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.41, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)

kern.log
Jul  1 16:59:26 biglebowski kernel: [ 1060.825645] __ratelimit: 3 callbacks suppressed
Jul  1 16:59:26 biglebowski kernel: [ 1060.825658] python[1778]: segfault at 21 ip 0000000000000021 sp 00007fffee72ddb8 error 14 in python2.6[400000+21c000]
Jul  1 16:59:34 biglebowski kernel: [ 1069.750024] NVRM: Xid (0001:00): 8, Channel 00000000
Jul  1 16:59:35 biglebowski kernel: [ 1070.750023] NVRM: Xid (0001:00): 16, Head 00000000 Count 0001e0e2
Jul  1 16:59:42 biglebowski kernel: [ 1077.750021] NVRM: Xid (0001:00): 8, Channel 0000001e
Jul  1 16:59:43 biglebowski kernel: [ 1078.750013] NVRM: Xid (0001:00): 16, Head 00000000 Count 0001e0e3

Hopefully, there is enough info here that someone can figure out what is causing this.

Thank you for posting that information.

May I suggest you file a bug report on Launchpad ? I would file it against GDM .

---

### Post by louieb on 2010-07-03
It appears to me some work to fix is being done. Had the problem on both laptop and desktop. Logging off the 2nd user now works as expected on the laptop. Now only the desktop is affected.  

Not much difference between the two installs - no 3rd party software yet - oh well.

---

### Post by e.meitner on 2010-10-27
You may want to take a look at this bug report and click "Does this bug  affects you" if you can reproduce it as described in the bug  description.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011)

---

### Post by bodhi.zazen on 2010-10-27
> **e.meitner said:**
> You may want to take a look at this bug report and click "Does this bug  affects you" if you can reproduce it as described in the bug  description.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/40011)

Wow, that is a very old bug report. I would almost suggest opening a new one as was mentioned earlier in the report the upstream code has significantly changed since dapper and I doubt that old bug report will get much attention.

---

