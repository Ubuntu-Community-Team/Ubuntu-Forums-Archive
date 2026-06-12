---
title: "Compiz, part II."
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Blåbär on 2009-02-24
Hello there!

I recently tried to install compiz, but to no avail. I posted my problem in another, older thread, stating that I wasn't even able to enter the compiz fusion icon-settings window. That's been resolved by now.

The new problem is that it doesn't seem to want to render the new fancy settings. Ubuntu won't answer to the standard keybindings or load any of the features. When I do a ctrl+c, ctrl+c in a terminal, all windows freeeze. To solve that problem I have to run compiz from the menus, and hit alt+2 and do a metacity --replace from there.

This is all very confusing, and I'm as new as it gets when it comes to linux/ubuntu. I don't even know what info you guys might need in order to help me, so please let me know if I sh/could look for something else.

I'm running on 8.10, 64 bits.

Thanks,
B.

---

### Post by Therion on 2009-02-24
> **Blåbär said:**
> I recently tried to install compiz, but to no avail. I posted my problem in another, older thread, stating that I wasn't even able to enter the compiz fusion icon-settings window. That's been resolved by now.
Okay, we need to clarify a few things here first.

1.  Compiz-Fusion is already installed in 8.10, so you don't need to install anything further.

2.  The Compiz-Fusion Icon is a totally separate application from Compiz-Fusion itself.

We need to be clear about these things so nobody gets confused.

> **Blåbär said:**
> The new problem is that it doesn't seem to want to render the new fancy settings. Ubuntu won't answer to the standard keybindings or load any of the features. When I do a ctrl+c, ctrl+c in a terminal, all windows freeeze. To solve that problem I have to run compiz from the menus, and hit alt+2 and do a metacity --replace from there.
When you go to System/Preferences do you a menu item for "Advanced Desktop Settings"?

What sort of graphics chipset or video card does your PC have installed?

---

### Post by Blåbär on 2009-02-24
I do not have any 'advanced desktop settings'-option, only the compizconfig settings manager.

I have "HD48070 512mb GDDRS", from the ATI radeon HD 4800 series.


What I "installed" was a compiz application from add/remove programs, via the applications-menu.

---

### Post by Therion on 2009-02-24
> **Blåbär said:**
> What I "installed" was a compiz application from add/remove programs, via the applications-menu.
Okay just for clarification it sounds like you installed the Compiz-Fusion Icon application, using Add/Remove.  That application puts an icon on your Gnome panel that allows you to choose your Window Decorator, Window Manager and so forth.  We can ignore that for now.

> **Blåbär said:**
> I have "HD48070 512mb GDDRS", from the ATI radeon HD 4800 series.
Cool.  Have you installed the Restricted Driver for your video card?  That's critical to using Compiz.

---

### Post by Blåbär on 2009-02-24
I haven't installed anything, just picked and pointed at a computer store, and they set it up for me. Hehe.

edit: Maybe I should mention that they set it up with xp, by my request. There on and forth I configured the PC myself, adding ubuntu.

---

### Post by Therion on 2009-02-24
> **Blåbär said:**
> I haven't installed anything, just picked and pointed at a computer store, and they set it up for me. Hehe.

edit: Maybe I should mention that they set it up with xp, by my request. There on and forth I configured the PC myself, adding ubuntu.
Okay that's cool.  Most likely you need to install what's called the Restricted Driver for your video card so Ubuntu can use it to its full potential.

Here's the documentation on how to do that:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Restricted_Drivers_Manager)

---

### Post by Blåbär on 2009-02-24
Ok, done. That went surprisingly smooth...

---

### Post by Therion on 2009-02-24
Well when you do it the Ubuntu way, it typically is.  Typically.

Anyway, glad it went well.  You've rebooted since the install of the driver, correct?  You should have been prompted to do that.

Now we just need to ascertain what it is you want Compiz to DO for you.  What kind of things are you trying to set up?

---

### Post by Blåbär on 2009-02-24
Restarted and fresh.

You're saying there's nothing I need to install when it comes to compiz?

I'd like to play around with the graphical options, the cube and what not. I don't really know everything it's got to offer.


Ahoy, just got an error message, erh not, got a confirmation saying that the computer's using my ATI card, it seems. Good news. ;)

---

### Post by Blåbär on 2009-02-24
Ok, so it's all up an running now. Thanks a bunch for helping me out.

I'll try to explore compiz a little bit now, maybe I'll hassle you if I run into some problems or can't seem to hook it up with certain gadgets.

Thumbs up.

---

### Post by Therion on 2009-02-24
> **Blåbär said:**
> Restarted and fresh.
Good.  Now you're ready.

> **Blåbär said:**
> You're saying there's nothing I need to install when it comes to compiz?
I think you're good to go at this point.  Do you have CCSM (Compiz Config Settings Manager) in your System/Appearances menu?  If you do, you're good to go.  If not the tutorial below will show you how to install it.

> **Blåbär said:**
> Ahoy, just got an error message, erh not, got a confirmation saying that the computer's using my ATI card, it seems. Good news. ;)
That's normal.  And the bubble will go away eventually.

> **Blåbär said:**
> I'd like to play around with the graphical options, the cube and what not. I don't really know everything it's got to offer.
Roger that.  You can start with this tutorial, and meanwhile I'll find an old post of mine that will help.  Start with this:

[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

You don't need to install CCSM I don't think, so you can skip that part unless you don't.  If you don't have it already, the guide will show you how to install it and then walks you through setting up some fun stuff.  That should keep you out of trouble for a few.  Back in a minute with more.

Okey doke... Here's the meat of my earlier post:

If you want to show off some cool effects, try this...

Go back to the Animations plugin and open it.

You should be on the "Open Animation" tab (there should be a row of tabs across the top of your menu at this point).

Make sure all the little tic-boxes down below in the "Random Effects Pool" are ticked "On".

Click on the first animation item in the list of three that you have. It'll say "Fade" or some such (I've changed mine and I don't recall what the defaults are).

A new "Edit" dialog box will open.

From the "Open Effect" drop-down menu, select "Random".

From the "Duration" drop-down menu in the "Edit" dialog box, change the setting from 150 to 600 using the slider or by typing in the numbers.

Go back to the top row of tabs and open the "Close Animation" tab.

Repeat the steps above for this tab... Go to the "Open Effect" drop-down menu, select "Random" etc.
Repeat the steps above for the "Minimize Animation" tab just like you did with the first two tabs (same thing, all three tabs).

Noooow start opening, closing and minimizing and maximizing some windows and see what happens.

If the effects are too slow for your taste's, you can decrease the effect duration (I told you to use 600) and speed up the animation. A duration setting of 300, for example, will make them "go" twice as fast.

If you want the same animation every time you close a window or maximize a window or something, you can choose one particular animation for that action from the drop-down menu instead of using "Random" like we do here. You could choose to have the "Glide" animation display EVERY time you minimize a window for example.

Getting the idea now?

---

### Post by Blåbär on 2009-02-25
I only have the compizconfig settings menu, no advanced desktop settings which you mentioned earlier.

I also tried to follow your "meat post", but it failed pretty fast since I only have one "tab" under animations, which is "effect settings". Under which I can find things called, in order of appearance: airplane, beam, burn, domino, explode, fold, glide 3, razr, skewer. None of which I got running. Ahem.

I'd also like to replace the bottom/roof of the cube, to either transparant or alternatively pictureX.

Any ideas?

Edit: Solved, by realizing I was in the wrong animations setting file. (y)

---

