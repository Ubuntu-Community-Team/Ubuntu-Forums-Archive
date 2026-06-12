---
title: "remove/adjust sound at startup"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by yozgoesdigital on 2009-05-15
Hi all,
I almost feel embarrassed to ask this question, because the answer is probably so obvious....

Is there a way to adjust/remove the starting sound when I start/quit Kubuntu?
Most preferably I would like to find a menu just like the Win (XP) configuration/sounds 
I have been checking the system settings already a few times, am I overlooking something?

Thanks

---

### Post by Didius Falco on 2009-05-15
> **yozgoesdigital said:**
> Hi all,
I almost feel embarrassed to ask this question, because the answer is probably so obvious....

Is there a way to adjust/remove the starting sound when I start/quit Kubuntu?
Most preferably I would like to find a menu just like the Win (XP) configuration/sounds 
I have been checking the system settings already a few times, am I overlooking something?

Thanks

Hi, and welcome to the Ubuntu Forums.

Go to **System/Preferences/Sound**. It will have two tabs, **Devices** and **Sounds**. On the **Sounds** tab you can set up the sounds as you like[B].

[/B]An alternate way to get to them is to right-click your **Fast User Switcher**, go to the **Setup Login Screen **and then to the **Accessibility** tab.

You have more choices using the first way, but can set up a login failure sound the second.

BTW - there aren't any dumb questions.

Regards,

Didius

---

### Post by yozgoesdigital on 2009-05-15
Thanks for the reply,
The things you name are completely unfamiliar to me, are you talking about Kubuntu and not Ubuntu?
I run Kubuntu 9.04, but have this problem already since Kubuntu 8.10

greetings, Jos

---

### Post by Didius Falco on 2009-05-15
You should have the Fast User Switcher - it's the button on your panel where you can log out, switch users, hibernate, restart, etc.

Meanwhile, I'll see what I can dig up about changing the sound in **K**ubuntu. <G>

Regards,

Didius

---

### Post by Didius Falco on 2009-05-15
Okay, I found this:

[http://kubuntuforums.net/forums/index.php?topic=3102379.0](http://kubuntuforums.net/forums/index.php?topic=3102379.0)

Where Dugeek said:

> The first step to answer your question is to take a look at **System Settings**. (should be right there in the "K" button menu)

The **System Settings** window is different from Control Panel in two important ways:

[LIST]
[*]first, you don't see all of the options at the same time (like Windows2000 and previous, or if you used "classic view" in XP/Vista) --these options have been sorted into some common-sense categories
[*]second, the window you see will "follow" you into the specific panels... like a web-browser, there will be a 'back' button (in this case, it's labeled **Overview**) that takes you back to the first window
[/LIST]

Here's the part that's probably throwing you a loop. The name for "system sounds" in Kubuntu is **Notifications**. If you look right there at the top, there's a Notifications icon! Click it.

Now the window changes to the Notifications panel... but it doesn't look like there's much there. That's okay, we're on the right track. In Linux, *every* application has the ability to notify you with sounds... even different sounds for different applications... and all of them can be controlled right here!

On my system, the first application I see is **Akregator**, with just two events. This may be different on your system, so just bear with me. The list where Akregator appears is labeled **Event Source** and it's a drop-down list. 

Pull the list down and find **KDE System Notifications**. If you ask me, someone should get this to be the first group that appears... if we contribute some feedback, they could make that change for us!

Now you'll see a much larger list of events. The "music" you're talking about would be the **Login** and **Logout** event sounds. Click on one of those and the options for that event appear at the bottom of the window. 

Right there, a checkbox for **Play a sound** lets you turn the music off. (clear the checkbox) Do that for both of those events and the music won't bother you again. Click **Apply** (bottom-right corner) to put those changes into effect immediately--just like in windows.



I hope that solves it for you. We both learned something out of this!

Regards,

Didius

---

### Post by yozgoesdigital on 2009-05-15
Hi Didius, Thanks for searching!!
This was exactly what is was looking for. I did check notifications before, but totally missed the dropdown menu with the different programs.
Did not know kubuntuforums.net either, thanks for the link.

Greetings Jos

---

### Post by Didius Falco on 2009-05-15
Glad to help where I can.

There are Kubuntu users here, so this is a good place for information - I'm just not one of them. But I like to search for things, so I thought I'd give it a go anyway.

Besides, like I said, this way I'm learning too.

Regards,

Didius

---

