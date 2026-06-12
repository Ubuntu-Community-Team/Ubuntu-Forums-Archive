---
title: "How do I make the windows (super)+m keys Invert Colors for the whole screen again?"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by mikodo on 2011-04-13
Hi,

I used to really enjoy having the windows (super) + m key  invert colors for the whole screen. It is how I usually kept my desktop.

I screwed it up and now when I press them together they give me the drop down menu of the indicator applet.

I don't know what I did, nor do I know what to do, to get the combination back to inverting the colors for the screen.

Here is the ubuntu Keyboard Shortcuts page describing it:

[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

Any suggestions? 

Thank you.

---

### Post by 3177 on 2011-04-13
I'd say look for it in keyboard shortcuts.
system>preferences>keyboard shortcuts.

---

### Post by mikodo on 2011-04-13
> **3177 said:**
> I'd say look for it in keyboard shortcuts.
system>preferences>keyboard shortcuts.

Hi,

No I looked there already.

Thanks.

---

### Post by 3177 on 2011-04-13
maybe try resetting your keyboard?

---

### Post by mikodo on 2011-04-13
> **3177 said:**
> maybe try resetting your keyboard?

No, I messed with that and nothing brought back the invert colors and then put it back to the default settings where they were before this happened and it still gives me the drop down menu of the indicator applet.

Thanks.

---

### Post by earthpigg on 2011-04-13
wow, i never knew about that. now i can give myself siezures on demand.

my girlfriend has a three-legged chihuahua that is deaf, partially blind, *and* that is epileptic. (no joke.)

i probably shouldn't do that when he is around, huh?

---

### Post by Rasa1111 on 2011-04-13
Super key + N makes your desktop "negative" colors.

 That what you mean?
[ATTACH]188893[/ATTACH] [ATTACH]188894[/ATTACH]

Hmm, Just tried Super+M , as you said..
Seems to do the same thing ..

edit: Ohh, I see..
Super+N makes the current window negative..
Super+M makes the entire desktop enviro. inverted..
 hmm, interesting...

So it appears I cannot help.
 Sorry mate. 

Have you gone into CCSM and checked the setting for it?

---

### Post by mikodo on 2011-04-13
[Have you gone into CCSM and checked the setting for it?[/QUOTE]

No. I wouldn't know what to do with it once I started playing with CCSM.

Thanks anyways.

Yes, it is the super + m whole Screen inverted coloring that I lost.

---

### Post by Rasa1111 on 2011-04-13
it's very simple.

in CCSM , under "accessibility", You see "Negative"
[ATTACH]188901[/ATTACH]
Once you open it, there are only really 2 "options",
and they are the key bindings. 
[ATTACH]188902[/ATTACH]
 Maybe they got changed/messed up.
Also make sure the little checkbox to the left still says "Enabled"
Worth a look.

 Peace

---

### Post by mikodo on 2011-04-13
Rasa1111,

You're brilliant!

I had to install CCSM and follow your instructions. The settings I have were still the same as yours and when I pressed the super key + m it still opened the drop down menu of the indicator applet. So, I changed the key combination for Toggle Screen Negative to Super + v and I have the screen able to toggle between the normal and negative again! Yeh!

Now, today I started Saving my multiple windows I like to have open all the time (terminal,nano, a nautilus window and a window with an e-book I a using to learn bash with command line. We used to be able to save our current sessions in Ubuntu and shut down the computer after setting the session and when rebooted it would open the desktop as before. Well no more say the devs. I asked on this forum today, and was told that Suspend would save the desktop windows exactly as before and I found so does Hibernation, even with the computer unplugged. They both bring the desktop back to the original configuration as before! Yeh! I just wonder if it tends to screw up compiz as in my key combination for inversing the pages color. I guess I will see with future Hibernation reboots.

Anyways, thank you everyone!

Mike

---

### Post by mikodo on 2011-04-13
Oh boy! CCSM looks like fun.

Thanks. :)

---

### Post by Rasa1111 on 2011-04-13
haha! Hiyah Mike !:o 
you flatter me, thanks! :lol:
I am just a silly newb who likes to mess with lots of settings is all. lol :p

 Glad you got it solved! :D

I always just use suspend or hibernate also, whenever I want things to stay as is. 

 :)

Cheers!

---

