---
title: "Cairo Dock (Though Awesome) is being a Poop"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by orphanlast on 2010-05-08
I am using "glx-dock" Cairo-Dock. (I used to use Avant, but the way they've modified it has pissed me off). Anyways. 

I've got this irritating thing on my Dock. It's called "_SubDock_" EVERY SINGLE TIME I hover my mouse over it, it closes my dock and opens the Configuration Menu for it. Here's what I've attempted to do, so far, to get rid of it.

I've tried looking in that Configuration Menu under the tab "Add-ons" and there's nothing in there called _SubDock_ so I can't get rid of it that way. 

I've tried to right click on it and select from the drop down menu "Remove Applet" but it all happens in a split instant. My dock disappears, the Configuration Menu comes up and my drop down menu disappears just as quickly as it appears.

Now... I know Linux operates completely differently than Windows, but if I've usually had a problem I couldn't fix on my own, I'd just uninstall the program and then reinstall it. That didn't work. The _SubDock_ is still there. 

I've also restarted my computer to see if that was a temporary setting as well. This is something that's evidently a permanent setting unless I can get rid of it manually.

I'm at a loss of words and I don't know what to do from here. I've explored all my known options... could someone please help. My whole desktop experience is a real pain in the butt because of this.

---

### Post by orphanlast on 2010-05-08
Here's some attached pictures to demonstrate what's up.

The first Attachment demonstrates what this thing looks like.

[ATTACH]156088[/ATTACH]

The second attachment demonstrates what happens after I hover my mouse over the blank spot labeled _SubDock_. Notice no dock and the Config Menu is up.

[ATTACH]156089[/ATTACH]

I've noticed THIS from a drop down menu when I play around with the dock and I'm fairly certain this is how it came into existence. 

I've force quit the dock and sometimes there's more than two, but even when there's just one... _SubDock_ is still there.

The Third Attachment demonstrates how I think I brought this thing into existence. It says "Add Subdock" (Which... I don't even know what that is... other than it's being a real poop. Why would anyone want something this annoying on their desktop. Why would anyone go "Oh yes -- yes indeed. I would love a pain in the *** every time I try to use my dock. Put that right on" that's humor, by the way.)

But notice how there's no "remove sub dock" button".... on that drop down menu

[ATTACH]156090[/ATTACH]

So yeah. I'm still at a loss.

---

### Post by orphanlast on 2010-05-08
Nevermind... I'm not sure what I did, but I started playing with the themes and that changed the way things looked on the desktop and that got it so that I could use the dropdown menu and I could sellect -- "Remove this Launcher" and that did the trick."

Can anyone tell me what that thing was, what the point of it is. And how to get rid of it easier without making my dock look completely foriegn for a little while?

---

### Post by peculiar penguin on 2010-05-08
Subdocks work like a directory/folder, you can stick multiple launchers inside. That way they take up less space on the main dock, and if you hover over the subdock you get a popup menu with all launchers inside.

I just added one and removed it without any problems, you may have a wonky theme or something. If nothing else works, you can always close the program and nuke its config directory (~/.config/cairo-dock) assuming you don't mind setting everything up from scratch again.

---

### Post by orphanlast on 2010-05-08
> **peculiar penguin said:**
> Subdocks work like a directory/folder, you can stick multiple launchers inside. That way they take up less space on the main dock, and if you hover over the subdock you get a popup menu with all launchers inside.

I just added one and removed it without any problems, you may have a wonky theme or something. If nothing else works, you can always close the program and nuke its config directory (~/.config/cairo-dock) assuming you don't mind setting everything up from scratch again.

Hey thanks for the response. You know... although I really liked that dock, it got really irritating. I really liked how I had full freedom with what the icons appear as on the dock, but they really need to simplify it a bit. It got too time consuming and after a while of messing with it, it wouldn't let me add applets.

So I decided that if that Dock was so customizable maybe i'm just overlooking something with Avant. Turns out Avant is not even close to being as customizable, but it's so much more pleasant to use. My beef with it was that I had the wrong ticks under the "task manager" settings. 

I'm all over the place with Ubuntu, right now. I'm sorry for the weird thread.

I ask for help with one dock and wind up using another after I solve the problem.

---

### Post by fabounet on 2010-05-08
which version are you using ?
the latest one has a very simple config panel (the full one is stil available, but is not the default one).

see here to get the latest stable release, since the project is moving forward at a high pace.
[http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en")

---

