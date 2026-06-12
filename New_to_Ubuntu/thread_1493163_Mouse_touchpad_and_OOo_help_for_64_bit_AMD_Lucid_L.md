---
title: "Mouse touchpad and OOo help for 64 bit AMD Lucid Lynx (10.04)"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Saiyaman on 2010-05-25
I'm having a bit of difficulty with the mouse touchpad for my "HP Pavilion dv6000" laptop.  My laptop's mouse touchpad has a button that you can press to disable and enable the touchpad whenever you want, and it works just fine in Windows Vista with no problems.  However, when I was trying to work on an essay on OpenOffice.org (and even right this moment, actually), the mouse keeps jumping all over the place and inserting the cursor somewhere else on the screen, be it a different place in the essay, or on a different window (if my OOo window isn't maximized).

So, this was really a pain, so I would press the on/off button for my touchpad, and turn it off.  But then, I would find that the cursor is no where to be found!  To make matters worse, when I turn my touchpad back on, I can't type anything in or right-click wherever text can be inputed, and the shutdown menu button at the very top-right corner of Lucid just refuses to open.  To shut down, I've been having to press and hold the power button that is physically on the laptop.

Then, while I'm in this state, I try to use the update manager.  I check for updates, and a message pops up saying something like "Keyboard can not be found.  .....some malicious program may be trying to keylog your keyboard" from the update manager.  There are "..." in the quote, because in fact, I saved it onto my essay, and when I manually restarted linux, the whole file was gone!

As I mentioned earlier, I was typing an essay that I was well into the middle of when it just all got deleted and now it's at 0 bytes.  I had OOo recover it at the time, both the essay before I saved and the essay after, but I exited out of the essay that I had before I saved, and I really can't get it back.  I tried going into "/tmp", but I couldn't really figure out what I had to be looking for.  Someone please help me...
I'm really irked about the mouse touchpad, but I'm much more upset about my lost essay!

---

### Post by Ozymandias_117 on 2010-05-25
If you go to ~/.openoffice.org/3/user/backup you may have some of your essay back.

Have you looked in System -> Admin -> Hardware drivers to see if there is anything special for your mouse?

---

### Post by philinux on 2010-05-25
Not certain for this one. System,Prefs,mouse  turn off mouse gestures

---

### Post by Joe of loath on 2010-05-25
To at least gracefully shut down, ctrl-alt-F1, log in and type 'sudo halt'.

---

### Post by Saiyaman on 2010-05-25
Ozymandias_117:  Thanks, I **never knew there was such a folder, so I went and checked (figuring out how to do that with much difficulty), and there was nothing there.  I kind of expected it; though, that doesn't make me feel any better...
I went ahead and checked System>Admin>Hardware Drivers, and all I saw was 2 hardware drivers, both of which were for Nvidia's graphic cards.  (The Hardware Drivers program/thing said it was searching for drivers, and apparently those 2 were the only 2 that were found)

philinux: Thanks, although I'm not too sure what you meant by &#8220;turn off mouse gestures&#8221; as I didn't see any options with a similar title, I did do some poking around, and cleared the &#8220;disable touchpad when typing&#8221; box under the &#8220;Touchpad&#8221; tab.  It helped a little, but sometimes when I pause for a little while to think, the cursor jumps all over the screen again since my palm sometimes accidentally touches it, so when I start typing again, I'm starting in the middle of some other paragraph.  It does help when I'm typing!  So far my cursor has jumped 2 or 3 times while I was still in the middle of typing, though.

**Edited in, because I forgot the never

---

### Post by Saiyaman on 2010-05-25
Joe of loath: Thanks, I *just* tried it out just now.  I have a few questions regarding it though.  What does ctrl+alt+f1 do exactly when you first enter into that text mode? I saw something about updates?  Does entering sudo halt in the terminal also kill processes that you want the system to stop doing (ie. taking too long on a process/freezing on it)?  When you shut down with the ctrl alt f1 and sudo halt way, does it save your session's settings (like how I would imagine a shutdown button from the shutdown menu would)?  And I know this isn't really relevant, but...why ctrl+alt+f1?  I mean why did the writers decide on f1 (and ctrl+alt of course) as the more basic text/I'm-not-sure-what-it-is way of running the system (why would it be intuitive)?  I'm not trying to give anyone a hard time, as these questions might, I'm asking purely out of curious.

---

### Post by Ozymandias_117 on 2010-05-25
> **Saiyaman said:**
> Joe of loath: Thanks, I *just* tried it out just now.  I have a few questions regarding it though.  What does ctrl+alt+f1 do exactly when you first enter into that text mode? I saw something about updates?  Does entering sudo halt in the terminal also kill processes that you want the system to stop doing (ie. taking too long on a process/freezing on it)?  When you shut down with the ctrl alt f1 and sudo halt way, does it save your session's settings (like how I would imagine a shutdown button from the shutdown menu would)?  And I know this isn't really relevant, but...why ctrl+alt+f1?  I mean why did the writers decide on f1 (and ctrl+alt of course) as the more basic text/I'm-not-sure-what-it-is way of running the system (why would it be intuitive)?  I'm not trying to give anyone a hard time, as these questions might, I'm asking purely out of curious.

It was just notifying you that there are new updates available for your system. System -> Admin -> Update Manager or in a terminal ```
sudo aptitude full-upgrade
``` to get them.

"sudo halt" will kill all processes and shut your computer down.

I'm not sure if it saves your settings or not, I would assume it does though.

Ctrl+Alt+f1 through Ctrl+Alt+f8 are your virtual terminals. f7 and f8 are reserved for your X sessions (That is your GUI) and f1 through f6 are all text (At least in defaults). What you need to remember for this to make sense, is Linux is simply tons of small programs added together to make an operating system. Even though you see this pretty GUI, everything you do are then translated by the program into text commands and passed farther on. You can do anything on your computer from one of those terminals.

I hope that makes sense, I was trying to keep it fairly simple, yet still explain it. :) If you didn't understand, let me know where I screwed up.

