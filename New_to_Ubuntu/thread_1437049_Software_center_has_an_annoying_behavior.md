---
title: "Software center has an annoying behavior"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by plasmafox on 2010-03-23
I just installed ubuntu from an 8.10 disk i had lying about, patched it up to 9.10 karmic, and was playing around with the available apps. This isn't the first time I've used ubuntu, but I don't have very much experience with I can handle console and am pretty comfortable with computers but I don't know how to compile things.

Anyway, I wanted to play around in the Software Center the way I did on my friend's iPhone at one point, going through and trying all the different games and programs. But it's frustrating because every time you hit "install" on one program it "helpfully" switches to a different screen listing current downloads titled "in progress"- this screen is of no help to me, especially since I have fast internet and most programs finish downloading before the screen even comes up. Put short, I want to make it not do that and instead go back to the category list. I did a quick search of the forums and while I only checked 10 out of 250 pages I didn't see something related.

I figure there's just a settings file to be edited or a terminal command i need to fire off but I haven't the faintest idea how to find it.

---

### Post by slakkie on 2010-03-23
I haven't tested software center in Lucid, but I do know it had some UI changes. I agree on your comments though, it is somewhat irritating.

---

### Post by mpt on 2010-03-23
Hi, I’m the lead designer for Ubuntu Software Center.

> **plasmafox said:**
> But it's frustrating because every time you hit "install" on one program it "helpfully" switches to a different screen listing current downloads titled "in progress"- this screen is of no help to me, especially since I have fast internet and most programs finish downloading before the screen even comes up. Put short, I want to make it not do that and instead go back to the category list.

I’m sorry about that. We did it that way in 9.10 because we did not have time to make it show installation progress either on the application screen itself, or in the department screen. We could show progress only in one place, so we showed it in an “In Progress” screen and switched to that screen whenever it was the only thing happening.

In Ubuntu Software Center 2.0 in Ubuntu 10.04, there will still be an “In Progress” screen, but progress will also be shown on the software item screen and in software listings. So we won’t switch to the “In Progress” screen automatically any more.

---

### Post by Drizzt611 on 2010-03-23
Sorry if this is easily fixable, but I'm new to Ubuntu (literally I just installed it an hour ago). For some reason, whenever I use the software center to download something, it says "Waiting for other software managers to quit" and I've looked around, but I haven't found a way to fix it.

---

### Post by Gadgetech on 2010-03-23
> **Drizzt611 said:**
> Sorry if this is easily fixable, but I'm new to Ubuntu (literally I just installed it an hour ago). For some reason, whenever I use the software center to download something, it says "Waiting for other software managers to quit" and I've looked around, but I haven't found a way to fix it.

The Update Manager was probably already running. You might have noticed a new icon (looks like a star with an arrow pointing down) in the system tray in the upper right corner. This runs automatically from time to time to check the servers for new updates. The issue should clear itself up after a few minutes.

If there is an update manager window that's open, make sure to close that first (assuming it's done doing it's thing). Then open up the Software Center.

---

### Post by Drizzt611 on 2010-03-23
> **Gadgetech said:**
> The Update Manager was probably already running. You might have noticed a new icon (looks like a star with an arrow pointing down) in the system tray in the upper right corner. This runs automatically from time to time to check the servers for new updates. The issue should clear itself up after a few minutes.

If there is an update manager window that's open, make sure to close that first (assuming it's done doing it's thing). Then open up the Software Center.
Unfortunately, I think it's a little more complicated than that. The system tray only has the standard things, and the only window I have open is Firefox. 
I will restart my computer and see if that fixes it.

---

### Post by Drizzt611 on 2010-03-23
> **Drizzt611 said:**
> . 
I will restart my computer and see if that fixes it.
Sadly, that did nothing.

---

### Post by plasmafox on 2010-03-26
> **mpt said:**
> Hi, I’m the lead designer for Ubuntu Software Center.



I’m sorry about that. We did it that way in 9.10 because we did not have time to make it show installation progress either on the application screen itself, or in the department screen. We could show progress only in one place, so we showed it in an “In Progress” screen and switched to that screen whenever it was the only thing happening.

In Ubuntu Software Center 2.0 in Ubuntu 10.04, there will still be an “In Progress” screen, but progress will also be shown on the software item screen and in software listings. So we won’t switch to the “In Progress” screen automatically any more.

 Thanks for the explanation! That's a far better answer than I was hoping for.

---

