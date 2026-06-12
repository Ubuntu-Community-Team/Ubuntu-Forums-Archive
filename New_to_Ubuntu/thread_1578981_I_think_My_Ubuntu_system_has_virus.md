---
title: "I think My Ubuntu system has virus"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by gauravbutola on 2010-09-21
Not too sure though. But lately my system (Ubuntu 10.04) is not running as expected.

My mouse pointer starts working automatically for few seconds, and I cant control it.
But today it got way too much out of hand. When I booted my computer and touched my mouse, It started working by itself and doing all the weird things by itself. It was opening Banshee and playing songs, switching workspace,Open Nautilus,Right click,even delting my panels and playing around with dockey, scrolling, opening trash and almost took over my system like someone else was using it.

And the clicks were not even random, All the clicks were intended to do some tasks like mentioned above. and doing all the weird stuff that I could not control at all. All I could do was to either use my keyboard (which was suppressed by the mouse clicks) or pull out the wall socket to brutally turn my computer off.
I couldn't work on my computer at all. Right now It seems fine. But it is now quite frequent.

Plz give me some help, what could be causing this problem.

---

### Post by Jazzy_Jeff on 2010-09-21
A ghost maybe...hehe. Sorry, couldn't resist. Have you tried a different mouse to see if your is faulty? Have you unplugged yourself from the internet when it happens to see if it stops? 

Hopefully someone else has more experience with this.

---

### Post by s0rc3r3r on 2010-09-21
just a suggestion.
is it cuz of 'enabling the remote desktop option'?


System->preference->remote desktop?


I dont think there could be chance of any UBUNTU virus doing such stuff.

---

### Post by psycho5 on 2010-09-21
Someone is remotely controlling your desktop, if you use vnc or remote desktop, they might be controlling ur desktop. next time that happens, use ur keyboard and open terminal

alt+f2 > gnome-terminal

then type "users" without quotes in the terminal it'll show u who's logged on

---

### Post by gauravbutola on 2010-09-21
ghost? haha... feels the same :(


No Remote desktop enabled for sure. Its disabled. and I dont think that when I boot up my system the remote desktop will be automatically enabled. and its still disabled.

---

### Post by Calash on 2010-09-21
I am putting my money on a hardware issue.  When it happens try unplugging the mouse and keyboard and see if it stops.

You can also disconnect your networking and see if it stops then.  That would eliminate the remote desktop possibility.

---

### Post by TNT1 on 2010-09-21
> **Calash said:**
> I am putting my money on a hardware issue.  When it happens try unplugging the mouse and keyboard and see if it stops.

.

Wouldn't a hardware issue be slightly more random than the OP suggests? I'd say his system is compromised.

---

### Post by eriktheblu on 2010-09-21
Do you use a wireless mouse?
Do you have a wireless interface connected?
Do you have a roommate with a wireless mouse and a sense of humor?

---

### Post by gauravbutola on 2010-09-21
> **eriktheblu said:**
> Do you use a wireless mouse?
Do you have a wireless interface connected?
Do you have a roommate with a wireless mouse and a sense of humor?

No wireless mouse.
I am on Dial Up network.
I am the only one in the room right now, no wireless mouse around.

disconnected internet but the problem still persists. It also happens at the login screen. the mouse keeps moving and clicking around.

Argh... its so insane. I dont want to screw my ubuntu as it is the only operating system I use on my computer.

---

### Post by gauravbutola on 2010-09-21
> **Calash said:**
> I am putting my money on a hardware issue.  When it happens try unplugging the mouse and keyboard and see if it stops.

You can also disconnect your networking and see if it stops then.  That would eliminate the remote desktop possibility.

unplugged mouse and key board, disconnected networking and problem is still there.

---

### Post by JamButty on 2010-09-21
I've never heard of any virus on any OS behaving as you describe, even setting aside the rarity of any type of virus on Linux based OSs. That seems the least likely explanation. I have had both keyboard and mouse sticking problems that have performed amazing ballets of undesired activity. Humans have a habit  of seeing patterns and intention where none exist, so I also  wondered how so much activity can happen accidentally, but in every case, that has turned out to be the culprit.

---

### Post by Calash on 2010-09-21
> **gauravbutola said:**
> unplugged mouse and key board, disconnected networking and problem is still there.

Well, that is interesting.  Does it do the same thing if you boot to the Live CD?

Is this a Laptop?  If so can you disable the trackpad and see if the problem continues?

Is there a practical joker in the house that has some basic computer skills?

What you are describing does not fit any virus I have ever heard of.

---

### Post by gauravbutola on 2010-09-21
> **Calash said:**
> Well, that is interesting.  Does it do the same thing if you boot to the Live CD?

Is this a Laptop?  If so can you disable the trackpad and see if the problem continues?

Is there a practical joker in the house that has some basic computer skills?

What you are describing does not fit any virus I have ever heard of.

No, I am on Desktop, 
OK booted with live cd. everything works fine there.
As I said, I am the only one in the room right now...

---

### Post by JKyleOKC on 2010-09-21
> **gauravbutola said:**
> OK booted with live cd. everything works fine there.That pretty well rules out hardware problems, so not very many possibilities remain.

Not to feed any paranoia, but it's possible for an intruder to modify a system so that you cannot detect his presence. If something of this sort has happened to you, the remote desktop capability could be active even though it appears to be turned off when you check. However you ruled that out when it persisted even after you disconnected the network...

The simplest solution is to back up all your irreplaceable data, then reformat the system and reinstall everything. My best guess is that some critical system file (or files) has become corrupted, but tracking down exactly which are involved could take months and you would never know for certain that all the problems had been corrected!

---

### Post by gauravbutola on 2010-09-21
> **JKyleOKC said:**
> That pretty well rules out hardware problems, so not very many possibilities remain.

Not to feed any paranoia, but it's possible for an intruder to modify a system so that you cannot detect his presence. If something of this sort has happened to you, the remote desktop capability could be active even though it appears to be turned off when you check. However you ruled that out when it persisted even after you disconnected the network...

The simplest solution is to back up all your irreplaceable data, then reformat the system and reinstall everything. My best guess is that some critical system file (or files) has become corrupted, but tracking down exactly which are involved could take months and you would never know for certain that all the problems had been corrected!

I think I have to get maverick now.... I cant live with this problem. 

Thanks everybody for the help. I have never seen such problem ever in my life. I was even trying to get access to RecordMyDesktop to show the nuisance it created but as I said the clicks were surpassing the keystrokes.

I think all possible measures have been thought about and I have to finally go with the reinstall and I choose Maverick :) for that...

