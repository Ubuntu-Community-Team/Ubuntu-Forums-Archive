---
title: "hardware issue with laptop with my monitor, help!"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by scotcella on 2010-11-23
Hi all,

It's been a while since I logged into the forum. I have only just managed to sit down today and try and sort out one of my laptops that has Ubuntu loaded on to it.
[B]
Here is my problem:[/B]

I have a 13" Dell laptop that is still going strong except for the screen. Never mind how it got broken..  but the machine is still going strong, so I worked around the broken screen by hooking it up with an external monitor. No problems there! YAY..

My problem is that a few months ago, I changed the display settings, and I can't remember what I did and now the external monitor screen does not display what is on the laptop (I think I may have unchecked something!).

Anyway.. I took it to work and hooked it up on my work monitor (different brand and size) and it was working fine. Tested other monitors, no problems. Tried undoing it at work, came home..  still no joy! :(

I don't want to buy another monitor as the one I have is just fine. I am unable to use the Live CD to upgrade to the latest Ubuntu version (and start fresh!) as the external monitor is unable to display anything that is being run off the Live CD for some very strange reason, so I'm stuck with what I already have on the laptop. If I remember right I have Jaunty or the next version- I am not sure.

So what it seems to me is that the laptop remembers the display settings for the external monitor I have at home. 

**Question: **
How can I revert to the previous display settings? 

Does anyone know how to enable me to upgrade to the latest version that will display on an external monitor when I use the Live CD?



(Sorry for the long post!!)

---

### Post by koleoptero on 2010-11-23
Have you tried alt+f2, and then typing gnome-display-properties and then hitting enter? Does a new program window appear in the laptop monitor, or the externally connected monitor?

---

### Post by scotcella on 2010-11-23
I am not able to use the laptop screen as it is broken. My laptop is connected to an external monitor which is not displaying anything (as the display settings were accidently changed). What I mean by display settings being changed is **System** - **Preferences** - **Display**

I took my laptop to work and connected it to a monitor (different brand and size) and it was working just fine. 

I am assume that the display settings for my external monitor at home has been saved and I need to undo it.

How do I change the display settings back? I can take my laptop to work and change it there but I need to know what to change and how to change it so it will work at home.

Thanks heaps in advance!

---

### Post by koleoptero on 2010-11-23
That program is the same as I said you should launch. It obviously has stored the settings for your home monitor. When you get it working with another monitor, open your file manager, set it to show the hidden files and folders, and go to /home/*your_username*/.gconf/

Somewhere in there should be the settings for that program. It'll be either in desktop/gnome/ subfolder or in apps/

Sorry for the semi-vague reply, but I don't have an external monitor to check where it stores its settings for sure.

EDIT: If you find those settings then just delete them.

---

### Post by scotcella on 2010-11-23
Okay great thanks, I will try that when I take the laptop back to work. Hopefully that will be the end of it. Will give it a go tomorrow and post back how I went.

Thanks for your help. Too bad I don't have another monitor at home!

---

### Post by scotcella on 2010-11-29
> **koleoptero said:**
> That program is the same as I said you should launch. It obviously has stored the settings for your home monitor. When you get it working with another monitor, open your file manager, set it to show the hidden files and folders, and go to /home/*your_username*/.gconf/

Somewhere in there should be the settings for that program. It'll be either in desktop/gnome/ subfolder or in apps/

Sorry for the semi-vague reply, but I don't have an external monitor to check where it stores its settings for sure.

EDIT: If you find those settings then just delete them.

Went into the file manager to have a look at the hidden files and folders. I was not able to find anything related to the monitor. Looked around some other files that I think maybe be relevant, but but couldn't find anything.:(

My only option at this point is to upgrade the laptop (which I don't mind) but I do wonder if I will be able to view the Live CD with an external monitor or not? (Since the laptop screen is not working)

---

