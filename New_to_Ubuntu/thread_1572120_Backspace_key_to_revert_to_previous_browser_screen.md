---
title: "Backspace key to revert to previous browser screen"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by mtonsbeek on 2010-09-10
Could some kind soul please remind me how you change the keyboard short cut to go back to a previous window in the browser.

I am on 10.04 and cannot find the relevant entry under System>Preferences>Keyboard Shortcuts

The default is Alt + left arrow but because I still dual boot into Windows regularly, I am so used to the backspace key.

Thanks.

---

### Post by Kixtosh on 2010-09-10
I don't know the answer to your question, but I do know that ALT + left arrow will also work in Windows to navigate back to the previous browswer screen. At least that way, if you can get used to using it and since you dual boot, it'll be the same in Windows and Ubuntu.

Actually, while we're on the topic, in case you don't know, ALT + F1 will pull up the applications menu. You can probably get the Windows key to do it as well (I think it's called "super"), but I haven't figured that one out.

It's interesting that on my other Linux laptop, running Xubuntu with LXDE (instead of regular flavored Ubuntu), several other Windows like shortcuts also work that don't work in Ubuntu:

- Win + D = desktop.
- Win + E = file explorer.

But then, when using the LXDE desktop environment (Peppermint, and Lubuntu also use it, as well as a few others), ALT + F1 does not seem to pull up the Applications menu! At least ALT + spacebar brings up the window size/move menu for both LXDE and Gnome (the "regular" Ubuntu desktop), as well as in Windows.

---

### Post by mtonsbeek on 2010-09-10
Thanks Kixtosh but the reason I like the backspace is that it is a one-fingered action instead of the Alt + Left Arrow needing 2 fingers/hands. 

I can keep the right hand on the mouse and zap back using the left hand on the backspace. I can navigate much quicker that way.

---

### Post by Kixtosh on 2010-09-10
^^^ Ah, yes! Are we not all creatures of habit?!

Hopefully some kind soul will come along shortly and put you out of your misery! ;)

---

### Post by Kixtosh on 2010-09-10
Hey! Maybe that "kind soul" is none other than my very own little self!

Try this thread solution for size, and let us know if it works!

[http://ubuntuforums.org/showthread.php?t=1316748](http://ubuntuforums.org/showthread.php?t=1316748)

If it does, mark your thread as solved please!

---

### Post by coffeecat on 2010-09-10
> **mtonsbeek said:**
> Could some kind soul please remind me how you change the keyboard short cut to go back to a previous window in the browser.

Do you mean the Nautilus file browser, or the Firefox web browser?

I can answer the latter but not the former.

In Firefox, type 'about:config' in the address bar. Dismiss the silly warning. Type 'back' in the filter, and look for 'browser.backspace_action' in the list. Change the Value to 0. You're done!

---

### Post by baddnady23 on 2010-09-10
Actually its pretty easy.

Open up firefox and in the address bar, type:
```
about:config
```

In the filter bar at the top of the window, type in backspace.  The following should then be displayed on the screen:
```
**Preference Name**              **Status**       **Type**        **Value**
browser.backspace_action     user set     integer     0
```
and its value is probably set to 1 or 2.  

Double click on that item and change the value to 0 and that should do it for ya!

---

### Post by natravis on 2010-09-10
In the address bar of Firefox, type ```
about:config
```
Click "I'll be careful" and then type "backspace" into the box (no quotes). The only option that should come up is  browser.backspace)action. If the value is 0, then I don't know what is going on with your computer. If the value is something other than 0, right-click on it and click Modify then type 0 (number not letter) and click Ok. Restart Firefox and test.

Edit: baddnady23 beat me to it. Oh well.

---

### Post by Kixtosh on 2010-09-10
Now it's my turn to throw some oil on the fire: can it be done in Chromium too, since that answer is only valid in Firefox?!

---

### Post by mtonsbeek on 2010-09-10
Aaaah.... I did not mention the browser did I. Sorry.
It is actually Google Chrome 6.0.472.55. Not Firefox and about:config gives me a blank screen.

---

### Post by Kixtosh on 2010-09-10
^^ He he!

"Great minds", and all that sort of thing ...

---

### Post by baddnady23 on 2010-09-10
[http://www.chromeextensions.org/appearance-functioning/backspace-as-back-for-linux-2/]("http://www.chromeextensions.org/appearance-functioning/backspace-as-back-for-linux-2/")

---

### Post by Kixtosh on 2010-09-10
Okay baddnady23, you ain't so bad! That seems to work perfectly, thank you so much! In case it saves a few clicks and searches within the extensions, try this link which might take anyone interested (including the O.P.) right there:

[https://chrome.google.com/extensions/detail/aeffggjddcchloadflonilaahpclmbnm?hl=en](https://chrome.google.com/extensions/detail/aeffggjddcchloadflonilaahpclmbnm?hl=en)

---

### Post by mtonsbeek on 2010-09-11
> **baddnady23 said:**
> [http://www.chromeextensions.org/appearance-functioning/backspace-as-back-for-linux-2/]("http://www.chromeextensions.org/appearance-functioning/backspace-as-back-for-linux-2/")

Thanks. That works nicely!

---

