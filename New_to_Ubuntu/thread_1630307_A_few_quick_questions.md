---
title: "A few quick questions"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Sejanus on 2010-11-25
Is there a way to customize the clock so that the week starts on Monday ends on Sunday?

After a period of inactivity the screen turns off. I need to enter a password after that. Where can I adjust the time before the screen goes off, and turn off the password pop up, I dont need it?

And one thing I love about Linux is the lack of retarded "are you sure you want to..." pop ups. Compared to Windows anyway. But still there are some of them here too. Like, when you are turning your PC off it asks if you are sure about that. How could I disable it? There's nothing like comming back after a two days absence and finding your PC still turned on with a message on screen "Are you sure you want to turn off..."

Thanks in advance!

---

### Post by amjjawad on 2010-11-25
> **Sejanus said:**
> After a period of inactivity the screen turns off. I need to enter a password after that. Where can I adjust the time before the screen goes off, and turn off the password pop up, I dont need it?


System > Preferences > Screen Saver


> 
And one thing I love about Linux is the lack of retarded "are you sure you want to..." pop ups. Compared to Windows anyway. But still there are some of them here too. Like, **when you are turning your PC off it asks if you are sure about that**. How could I disable it? There's nothing like comming back after a two days absence and finding your PC still turned on with a message on screen "Are you sure you want to turn off..."

It's called "Warning Messages" for a reason. Even if there is a way to turn that off, it would be a bad idea. Imagine a System without Warning Messages? Imagine you drive in New York for example without Traffic Lights!

---

### Post by racie on 2010-11-25
> **Sejanus said:**
> **After a period of inactivity the screen turns off. I need to enter a password after that**. **Where can I** adjust the time before the screen goes off, and **turn off the password pop up**, I dont need it?

Try going to "/etc/default/acpi-support" and comment out (put the # symbol in front of it) the line "LOCK_SCREEN=true."  This should disable the password prompt.  It worked for me.

*edit* Or you could try this solution:
> 1. As you've probably already done, uncheck:
"lock screen when screen saver is activated" 
in the System->Preferences->Screen Saver menu.

2. Type gconf-editor in a terminal. Under apps/gnome-power-manager/locks check: 
"use_screensaver_settings". 

3. If still asked for password, you can (also in gconf-editor) go to desktop/gnome/lockdown and check: 
"disable_lock_screen"
Credits to itslofty below for this tip!

---

### Post by 3rdalbum on 2010-11-25
The shutdown warning can be disabled. Hit Alt-F2 and type 'gconf-editor'. Expand out / and apps and indicator-session and the setting is in there. However I would advise keeping it on as it will save time if you hit Shutdown instead of Suspend!

---

### Post by Sejanus on 2010-11-25
Thank you for your replies. I managed to fix screensaver / password issue, however I cannot remove the shutdown warning.

> 
The shutdown warning can be disabled. Hit Alt-F2 and type 'gconf-editor'. Expand out / and apps and indicator-session and the setting is in there. However I would advise keeping it on as it will save time if you hit Shutdown instead of Suspend!

All I see there is the options to remove certain buttons from the menu. I can remove shutdown button completely from the top-right menu but I didn't see how I could remove warning only. I can add screenshot if that'd help.



Considering usefulness of the warnings.
Comparison to the traffic signs is not valid. Traffic signs tell you what you can (must) do and what you cannot. Warnings simply ask if you are sure about what you are doing. Yes I am thanks for asking, thats why I am doing it in the first place. Usually they do not provide any useful information on consequences or alternatives or anything else, just ask if you are sure. Waste of time. If they provided info on possible consequences or if they guided me through something, like the traffic signs do, I'd gladly accept them.

Even if I accidentally hit something I don't intend to do, usually I press YES on pop ups without thinking - I am so bored of them I don't even read. Maybe this is a bad habit developed from using Windows where you must confirm you know what you are doing three times per minute due to all sorts of software design flaws (trying to save settings in C:/Program Files, etc.) 99 times out of 100 they are meaningless.

And when it comes to turning off the PC, this is not something that even requires the warning. It has no possible fatal consequences, you can always turn it back on :D 

Lets take another example, I must always confirm that I want to close qBittorrent. What? Why on Earth? Is closing it such a potentially dangerous action? I can run it anytime again and all the downloads will continue from the point they stopped at. There's no possible harm to my PC or anything from closing it and yet I am forced to deal with stupid confirm pop up.



If they weren't so common and useless in 99% of cases, they would serve their purpose. But alas, they don't. So I am very happy with my Ubuntu where they are relatively rare, compared to Windows spam.

Anyhow sorry for the rant, I hope you see my point :)

---

### Post by amjjawad on 2010-11-25
It must be the **flu** that makes me post **_bad examples_**. My apology.

*_My point is:_ I would not disable that if I were you but that's only me.*

Good luck!

---

### Post by QLee on 2010-11-25
[QUOTE=Sejanus]...
If they weren't so common and useless in 99% of cases, they would serve their purpose. But alas, they don't. So I am very happy with my Ubuntu where they are relatively rare, compared to Windows spam.

Anyhow sorry for the rant, I hope you see my point :)[/QUOTE]
Rants are allowed, they can serve a useful purpose as a relief valve and I for one can tolerate them from people who recognise what they are writing.

I believe I do see your point. I too am a power user and rarely enter a command that I don't want to run, nor do I click on some GUI icon unless I want to use the action. That being said, I am human and make mistakes from time to time. I have the advantage of not being stuck with the Windows mindset of, just click yes to get on with my work, which some of my friends who use Windows do without thinking. 

But this is not about us, Ubuntu is crafted to be as easy as possible for inexperienced users and people who never want to, nor will they ever, be power users. As you have discovered, Ubuntu gives you choices of customising once you understand enough. Cool, eh? 

If you don't like amjjawad's analogy, how about the analogy of a "Slow Curve Ahead" sign. I watch ahead and don't speed so don't need that sign most of the time, but I don't suggest that it is unnecessary or that it should be removed (although that might be a good idea from the standpoint of the concept of Darwinian natural selection).

---

### Post by 3rdalbum on 2010-11-27
> **Sejanus said:**
> All I see there is the options to remove certain buttons from the menu.

Look more carefully at the descriptions of the options. I was on my phone at that time so I couldn't give the exact name of the option.

It's /apps/indicator-session/suppress_logout_restart_shutdown, and the long description is this:

> Whether or not to show confirmation dialogs for logout, restart and shutdown actions.

---