---

### Post by Saiyaman on 2010-05-27
> **Ozymandias_117 said:**
> It was just notifying you that there are new updates available for your system. System -> Admin -> Update Manager or in a terminal ```
sudo aptitude full-upgrade
``` to get them.

"sudo halt" will kill all processes and shut your computer down.

I'm not sure if it saves your settings or not, I would assume it does though.

Ctrl+Alt+f1 through Ctrl+Alt+f8 are your virtual terminals. f7 and f8 are reserved for your X sessions (That is your GUI) and f1 through f6 are all text (At least in defaults). What you need to remember for this to make sense, is Linux is simply tons of small programs added together to make an operating system. Even though you see this pretty GUI, everything you do are then translated by the program into text commands and passed farther on. You can do anything on your computer from one of those terminals.

I hope that makes sense, I was trying to keep it fairly simple, yet still explain it. :) If you didn't understand, let me know where I screwed up.

Wow, thanks!  I have noted everything you wrote.  It doesn't all make sense to me, especially what this X sessions thing is and how Linux needs 6 what I understand to be text-based terminals, but otherwise your explanation was very clear and gives me very solid information to start out with, so I'll look more into it since I haven't gotten very far into Computer Science yet.  

I think I might have heard somewhere that the point of having so many terminals is in case one terminal becomes unresponsive or something, Linux can still run the other parts.  It seems like having so many terminals simply for back up doesn't really make sense.  Nor does having all these terminals be programs within each other make sense.

On a different note:
Actually, my touchpad still jumps everywhere when I type, and now I find it really bothersome again.  My solution was just to put some tape on the bottom of the post-it on my desk and cover my touchpad with it while I type.  Even though it kind of obstructs my thumb's accessibility to the space bar, my touchpad problem has been solved! (for now)

---

