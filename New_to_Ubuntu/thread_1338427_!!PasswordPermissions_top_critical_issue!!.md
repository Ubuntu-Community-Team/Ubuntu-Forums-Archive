---
title: "!!Password/Permissions top critical issue!!"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by trypanon on 2009-11-26
it is big doubt whether this question is for beginners, but it is absolutely not for Absolute ones................
so:
[COLOR=Red]_**how to make ubuntu 9.10 insert (system) password into application's prompt automatically, without any human interruption?!?!?!**_[/COLOR]
*to save irrelevant entries, i'll tell you that i need this to let the propriety firewall of my organization start up after reboot ALONE!*

---

### Post by Mr. Devil on 2009-11-26
Add this to /etc/sudoers ( /usr/bin/firewall is just an example ):
```
%admin ALL=NOPASSWD: /usr/bin/firewall

```

Basically, it'll allow launching an application ( sudo <command> ) without the need of password.

---

### Post by Don1500 on 2009-11-26
Are you asking how to start Ubuntu without it asking for a password?

if so just:
System => Administration => Login screen

This will let you set up THIS machine with a normal user, no password on start up, but NOT ROOT ACCESS.

---

### Post by BugBuster on 2009-11-26
Is is absolutely necessary to enter the system password visually?
Or else you could simply add the command to start the firewall into the /etc/rc.local file.

All commands in this file are executed with root (system) privileges.

Hope I have understood your query correctly.

---

### Post by trypanon on 2009-11-26
> **BugBuster said:**
> Is is absolutely necessary to enter the system password visually?
Or else you could simply add the command to start the firewall into the /etc/rc.local file.

All commands in this file are executed with root (system) privileges.

Hope I have understood your query correctly.
****
[COLOR=Lime]
BB[/COLOR], it is totally unnecessary to observe who/how/when is inserting the [SIZE=2]*passwd*[/SIZE], the point is that it has to be somehow inserted...
there's several ways to manage startup of apps i'm familiar with:
1- through application itself, modifying its preferences (or its system files) - in my case not applicable, as it has no even similar options;
2- creating insane-perverted batch, which is making everything (incl. blowjob) alone - too crazy & devours resources;
3- adding/changing ***sudoers*** content - useful, but doesn't want to work in my case (i'm already getting out of my mind!). maybe [COLOR=Cyan]mr.Devil[/COLOR] will be so kind to tell me exact syntax for 9.10's ***sudoers***, meaning where & hot should it be written;
4- checking "V" (or "X") in *[SIZE=2]system-->preferences-->startup_apps[/SIZE]-->YOUR_ENTRY* - here, i think i have to work around!!! in this case, there is a prompt to insert (regular system) [SIZE=2]*passwd*[/SIZE], even though this system is set to login silently. system, but not its applications...
so there is kind of reaction of the application, & i think some kind of command string must be invented for this startup entry. i tried few variations - all were worthless. the last one looked like [B][COLOR=Blue][U][SIZE=2]sudo alltray -stask su-to-root -X -c /usr/sbin/MY_APP.
[/SIZE][/U][/COLOR][/B][COLOR=Blue][SIZE=2][COLOR=Black][SIZE=1]it works if i'm making the launcher with this string - app starts directly into the tray without password or anything else. but not on the boot...
ANY IDEAS, MIGHTY GENIUSES? :)
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by JKyleOKC on 2009-11-26
If you can launch the application from the command line, BugBuster gave you the answer: put that command, less the "sudo" prefix, into the "/etc/rc.local" file just in front of the existing "exit 0" line.

The rc.local file is always executed as the very last step of the boot process, and it executes with root privilege so does not need the password (the password prompt comes from sudo, not from the application itself). This will make things totally automatic as you desire.

If necessary, you can add a line "sleep 5" just in front of your new command to make the boot process wait 5 seconds, should it be necessary to make the firewall load properly. You could use 60 instead of 5, if you wanted to make it wait a full minute. However for most programs "sleep 2" is perfectly adequate, and it's likely that you won't need to slow things down at all...

---

### Post by harfa on 2009-11-26
if its a "top critical issue!!11!" how about you go get some paid support for your organization? 
this is a volunteer forum, your problem is no more important than anyone elses.

---

### Post by trypanon on 2009-11-26
JKyleOKC, thanx a lot! it sounds like smth making sence :) i'll try it just in the morning... in 3 more hours - never sleeping in the name of business, security ](*,)[-(#-o & ... money.;) 
THUS.....

[B][COLOR=Purple]> **harfa said:**
> if its a "top critical issue!!11!" how about you go get some paid support for your organization? 
this is a volunteer forum, your problem is no more important than anyone elses.[/COLOR][/B]  

i can not understand what this post supposed to highlight? if i seemed to you over-worried, so it is just due to whole_week_long_multitasking..... i'm sorry for bringing my rush to the forum.
but if dear harfa meant smth different, i'd recommend him to wipe this post, drink some venom, & keep inspecting the forum loosing the time when he could learn some new stuff...

---

