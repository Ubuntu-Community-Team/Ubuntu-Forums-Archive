---
title: "How to fix widgets in Kubuntu?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by maneesh77 on 2010-04-28
First time to try Kubuntu.

Kubuntu 10.04

My problem is that whenever I try to move widgets to the place on the desktop I want to put them, they all come bunching back to the center/ their original position. If I lock widgets they all lock, not just the one I moved, and can't be moved to the place I want them to go. 

Really frustrated with KDE, since its completely new to me and widgets was the first time I tried to play with. 

Any ideas on how to make widgets stay where I place them on the desktop and not move by themselves to the center

---

### Post by jkxx on 2010-04-28
Are the widgets moving back to the center right away or after you run any apps/leave KDE?

One thing to check for is in the control panel (System Settings), then Desktop, then Workspace. Make sure the Dashboard is set to 'Show desktop widgets' although it should be already.

Sometimes the theme can influence how widgets behave too so the problem might go away if you change your desktop theme. You can do this through System Settings, then Appearance, then Style, then Workspace tab. Once you do change it, log out and then back in to see what you actually did since some changes don't manifest right away.

---

### Post by maneesh77 on 2010-04-28
> **jkxx said:**
> Are the widgets moving back to the center right away or after you run any apps/leave KDE?

One thing to check for is in the control panel (System Settings), then Desktop, then Workspace. Make sure the Dashboard is set to 'Show desktop widgets' although it should be already.

Sometimes the theme can influence how widgets behave too so the problem might go away if you change your desktop theme. You can do this through System Settings, then Appearance, then Style, then Workspace tab. Once you do change it, log out and then back in to see what you actually did since some changes don't manifest right away.

The widgets move back when I try to change the position of another widget. Desktop widgets is active and it is the original theme

---

### Post by charlesC on 2010-05-04
Yes, I have this problem too.

Every time I move a widget or shortcut on the desktop, it waits a second then jumps back to its original position.

Rather frustrating!

---

### Post by adajar99 on 2010-05-09
Is there a solution to this?  I agree, this is really frustrating.  People have been raving about how good Lucid is, but we have a very obvious bug that was not caught before the release. And to think this is a much-awaited LTS...

---

### Post by Zorael on 2010-05-10
A quick question. Do you have icons on your desktop? If you right-click the empty desktop and pick Desktop Activity Settings, and then pick the Activity section, is the Type set to Folder View?

A Folder View activity behaves like a traditional desktop does, in that it houses icons and not much else. I don't think you *can* put any other widgets into it, in which case what's happening is that Plasma notices that you're trying to do just that, and rolls back to the state things were in before you started dragging.

What you need to do (if it is indeed a Folder View) is to set the activity type to Desktop. If you want icons, you can add a separate Folder View widget and point it to, say, your **~/Desktop** folder.

*Then* you should be able to drag other widgets onto it, and/or create new ones in it.

---

### Post by ankspo71 on 2010-05-10
Hi,
It was happening to me too, but it went away after installing the Nvidia proprietary driver. Maybe it is somehow connected with the neauvou driver? Whatever was causing it, it seemed like KDE was failing to rewrite the new locations of the widgets. I use folder view by the way.

---

### Post by bvitnik on 2010-05-10
Is this your bug?

[http://www.youtube.com/watch?v=_b3TuEECXyg]("http://www.youtube.com/watch?v=_b3TuEECXyg")

If that is your bug, leave some comment at Ubuntu Launchpad confirming the bug. Maybe then it will get some attention (it badly needs :) ).

Launchpad bug report -> [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/569877](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/569877)

---

### Post by adajar99 on 2010-05-11
Hi Bojan (this is you, bvitnik, right?),

Thank you!  Checked out the link you provided, followed your workaround (restarted plasma), the issue was solved.

---

### Post by bvitnik on 2010-05-12
> **adajar99 said:**
> Hi Bojan (this is you, bvitnik, right?),

Thank you!  Checked out the link you provided, followed your workaround (restarted plasma), the issue was solved.

Yes that's me :).

I still don't know what's causing it. Nouveau is not the cause, because it happens on my other machine with radeon driver and also in virtual machine. Maybe KMS is the cause, but then again, in virtual machine there is no KMS and the bug is still present. I'm surprised that not many people has this bug but I myself can reproduce it anywhere. Maybe when you install proprietary drivers the bug disappears, and most people install them.

The weirdest thing is that it only happens in Kubuntu and not in other distros (with KDE) I tried.

Doesn't seem the bug is getting any attention.

---

### Post by guest_user on 2010-12-09
Is this bug solved yet?

EDIT: ok after I updated, everything seems fine

---

