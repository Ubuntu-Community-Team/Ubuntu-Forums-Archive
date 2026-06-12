---
title: "Logout disabled! (Don't know why.)"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-08
I've got a strange problem here. The logout function has been disabled in both Gnome & KDE. I don't know if this is affecting any other profiles than the one I'm currently using. The current profile is set as being disallowed for doing admin functions.

I'd worked in Gnome tweaking display settings, and tweaking the preferneces in Open Office. I decided to log out to switch to KDE and set up a KMail email account. The logout wasn't working. I finally used Ctrl/Alt/Sysreq-REISUB to reboot.

When the login screen was displayed again, I switched desktop selection to KDE and logged in. Almost (see next paragraph) everything was fine for the couple of hours I worked in KDE - but, when I tried to log out, there was a system notification that said "Logout disallowed by". And didn't tell me by who or what. I'm going to try tweaking the user profile's permissions, using authorization from an admin profile. I don't know if that will work or not,... Or, even if changing permissions will enable a normal logout. But, I'm going to try it after I post this message.

There was one weird thing when I was in KDE. I returned to tweaking Open Office settings, and at the end when I was looking at the "Internet" section it was listing something like "oomau" as the default mail client. (I've forgotten exactly what, and didn't write it down.) I replaced it with "KMail", and proceeded to do other things. Is it possible my computer was hacked, and some defective damaged settings while inside?

I almost forgot to mention, that when I was finished web browsing, Firefox wouldn't close via the control in upper right corner of the window. I had to shut it down using a menu-click (selecting "close") on the bar at the bottom of the screen.

My initial guess, is that the system notification didn't tell me who or what disabled the logout because it simply didn't have that info. Is there any way to discover what the problem is, preventing logout? And, how to fix it if this problem persists?

Updating info: Adding admin powers didn't fix it. So, I removed admin powers, then used Ctrl/Alt/Sysreq-REISUB to restart the machine. Not quite willing to drop it for now, I logged into Gnome as an administrator, then immediately logged out. It worked. Encouraged by that success, I did the following:

*) I logged into a "Failsafe" Gnome session using the limited user profile that had failed to log out before. Once into Gnome, I immediately logged out. It worked!
*) I repeated logging into Gnome, but this time in a normal session. Logging out immediately again, it worked!
*) I logged into KDE using that same profile, then immediately logged out. That worked, too.

I've logged in & out from both KDE & Gnome repeatedly now, using both profiles without the problem recurring. I don't know if this logout problem will happen again in the future, or even what caused it. But, "Enquiring minds want to know!"

---

### Post by scruffyeagle on 2011-08-21
The preceding post was about events on a Dell Inspiron, that I'm now certain was hacked & damaged. This post is about events on a Toshiba Satellite A205. Both machines are loaded with Ubuntu v10.04 LTS 32-bit.

I'm having a failure of the ability to logout, restart, &/or shut down. "Switch from", changing to another listed User, Suspend, & Hibernate aren't affected by this failure. This failure will consistently happen if I log into a Gnome session, activate Open Office writer, shut that down right away without doing anything, and then try to log out. I've only seen this happen on this particular machine, in this installation of the OS. But, if I do the sequence I just listed, it will happen _every_ time.

I came up w/ 3 options for turning off the machine's power.
1) Ctrl/Alt/Sysreq-RESIUB will end up at the login page after rebooting, and the shutdown menu on that page can be used to turn the machine off,
2) Hibernate will turn off the power, but the drawback is that on powering it up it will always return to the session where the end session function failed, and
3) Use the "Switch from" option to gain access to the login page w/ list of users. From there, I can use the menu from the lower right corner, and the functions from that menu will work.

The safest of these 3 in terms of protecting settings & data is obviously option 1, but this machine is for my mother and that awkward key combination is impossible for her 82-yr-old hands to do. So, I've told her to use option #3 when this problem happens.

It would be much better for her, and for this machine, if I could find some way to solve this problem. Anybody have any suggestions?

---

### Post by heyandy889 on 2011-08-21
I'm kind of confused. Sorry, dude. I would recommend hitting the old Google with 4-5 word searches, like "logout doesn't work kde." Even better would be to limit the search to the past year, so you make sure you're getting recent information.

Sorry I don't have a specific fix. Good luck, dude!

---

### Post by scruffyeagle on 2011-08-22
> **heyandy889 said:**
> I'm kind of confused. Sorry, dude. I would recommend hitting the old Google with 4-5 word searches, like "logout doesn't work kde." Even better would be to limit the search to the past year, so you make sure you're getting recent information.

Sorry I don't have a specific fix. Good luck, dude!

It's okay, friend. I posted that yesterday, hoping someone would have a suggestion - and, in the application of their suggestion, I might learn something useful. Between then and now, I've decided that if there wasn't any such suggestion posted, I'd wipe the installation and start over from scratch. I can only hope this isn't some consequence of interaction between Toshiba firmware and Ubuntu... My current guess is that there's probably some combination of list adjustments done by programs, or environment variables settings set by programs, that's causing this. I don't have the knowledge & experience to track it down or fix it on my own. Perhaps, in the re-installation, I'll do some minor point of setup differently and stumble into a setup that doesn't have this disfunction.

---

