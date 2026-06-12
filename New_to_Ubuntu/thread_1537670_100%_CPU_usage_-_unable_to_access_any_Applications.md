---
title: "100% CPU usage - unable to access any Applications"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by elasticsoul on 2010-07-23
Hi all,

I'm really trying to like Ubuntu, but....arrgh. 

I was connected all day at work with a wired ethernet cable, and could do pretty much whatever I wanted. Here's the sequence of events that has me now nearly locked out of the computer: 

While connected via ethernet cable:

[LIST=1]
[*]I installed WICD (because Network Manager cannot connect to my home network)
[*]I set up Evolution to d/l my gmail, but then had to stop that because it wanted to download all my gmail
[*]I was able to generally play around in Ubuntu
[/LIST]
I disconnected, left work, am on a ferry with wireless:

[LIST=1]
[*]I connected via WICD to the online wireless; I disabled Network Manager wireless
[*]Every time I click Applications, the HD light comes on continuously, active applications are disabled, and the screen 'resets'
[*]I can only run Firefox because it has an icon outside of applications
[*]When I run System >  Administration > System Monitor, CPU usage is 100% continuously
[*]If I click Process to try and see what is using all this CPU, again with screen reset, which closes System Monitor
[/LIST]
Does anyone have any ideas what's going on? I can't run any applications at all.

---

### Post by Ozymandias_117 on 2010-07-23
It sounds like you're not able to find out what is using all your CPU through System Monitor? If so, try opening a terminal (alt + f2 will pull up a Run Dialog box, type in "gnome-terminal") and use the command ```
top
``` to find out what's using it all. Then you can use ```
kilall -9 prog_name
``` to kill it. Then let us know what's using it and we may be able to offer a suggestion.

---

### Post by elasticsoul on 2010-07-24
Exact same problem when I fit Alt-F2: HD light comes on for ~30s solid, I can't do anything with it, then the Run Dialog box closes.

EDIT: If this were Windows, I'd consider this could be a virus. Every time I try to run something from the Applications menu, crash. If I bypass the Applications menu and use Alt-F2, crash. If I try to find out what program is causing the problem vis System > Administration > System Monitor > Process, crash. But this is Ubuntu. So instead, it is beginning to sound like, and I REALLY hate to say this, but it presents as a flaky, unreliable, buggy OS.

BTW: Right now, connected by wire to the network, CPU is ~35%, swap is 0.0%. So I was, for the first time, able to check processes:

* Gnome system monitor 15-40%
* Gwibber 0-100%

A couple other things under 3%

---

### Post by QIII on 2010-07-24
System Monitor is hungry, so that usage might not be abnormal.

Gwibber's CPU usage is disconcerting.  Do you use Gwibber?  I don't,  personally, but I know there was a lot of complaining about it on the  forum for some time.  I don't know if that has been resolved.

When was the last time you updated?  Do you have Gwibber set to run at startup?  Gwibber and Facebook?

[https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/451360](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/451360)

---

### Post by Sir Jasper on 2010-07-24
Hi,

Gwibber (use the searchbox above) is reported by many forum members as having problems.

My regards

---

