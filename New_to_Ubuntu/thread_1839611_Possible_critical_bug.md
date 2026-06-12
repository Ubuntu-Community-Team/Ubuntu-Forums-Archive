---
title: "Possible critical bug"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by g33p on 2011-09-05
I think I just found a *bug* in ubuntu 11.04 32bit desktop.
I left my pc on all the night. But lastly, I had right clicked the mouse.
So, when I turned my pc on this morning, I could still see the context menu.
I clicked 'create new folder' by mistake.. and a folder was created and, user was logged out then.
after logging in, the folder was there.
so this is just an info. anyone can take it on from here.
I am sorry if this isn't the right place to post [i seriously doubt it]. But I haven't got much time.
so someone please take it on from now.

---

### Post by axatrikx on 2011-09-06
is it reproducible? 
can u do the same thing again n see it happens?

---

### Post by 3rdalbum on 2011-09-06
Firstly, this definitely isn't the right place for bug reports. You need to report them at [www.launchpad.net](www.launchpad.net) - note that you'll need to register for an account there.

When making the bug report, you should include as much information about your system as possible. Also, it helps developers if you say something like:

> 
What I did:
1. I clicked on x
2. I did y

What I expected to happen:
I expected the window to close.

What actually happened:
I was logged out. The login screen appeared and I was able to log in and continue my work.

It might be a good idea to look up the "ubuntu-bug" command on Ubuntu - it's a way of reporting bugs that automatically attaches system information to your bug report, to help developers work out what has gone wrong.

However, don't bother if you can't reproduce the problem. If you can't make the problem occur again, and tell the developers how to trigger the problem, the developers have no hope of figuring it out. Also, if you can't reproduce the problem, it's probably not going to happen enough to really cause problems for other people.

If you can reproduce the problem, it would probably be worthwhile downloading Ubuntu 11.10 Beta 1 and seeing if the problem is present there too. Most of the development effort goes into the development version, so it's more likely to be fixed in the newer version than in a post-release-update for the old version. Plus, if it's fixed in the new version already, you don't need to report it as a bug.

---

### Post by haqking on 2011-09-06
> **g33p said:**
> I think I just found a *bug* in ubuntu 11.04 32bit desktop.
I left my pc on all the night. But lastly, I had right clicked the mouse.
So, when I turned my pc on this morning, I could still see the context menu.
I clicked 'create new folder' by mistake.. and a folder was created and, user was logged out then.
after logging in, the folder was there.
so this is just an info. anyone can take it on from here.
I am sorry if this isn't the right place to post [i seriously doubt it]. But I haven't got much time.
so someone please take it on from now.


I cant see this as a bug ?

You said you left computer on all night.

Then you say you turned it on in morning ?

Conflict there.

Then you say you had clicked for context menu and was still there and you chose to create a new folder and then it was there after you created it, so that is an action chosen by you and is suppose to happen. ?

Only issue is see is the action logged you out ?

sounds more like a one off if you ask me, if you can reproduce it time and time again then register at [launchpad]("https://launchpad.net/") as shown above and report a bug.

---

### Post by mastablasta on 2011-09-06
> **haqking said:**
>  
You said you left computer on all night.
 
Then you say you turned it on in morning ?
 
Conflict there.
 
.
 
perhaps computer was hibernating in which case it stays loged in i believe.

---

### Post by haqking on 2011-09-06
> **mastablasta said:**
> perhaps computer was hibernating in which case it stays loged in i believe.


oh yeah good point.

Sill dont think it is a bug, needs to reproduce for clarity.

---

### Post by g33p on 2011-09-15
@ALL
sorry about 'turned on my computer in the morning' part.
I actually meant "I left my computer on all night but turned off my monitor. Then, in the morning I turned on the monitor"


And, yes, I can reproduce the "bug":
what I exactly did:
minimize all open windows
right click on desktop
hover on to 'create new folder'
don't disturb the computer till it locks itself.
when the screen has faded to black, just move your mouse just a little bit.
I saw not the unlock screen but the context menu on the desktop.
I clicked the 'create new folder' and then, it was created, and the computer was immediately locked.
I unlocked it, and found the created folder there.

what i expect:
close the context menu and lock screen.

what seems wrong in it?
i created a new folder when i was not supposed to be able to.

---

### Post by Wim Sturkenboom on 2011-09-15
Register on launchpad (if you have not already done so) and report it there. I agree that it is a bug, I however doubt that it will get a high priority as it's reasonably innocent in this case (somebody gets to your PC and can create a directory is not really critical ;))

---

### Post by g33p on 2011-09-15
I have read the guidelines regarding bug submission, and created launchpad account too. But I couldn't decide under what app I have to file this bug
what should i enter for app name while entering ubuntu-bug <appname> in terminal?
Also, recent finding:
this also applies to ubuntu icon on the top left of the screen.
when i click it, (i got a search screen). and I leave it like that, when I come back, it doesn't lock till some time.

@Wim:
yeah on thinking about it again, feels that this isn't critical at all [unless someone could really *exploit* this]

---

### Post by FormatSeize on 2011-09-15
> **g33p said:**
> 
 [unless someone could really *exploit* this]
To do what, exactly? Create a virus that starts if someone right-clicks right before they go to sleep, and have them wake up to a critical mass of "New Folder" icons that causes some sort of disk failure?

---

### Post by SavageWolf on 2011-09-15
If anyone has physical access to your machine while your asleep, chances are they will just steal it (Or just the hard disk).

---

### Post by sanderd17 on 2011-09-15
Most things that require a GUI to work are not dangerous (security-wise), because almost all mission-critical computers don't have a GUI.

So security issues that require a GUI always get a low priority.

---

