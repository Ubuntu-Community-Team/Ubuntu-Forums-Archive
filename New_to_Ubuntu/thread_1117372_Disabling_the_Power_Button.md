---
title: "Disabling the Power Button"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by alanfang on 2009-04-05
I have an msi wind, which has a small power button you can press to turn it off. I want to disable this button entirely. I have seen various tutorials involving editing /etc/acpi/events/powerbtn and tried them, but they seem to have done nothing. Thanks.

---

### Post by RedSingularity on 2009-04-05
Go to System>Preferences>Power management.

Under the "General" tab.

---

### Post by alanfang on 2009-04-05
All that does is allow me to have it ¨Ask Me" or go directly to shutdown. I just want to disable it entirely.

---

### Post by RedSingularity on 2009-04-05
Ohh im sorry i got it mixed with the "Suspend" button.......i am not exactly sure how you would go about disabling it completely.  May i ask why you want that?

---

### Post by alanfang on 2009-04-05
I know some less than mature people who find it funny to hit the power button, followed by enter, to shutdown my computer while I'm working.

---

### Post by RedSingularity on 2009-04-05
Ohhhhh very nice!  I happen to know a few of those "funny men" myself.  And unfortunately i live in the same house as them.  ;)

---

### Post by alanfang on 2009-04-06
Anyone have any ideas for this?

---

### Post by Malalo on 2009-04-06
One thing you could do is open up your machine and remove the wiring between the button and the motherboard...

---

### Post by mikechant on 2009-04-06
Given that you don't want these people messing around, just disabling the shutdown function isn't really enough. They could do something else stupid instead. 
Perosnally I would use the screen lock function.
I believe you can just hit CTRL-ALT-L to invoke it (not at my Ubuntu machine at present so I can't test it).

---

### Post by LowSky on 2009-04-06
Lock screen will not stop a poweroff command from the power button, as that command is issued with the BIOS. Best option is to go to BIOS and change the power off functiion, from off to suspend ( the the laptop even has that option. that way if they do hit is it wont tbe that bad.

---

### Post by alanfang on 2009-04-06
I have it set to suspend right now, but it's still a hassle when I'm right in the middle of working.

Screen lock won't really work because it generally happens while I'm working.

---

### Post by mikechant on 2009-04-09
If this sort of thing is happening when you are sitting there working, it sounds you need more of a people solution than a technical solution.
Suppose you do disable the power button.
What's to stop them from pulling out the power cord at the socket? Or finding something else equally stupid and annoying to do?

This sort of thing shouldn't be tolerated in any workplace, school or college environment. And if it's 'friends' or family can you not convince them that it really isn't funny anymore? Or repeatedly do the same or equivalent thing to them until they agree to stop? Or smack their hand with something solid?

However, getting back to the technical anyhow, I would suggest replacing the button with a key lock. These used to be common but I bet you can still get them for use in certain commercial environments.

---

### Post by exactt on 2009-06-05
anyone found a solution for this problem yet?

p.s. please stop asking stupid "why"-questions!

---

### Post by exactt on 2009-06-05
found it at [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/156645](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/156645)

"you can disable it via gconf-editor, just set /apps/gnome-power-manager/buttons/power to "nothing". you must set this key for each user."

---

### Post by mikechant on 2009-06-05
> p.s. please stop asking stupid "why"-questions!

You know, people are more likely to think about and provide good answers to your problem if you take a few seconds to answer their "stupid" questions. There is such a thing as natural human curiousity.
Anyhow, I think you're going to find that requirements like yours nearly *always* lead to questions as to why you want to do this.

---

### Post by exactt on 2009-06-05
sorry if i have been a bit harsh... but i could also take it the other way round and suggest one could spend a moment and realize that the person has a good reason to ask the question. and that there are many possible reasons worth asking...

anyway it is just annoying to read ten postings that don't bring yourself closer to the answer and just steal your time...

---