Thanks all

---

### Post by adit on 2010-09-21
> "Is there a practical joker in the house that has some basic computer skills?"

Most likely.
Someone in your house (maybe your friend) has written a shell script to do these things.

---

### Post by endotherm on 2010-09-21
I vote for prankster. why would malware ever move a mouse, or really do much of anything with the ui?

---

### Post by JKyleOKC on 2010-09-21
> **gauravbutola said:**
> I think all possible measures have been thought about and I have to finally go with the reinstall and I choose Maverick :) for that...

Thanks allNote that Maverick still isn't final, and the last few weeks before release are normally when the nastiest bugs crawl out in a new release. If you depend on your system, you'll be better off to re-install the version you now have, from the live CD, and then replace it with Maverick sometime in December or January after all the usual early problems have been found and fixed...

---

### Post by Calash on 2010-09-21
> **gauravbutola said:**
> I think I have to get maverick now.... I cant live with this problem. 

Thanks everybody for the help. I have never seen such problem ever in my life. I was even trying to get access to RecordMyDesktop to show the nuisance it created but as I said the clicks were surpassing the keystrokes.

I think all possible measures have been thought about and I have to finally go with the reinstall and I choose Maverick :) for that...

Thanks all

Unless you intend to be a beta tester and live with that responsibility I would avoid Maverick until it is released next month.  Stick with 10.04 when you reload.

---

### Post by Jazzy_Jeff on 2010-09-21
If you are going to reinstall and need to back things up use the Live CD to do that. I would also stay with 10.04 for now. Good luck to you.

---

### Post by Spice Weasel on 2010-09-21
e: Never mind. I see you reinstalled, good luck.

---

### Post by arvevans on 2010-09-21
I too found my optical mouse (wired type) to be unstable upon upgrading to 10.04 Ubuntu.  This was partially fixed by changing the surface texture the mouse is running on from vinyl with textured surface to a non-reflective cloth surface mouse pad.  Some of the problem is still there, but not nearly as bad as it was with the shiny textured vinyl desktop surface.  In my case it seems that LCD screen scan is being reflected off the vinyl surface and picked up by the mouse.  Setting an optical barrier (a box of tissues) between screen and mouse also stops most of the problem.

When I boot to older versions of Ubuntu this problem is not there, so I'm guessing that something may have changed in how the mouse is scanned in the 10.04 release.

---

### Post by -kg- on 2010-09-21
I think adit hit the closest, IMO:

> **adit said:**
> Most likely.
Someone in your house (maybe your friend) has written a shell script to do these things.

The second I read the symptoms in your OP, that was what came to mind...a script written to simulate mouse movements and events AND, considering it only happens sometimes, the script is run as a CRON job.

If I'm not mistaken, Ubuntu has a facility to record mouse movements and keyboard inputs, just like Windows does (I can't remember if it's a GUI).  One could use this to generate movements like you describe and run it occasionally with CRON.

---

### Post by KegHead on 2010-09-21
Hey -kg..

I live in Alton.

Good to have someone close by for help!

Is there an Ubuntu users group close by?

KegHead

---

### Post by Rubi1200 on 2010-09-21
> **-kg- said:**
> I think adit hit the closest, IMO:



The second I read the symptoms in your OP, that was what came to mind...a script written to simulate mouse movements and events AND, considering it only happens sometimes, the script is run as a CRON job.

If I'm not mistaken, Ubuntu has a facility to record mouse movements and keyboard inputs, just like Windows does (I can't remember if it's a GUI).  One could use this to generate movements like you describe and run it occasionally with CRON.
If this is the case, then the OP needs to start investigating and doing some damage control.

---

