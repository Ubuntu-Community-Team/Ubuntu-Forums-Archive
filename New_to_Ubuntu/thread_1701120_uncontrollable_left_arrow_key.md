---
title: "uncontrollable left arrow key"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by elliryn on 2011-03-06
Hi guys,

I just installed Ubuntu 10.10 Netbook Remix on my HP Mini 1000. Everything worked fine right up until I tried typing - apparently the left and right arrow keys on my keyboard are uncontrollable. Everything I type ends up looking messed up because as I type, the left arrow key makes my letters go backwards if I'm making sense.

This also happens when I click on, say, "File" on Firefox. It starts rotating between all the different menu options even though I'm not pressing anything on the keyboard.

Does anyone have any idea what's going on? Is this a problem with the keyboard itself?

**EDIT.**
I tried using my USB keyboard with the netbook, and the same problem occurs. Apparently the backspace key is a little nuts as well. I guess this isn't the keyboard's problem then. What else could be causing the keys to go wonky? ):

---

### Post by fabricator4 on 2011-03-06
> **elliryn said:**
> I just installed Ubuntu 10.10 Netbook Remix on my HP Mini 1000. Everything worked fine right up until I tried typing - apparently the left and right arrow keys on my keyboard are uncontrollable. Everything I type ends up looking messed up because as I type, the left arrow key makes my letters go backwards if I'm making sense. 

I was going to suggest that you change the touch pad settings to "disable while typing".  Being a touch typist I have a problem where inadvertent contact with the touchpad causes all sorts of problems.  I also have button emulation on the mousepad disabled because this also causes problems.  Touchpads are not well placed for touch typists.

However, your edit below makes me wonder if this really is the problem, if it still happens with a separate keyboard, and a <backspace> problem at that, unless your keyboard is coincidentally faulty as well.

Chris

**EDIT.**
I tried using my USB keyboard with the netbook, and the same problem occurs. Apparently the backspace key is a little nuts as well. I guess this isn't the keyboard's problem then. What else could be causing the keys to go wonky? ):[/QUOTE]

---

### Post by quirks on 2011-03-06
I doubt it has something to do, with you hitting the touchpad accidentally. I assume that the left arrow key on your netbook keyboard is pressed constantly (for whatever reason). This would explain the looping through the Firefox menu and the "backwards-typing". It could be a hardware defect or a driver issue. It is of no use to plug-in a USB keyboard, because even when an external keyboard is attached, the internal one is still functional and as such, the signals from the left arrow key are still sent.

Since when has this problem existed? Ever since the installation of 10.10 or earlier? Do you have a possibility to test a different OS, such as an older version of Ubuntu using a live CD or maybe MS Windows? If the problem does not occur with another OS, then I call it a driver issue. If it persists, then most likely, your keyboard is defective and you need to have it replaced.

---

### Post by elliryn on 2011-03-06
> **quirks said:**
> I doubt it has something to do, with you hitting the touchpad accidentally. I assume that the left arrow key on your netbook keyboard is pressed constantly (for whatever reason). This would explain the looping through the Firefox menu and the "backwards-typing". It could be a hardware defect or a driver issue. It is of no use to plug-in a USB keyboard, because even when an external keyboard is attached, the internal one is still functional and as such, the signals from the left arrow key are still sent.

Since when has this problem existed? Ever since the installation of 10.10 or earlier? Do you have a possibility to test a different OS, such as an older version of Ubuntu using a live CD or maybe MS Windows? If the problem does not occur with another OS, then I call it a driver issue. If it persists, then most likely, your keyboard is defective and you need to have it replaced.

Thank you very much for your reply (and to you too, fabricator4) - I've never had this problem on Windows XP before I installed Ubuntu, and actually, on my first installation of Ubuntu, I didn't have this problem either. It was recently when I decided to try and fix a wireless problem by reinstalling Ubuntu 10.10 that this problem popped up.

If it's a driver issue, should I reinstall the driver for the keyboard? Where can I locate the right driver for that?

---

### Post by quirks on 2011-03-06
The driver issue is only a guess. There could be other reasons. If it really is the driver, then I wouldn't know off the top of my head what package you had to re-install in order to re-install the driver. Plus, I am not sure, if a re-installation of the driver would fix anything. Let's try to isolate the problem a little, first.

Can you remember that you did anything special right before the issue first appeared? In particular did you do one of the following:
[LIST]Did you apply any updates? If so, please open Synaptics package manager and go to File -> History and tell as, what updates you applied right before the problem first showed up.[/LIST]
[LIST]Did you change any system configuration? If yes, what did you do?[/LIST]

Often it is not the entire system that is affected but just your profile (due to a bogus setting, for example). Does the problem show up on the login screen? Would you mind creating a second user and login as this user to see if the problem is gone? If the problem does not occur on the login screen or with the test user, then your profile is somehow messed up. In this case, we would need to track down the setting that is causing it.

Can you try to boot from your Ubuntu live CD and check if it is gone?

Also, have you tried rebooting in the meantime? And by reboot I mean really restart and not just hibernate. (I am fairly sure that you have, but often people haven't and lots of time is wasted, even though the problem would have solved itself with a simple reboot - if only I had asked for it.)

---

