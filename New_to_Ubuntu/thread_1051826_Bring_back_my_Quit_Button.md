---
title: "Bring back my Quit Button"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-01-27
This is embarassing!

I stupidly removed my Quit Button from the panel...

Trying to get it back, I could not find it but I managed to "add to panel" a "Log-out" button, which looks the same but does not work the same way.
I now need to work through a series of screens  to shut down or restart etc & confirm all selections.

How can I get the good old function back, where 1 click on the button opened a screen to select Log-out, Switch off, Restart etc which then worked straight away without asking for confirmations?

A small thing, but I really appreciated that button!

Thanks for any help.

---

### Post by mhh91 on 2009-01-27
first,add the extra plugins from synaptic

you'll find more panel plugins for use then :)

---

### Post by prshah on 2009-01-27
> **2CV67 said:**
> 
Trying to get it back, I could not find it but I managed to "add to panel" a "Log-out" button, which looks the same but does not work the same way.


If you have the "Shut Down" in your Applications menu, you can drag-n-drop it into the taskbar, and you will get back the functionality you want.

---

### Post by 2CV67 on 2009-01-27
Thanks for both replies.

I don't have Shut-down in the Applications menu, nor anywhere else I looked so far, even in Trash...

Not sure what you mean by > first,add the extra plugins from synaptic

I am only trying to get back the normal Quit response...

---

### Post by 2CV67 on 2009-01-27
Oh NO!!

It looks like what I am getting now is the new "Improved" Intrepid log-out response.
[http://ubuntunext810.blogspot.com/2008/08/exit-strategy.html](http://ubuntunext810.blogspot.com/2008/08/exit-strategy.html)

This is AWFUL!

Can I get back to the beautiful previous log-out response?

---

### Post by mcduck on 2009-01-27
So what you want is the applet that has a drop-down menu which allows you to log out, switch to guest session and shutdown/reboot/suspend/hibernate? The one that is the default on fresh Ubuntu 8.10 install?

Right-click on the panel, select "Add to panel", find the "User Switcher"-applet & drag it to your panel.

---

### Post by 2CV67 on 2009-01-27
Ah - Thank you!

That gets me back to where I was this morning...
I suddenly had my name next to the Quit Button, which I don't want for several reasons, like publishing screenshots on forums!
So I right clicked on my name to "Remove from Panel" & lost the button too.
And couldn't find it anywhere - who would think of "user switcher" & why no Quit icon??

Now, thanks to your help, I got the button & name back.
Then I found I could select a neutral icon next to the Button instead of my name (but why any icon - I prefer nothing!).

So it looks as though I can now have a drop-down list which I need to read & select what I want, but at least I can get out in 2 clicks, which is good.

But as I am a GUI sort of person, I STRONGLY prefered the old (pre-Intrepid) system which was all done by big simple obvious icons.
Ergonomically, this is a surprising deterioration & I would like to re-instate the pre-Intrepid scheme if/when possible.

I often used that old Quit sequence to show people how much better Ubuntu was than Windows...

Thanks very much for your help.

---

### Post by 2CV67 on 2010-09-15
Bumping this, as I just spent a long time screwing around with the various Exit Modes from Lucid for a new user.

Man, this is bad!

I hope somebody can tell me that there is now (a long time after previous posts) a better solution available somewhere.

Unless I am mistaken, the default Quit system now is an Applet with User's name & what looks like a greyed-out blob, usually synonymous with 'disabled'?
The Stop button on anything should be big, red & obvious, shouldn't it?
Clicking on the grey blob produces an adjacent drop-down list with all the choices you could want. (Good)
Not in my ideal order (can't please everybody, of course) and without quick-identification icons.

I absolutely don't want my name on the screen, for all sorts of reasons.
So I removed it - but lost the Quit button at the same time.
I would never have been able to put it back, but I found a link [here]("http://ohioloco.ubuntuforums.org/showthread.php?t=1403531") saying how to put back the complete applet with name (called "Indicator Applet Session"!!) but also how to get the button without name > follow the above thread to add the session applet but add it twice and delete the first one with chat options and name of user. The second add will only add the power button..
Which seemed to work, until next login, when the name was back!

The User-Switcher applet mentioned in a previous post doesn't seem to handle Shut-Down or Re-Boot options.

So I abandoned that & tried adding just a button to the panel.
As far as I can see, if I need to be able to Logout & also to Shut Down, then I need 2 buttons.
Each of which opens a nice window with good big clearly-iconed choices.
But the windows open mid-screen, a long way from the Quit buttons.
And they ask for confirmation before acting.
This is too bad! 

Especially when earlier versions (up to Hardy?) had a (near) PERFECT system.
One button brought up one window with all the possible options, with big clear icons and no confirmations.

What I would like to see - & I hope somebody will tell me it is now possible - is:
One big red button (that I can customize if I want).
Which opens one menu.
Next to the button.
With a list of all reasonable options (that I can customize).
With clear icons for rapid homing.
Which do what they say without further confirmation (I am already at step 2 of the process. OK - make confirmation customizable if you like).

Or I would be very satisfied if I could just get back to pre-Intrepid behaviour, as illustrated [here]("http://ubuntunext810.blogspot.com/2008/08/exit-strategy.html") (see pictures & read comments at bottom).

Any hope?

Thanks!

---

### Post by prshah on 2010-09-15
> **2CV67 said:**
> the default Quit system now is an Applet with User's name & what looks like a greyed-out blob, usually synonymous with 'disabled'?

Actually, the "grey blob" with the cross is an indicator of your online status. It appears to the left of your user name. To the right is a power-off symbol (which varies depending on your theme). Usually, is is a light grey, but changes to red when a restart is required (Eg, after a kernel upgrade).

You can get your "big red button" which launches a dialog box with quit options using the "Shut down" applet. Right click a blank area of the taskbar, choose "Add applet" and look for "Shut Down...". When added, a bright red (almost scarlet) "power off" button appears on the taskbar. Clicking produces a dialog box with various power-off options.

Try it and see if it is satisfactory.

---

### Post by LowSky on 2010-09-15
i usually remove the logout icon, once removed a new menu item appears under the system portion of the menu.

---

### Post by hoss2001 on 2010-10-14
There is a "shut down" button. Right click the panel, and click "add to panel." The "shut down" button is almost to the bottom. Only it's gray instead of red, and only two functions, restart or shut down. I did my upgrade from the alternate i386 cd instead of online. (I have dialup) I don't know if that makes a difference. If you still want the logout option, you'll have to keep the little green guy too.

---

### Post by 2CV67 on 2010-10-14
I have slowly realized that the color (& design) of the various icons depends on the Theme (System > Preferences > Apprearance > Theme) you happen to be using. 
So one man's "grey blob" can be another's "green man"...

Having chosen a Theme, you can still tune your icon appearance (radically) in System > Preferences > Apprearance > Theme > Customize > Icons.

So color is not really a problem (once you realize that...).

What rests as an irritation is having to have 2 buttons if you want all the Logout/Switch/Restart/Shut-down options without your name on the screen.

It's an irritation & an incomprehensible step backwards, not a disaster.

---

