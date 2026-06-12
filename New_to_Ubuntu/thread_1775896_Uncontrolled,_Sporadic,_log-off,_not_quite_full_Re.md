---
title: "Uncontrolled, Sporadic, log-off, not quite full Reboot"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Grendel336 on 2011-06-05
For the past few weeks I've been experiencing a strange issue that never happened before. 

I'll be happily surfing the internet using my older Toshiba laptop, clicking and scrolling about using Chrome, when all of a sudden, without warning the screen will snap to black, then almost act like the computer is rebooting, but almost as fast the log-on screen will appear. 

Once I log back into Natty everything is back to normal as if I've just turned on computer and logged in from a complete shut down. 

I have a dual-boot system with Mint as the other boot option. Never had an issue there. 

I can't tell if there's a sequence of clicking and scrolling that initiates the pseudo-restart or what. The problem never seems to happen when I'm just sitting on one page doing something like writing this post.

But if I wanted to open another tab and go grab a link then come back here and paste it in I might have the situation reappear. Like I'm moving too fast for the system to keep up which then causes a "burp" and a mini-reboot. 

Like I said....it's not a full-on reboot. Just a quick black screen, then the standard log-in screen. 

As I'm reading this I just thought I've not spent any time using Firefox with Natty. Might there be some issue with overworking Chrome?

Any ideas what might be causing this? 

Thanks for any help or suggestions.

---

### Post by wildmanne39 on 2011-06-05
> **Grendel336 said:**
> For the past few weeks I've been experiencing a strange issue that never happened before. 

I'll be happily surfing the internet using my older Toshiba laptop, clicking and scrolling about using Chrome, when all of a sudden, without warning the screen will snap to black, then almost act like the computer is rebooting, but almost as fast the log-on screen will appear. 

Once I log back into Natty everything is back to normal as if I've just turned on computer and logged in from a complete shut down. 

I have a dual-boot system with Mint as the other boot option. Never had an issue there. 

I can't tell if there's a sequence of clicking and scrolling that initiates the pseudo-restart or what. The problem never seems to happen when I'm just sitting on one page doing something like writing this post.

But if I wanted to open another tab and go grab a link then come back here and paste it in I might have the situation reappear. Like I'm moving too fast for the system to keep up which then causes a "burp" and a mini-reboot. 

Like I said....it's not a full-on reboot. Just a quick black screen, then the standard log-in screen. 

As I'm reading this I just thought I've not spent any time using Firefox with Natty. Might there be some issue with overworking Chrome?

Any ideas what might be causing this? 

Thanks for any help or suggestions.
Hi. what is the specs of your system? how old is it? Have you cleaned it out recently, because natty does use a few more resources then previous release and a laptop runs warm anyway. What video card do you have?

---

### Post by Grendel336 on 2011-06-11
I have a:

Toshiba Satellite with an AMD Turion X2 2.00 GHz processor
3 gb ram
ATI RS690M Radeon x1200 series video card

Thanks for helping. 

This issue never happens when using Mint 9. Only when using Ubuntu 11.04 - and only when surfing internet.

---

### Post by VOT Productions on 2011-06-11
Are you running Unity 2D or Unity 3D?

---

### Post by Grendel336 on 2011-06-11
Not sure which Unity I'm using. 

I do know I downloaded the 32 bit version. 

Interestingly, I've just recently switched to Ubuntu Classic in the log-on options, and the computer seems to be running fine right now. 


No issues at all. So far.

---

### Post by VOT Productions on 2011-06-11
Unity 2D - No effects. Usually snappier.
Unity 3D - Eye candy all the way.

If you have unity-2d in synaptic installed, you have Unity 2D. If not, it is Unity 3D, and install Unity 2D.

---

### Post by wildmanne39 on 2011-06-11
> **Grendel336 said:**
> Not sure which Unity I'm using. 

I do know I downloaded the 32 bit version. 

Interestingly, I've just recently switched to Ubuntu Classic in the log-on options, and the computer seems to be running fine right now. 


No issues at all. So far.Hi, a lot of times classic with no efects runs better there is less programs to cause problems and it is easier on resources causes less heat up of computers. The main issue is usually compiz and video card issues.

---

### Post by Grendel336 on 2011-06-12
Problem returned. Using Ubuntu Classic the issue has now come back. Although not as often. 

It is a unwanted "log-off" situation. Not a reboot. 

So what steps do I do to discover the exact "unity" I've installed? 


I originally loaded the beta version and just kept updating as the stable release was introduced. 

I never had this "unwanted log-off" dilemma when using the Beta version. It only surfaced within the last two weeks or so. 


Thanks for the help. I'll be glad to post my unity version once I figure out how to know exactly what I have.

---

### Post by VOT Productions on 2011-06-12
> **Grendel336 said:**
> Problem returned. Using Ubuntu Classic the issue has now come back. Although not as often. 

It is a unwanted "log-off" situation. Not a reboot. 

So what steps do I do to discover the exact "unity" I've installed? 


I originally loaded the beta version and just kept updating as the stable release was introduced. 

