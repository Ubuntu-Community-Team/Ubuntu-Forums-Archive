---
title: "Top panel locked in Karmic 10.04"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by PepeLapiu on 2010-07-04
Hi, I am reposting this thread because the original thread had a misleading tittle and I didn't get the answer I was looking for.
The original thread is here: [http://ubuntuforums.org/showthread.php?t=1515732](http://ubuntuforums.org/showthread.php?t=1515732)

The top panel is not configured the way I want. I would like it to be bigger, auto-hidden, non-expended and I would like to add/remove a few items on it.

But I am not able to edit the preferences. 

When I right-click the top panel and choose "Preferences", the only option offered is "Show windows from all desktops".

Someone replied that the panel is locked by default and so I would have to log out and log into the Gnome session, then edit the panel preferences from there.

But I have been unable to figure out how to log into the Gnome session.

Aren't there any way I can unlock that panel?
I thought Ubuntu was about the user configuring the OS however he wants .... so why did they go and lock that panel anyway !?!?

Cheers,
PepeLapiu :)

---

### Post by jtarin on 2010-07-04
[Try this bit of info for an indepth look]("http://library.gnome.org/admin/system-admin-guide/stable/gconf-8.html.en#gconf-14").

---

### Post by -kg- on 2010-07-04
I read the information in the original thread, and in no way get the menu items when I click on the top bar.

What information does it give you when you click on "About"?  That will tell you what you're looking at.

---

### Post by kerry_s on 2010-07-04
to select the session: log out & select your user, before you enter your password, on the bottom click on the session arrow, select "gnome", enter your password & log in.

ps: 10.04 is lucid, not karmic.

once your in gnome you can add the netbook-launcher, maximus & what ever other netbook things you want.

you'll also need to turn off nautilus managing the desktop & auto mounting, the netbook-launcher does that.


i use the netbook stuff on my nettop. i started the other way around though, from the normal ubuntu gnome install.

---

### Post by -kg- on 2010-07-04
> ps: 10.04 is lucid, not karmic.

Yes, I'm running Lucid (10.04) and the OP is running Karmic (9.10).  I ran Karmic for a *long while* before upgrading to Lucid.  The panels and their configuration menus are essentially the same.

That the OP is not even getting a menu selection to "Add To Panel" tells me that he may not be clicking on an actual panel.  That's why I requested him to click on "About" in the menu he's getting.  "About" should read "About Panels".

---

### Post by kerry_s on 2010-07-04
> **-kg- said:**
> Yes, I'm running Lucid (10.04) and the OP is running Karmic (9.10).  I ran Karmic for a *long while* before upgrading to Lucid.  The panels and their configuration menus are essentially the same.

That the OP is not even getting a menu selection to "Add To Panel" tells me that he may not be clicking on an actual panel.  That's why I requested him to click on "About" in the menu he's getting.  "About" should read "About Panels".


i was referring to the thread title:
> Top panel locked in Karmic 10.04

yes, your right in 9.04/9.10 the panel is not locked, but you do have to unlock the taskbar(window-picker-applet) & slide it over to get to the actual panel.

in 10.04 the panel is locked down.

---

### Post by lkjoel on 2010-07-04
Try LinuxEssentials, it could help it.

---

### Post by -kg- on 2010-07-04
My apologies, kerry_s...I was reading the information in his information area to the left, and not reading the original post, in which he stated:

> Hi all, I just installed 10.04 on my netbook.

PepeLapiu, you need to change the information in your control panel (on this site, not your computer) to reflect what version you're using now. :)

Perhaps this is an issue with or feature of the netbook remix.  Except that he didn't say that he installed the netbook version...just 10.04.  I've never had experience with this issue.

> yes, your right in 9.04/9.10 the panel is not locked, but you do have to unlock the taskbar(window-picker-applet) & slide it over to get to the actual panel.

in 10.04 the panel is locked down.

I'm confused, now.  I've never had this issue with either of these versions, or the ones before.  I don't have a "Window Picker Applet" installed, nor was it installed as default upon installation.

Would that be Window Selector or Window Switcher?  They both seem to do the same thing.  Again, it would be helpful if we could find out what "About" tells him.  From the other thread:

> When I click on an empty spot the drop-down menu shows:
-Preferences
-About
-Remove from panel (greyed out)
-Move (greyed out)
-Lock to panel (greyed out)

So apparently, for some reason, he is unable to move it (greyed out), remove it (greyed out), or unlock it on the panel (greyed out).  Kinda hard to slide it over when you can't even unlock it or anything.

Gotta find out what it is before we can suggest a course of action.

---

### Post by kerry_s on 2010-07-05
just the fact he's saying it's locked, i know he has netbook remix installed.

window-picker-applet is the taskbar with the close button(X) on the end. if your using netbook remix you have it or else you would be right clicking the taskbar to close the window.

i've used them all & run a custom netbook type setup. i use the standard showdesktop & taskbar. i have maximus set not to undecorate, but i still use maximzed windows.

---

### Post by mirchichamu on 2010-07-05
I am not very familiar with Linux BUT I had the same problem. I downloaded this Ubuntu tweak and it solved my problem. Go to Genome settings and panel settings and untick panel lock.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by PepeLapiu on 2010-07-07
Okay all. Here's the skinny of it all.
I have 10.04 Lucid Netbook Remix installed. And yes, I will update my profile right after this message, thanx for pointing it out.
And yes, Lucid netbook has the panel locked.
I logged out and logged into the Gnome session. In Gnome session, the panel isn't locked and the annoying bussy desktop menu of the netbook version is gone (bonus!).

Now the puter automatically logs into the Gnome session, which I prefer anyway. So no more locked panel and no more netbook menues. Thanx all, the issue is solved thanx to your great help.

I love this open source community thing!!

Cheers,
PepeLapiu :)

---