I never had this "unwanted log-off" dilemma when using the Beta version. It only surfaced within the last two weeks or so. 


Thanks for the help. I'll be glad to post my unity version once I figure out how to know exactly what I have.

Is your laptop overheating?

---

### Post by Grendel336 on 2011-06-12
Don't know. Would Natty over-heat more often than Mint 9? 

I'm not pushing the laptop by any means. Not a multi-tasking wizard or gamer. Usually just surfing about the internet. 

I don't get the forced log-off when working around trying to find out what version of Unity I'm using. 

Only when clicking through web pages on the internet. 

I sometimes almost feel like the scrolling & clicking almost too fast in sequence might be a contributing factor. 

I'm really trying to pinpoint anything that might be more than just coincidental.

---

### Post by wildmanne39 on 2011-06-12
> **Grendel336 said:**
> Don't know. Would Natty over-heat more often than Mint 9? 

I'm not pushing the laptop by any means. Not a multi-tasking wizard or gamer. Usually just surfing about the internet. 

I don't get the forced log-off when working around trying to find out what version of Unity I'm using. 

Only when clicking through web pages on the internet. 

I sometimes almost feel like the scrolling & clicking almost too fast in sequence might be a contributing factor. 

I'm really trying to pinpoint anything that might be more than just coincidental.
Hi, it is possible your laptop is getting hot, they do run hotter then desktops,I would clean it out and use a chilling pad to keep it cooler. People are also having trouble with chrome causing issues like yours. Unity does run hotter on my desktop when I am watching like hulu shows in full sreec it jumps up 20 degrees. Also after this happens use log viewer and look at your logs and see if you can find what the problem is that way. An easier way is to open the terminal and type in chrome and run it that way and if it closes you will get a list of errors in the terminal of what happened.

---

### Post by Grendel336 on 2011-06-13
Hmm...I spent about 3.5 to 4 hours yesterday with pandora playing while booted into "Ubuntu Classic - no effects" and there was no forced reboot during all that time. Pandora never hickuped at all. 

During this time I was stripping wallpaper, so there was no direct interaction with the computer other than it was running and playing music. 

I honestly think there's a connection between the touchpad and the "mouse" buttons being worked, or overworked when surfing about the internet. 

I'll try to pay attention to temperature and see if there's a connection between the reboots and increased temps. 

Is there a wonderfully simple temperature meter I can use within the Natty applications that will reflect what's going on in my processor? 

Thanks for attempting to figure this out.

---

### Post by wildmanne39 on 2011-06-14
> **Grendel336 said:**
> Hmm...I spent about 3.5 to 4 hours yesterday with pandora playing while booted into "Ubuntu Classic - no effects" and there was no forced reboot during all that time. Pandora never hickuped at all. 

During this time I was stripping wallpaper, so there was no direct interaction with the computer other than it was running and playing music. 

I honestly think there's a connection between the touchpad and the "mouse" buttons being worked, or overworked when surfing about the internet. 

I'll try to pay attention to temperature and see if there's a connection between the reboots and increased temps. 

Is there a wonderfully simple temperature meter I can use within the Natty applications that will reflect what's going on in my processor? 

Thanks for attempting to figure this out.
Hi, I have an applet installed on my awn launcher but it requires the awn launcher to use it, it was easier to set up in gnome2. You can look in synaptic or software center and search for screenlets and see if they are still part of natty if so you can install them and keep an eye on temperature.

---

### Post by bhagwad on 2011-06-22
I have the exact same symptoms. Fooling around in Chromium opening tabs, clicking on links etc, and the BAM - I'm kicked back to the login screen. It's not a reboot. Just as if I logged off.

I have a Sony Vaio, 3GB memory, dual core and the usage is hardly intense. I'm pretty sure it's not a hardware issue.

It bugs me because I sometimes lose my work. It seem pretty random (though obviously there has to be a reason why it happens at that particular moment...)

---

### Post by wildmanne39 on 2011-06-22
> **bhagwad said:**
> I have the exact same symptoms. Fooling around in Chromium opening tabs, clicking on links etc, and the BAM - I'm kicked back to the login screen. It's not a reboot. Just as if I logged off.

I have a Sony Vaio, 3GB memory, dual core and the usage is hardly intense. I'm pretty sure it's not a hardware issue.

It bugs me because I sometimes lose my work. It seem pretty random (though obviously there has to be a reason why it happens at that particular moment...)Hi, a lot of people have trouble with Chromium, they install chrome instead and it usually fixes the problem.

---

### Post by seanos on 2011-07-14
[Edit: OK...I didn't read this thread very well :oops: - my problem is the Reboot menu option only logging me out, not rebooting]

---

### Post by wildmanne39 on 2011-07-14
> **seanos said:**
> [Edit: OK...I didn't read this thread very well :oops: - my problem is the Reboot menu option only logging me out, not rebooting]Hi, you would be better off starting your own thread with a good title that describes the problem, and include your system specs.

---

### Post by CatKiller on 2011-07-14
> **Grendel336 said:**
> It is a unwanted "log-off" situation. Not a reboot. 

No it's not. It's an X crash.

---

