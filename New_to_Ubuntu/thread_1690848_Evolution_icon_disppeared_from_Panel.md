---
title: "Evolution icon disppeared from Panel"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by wonfineday on 2011-02-19
The icon for Mail/Evolution has disappeared from Panel. :(

I created a launcher for Evolution figuring that might work... well it does launch Evolution but the notifications for new mail don't show up, and none of the other stuff... 

Please help. How can I get my Email/Chat notification icon back on Panel? 

Thanks

---

### Post by bwallum on 2011-02-19
The Evolution envelope icon is part of the Indicator Applet. Let's try to reinstall it. 

Open a terminal (Applications>Accessories>Terminal)

You should get a console window open with a prompt ending in a $ sign.

At the prompt type in:-```
killall gnome-panel
```then press the return key. Does the envelope icon return?

---

### Post by suomalainen on 2011-02-19
Aren't you suppose to be able to go to Applications--->Office and then left click on Evolution and choose "add launcher to panel" ????

---

### Post by wonfineday on 2011-02-19
> **wonfineday said:**
> The icon for Mail/Evolution has disappeared from Panel. :(

I created a launcher for Evolution figuring that might work... well it does launch Evolution but the notifications for new mail don't show up, and none of the other stuff... 

Please help. How can I get my Email/Chat notification icon back on Panel? 

Thanks

That didn't work :(

---

### Post by wonfineday on 2011-02-19
> **suomalainen said:**
> Aren't you suppose to be able to go to Applications--->Office and then left click on Evolution and choose "add launcher to panel" ????

That was the first thing I tried... even before I posted here... 

One new thing about it is that I now have a "[myusername]" button where the email icon used to be... maybe related... maybe not...?

---

### Post by howefield on 2011-02-19
Check that you have the indicator-me package installed.

---

### Post by bwallum on 2011-02-19
Wonfineday, did you try 'killall gnome-panel' in #2? If so what happened?

---

### Post by philinux on 2011-02-19
In these cases it's much easier and quicker to reset the panels back to their default settings.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Then

```
killall gnome-panel
```

Of course you lose any customisations.

---

### Post by wonfineday on 2011-02-22
> **bwallum said:**
> Wonfineday, did you try 'killall gnome-panel' in #2? If so what happened?

I'd best describe it as the Panel flickerd: it was closed and then automatically restated. Now what? :(

---

### Post by wonfineday on 2011-02-22
> **howefield said:**
> Check that you have the indicator-me package installed.

It is indeed installed. Now what?

---

### Post by bwallum on 2011-02-22
> **wonfineday said:**
> I'd best describe it as the Panel flickerd: it was closed and then automatically restated. Now what? :(
That was the panel repainting. It should now show a small envelope icon (providing you have Evolution installed). Can you see the small envelope icon?

---

### Post by wonfineday on 2011-02-22
> **bwallum said:**
> That was the panel repainting. It should now show a small envelope icon (providing you have Evolution installed). Can you see the small envelope icon?

No I don't... :( 
I did manually add evolution to the panel but that only shows an open envelope icon all the time. 

Earlier I used to see the envelope, when I clicked on it I had the option to chat, mail etc. and when I received new email it the icon showed that as well. Now none of that... :( 

I'd really appreciate some way of being able to get back to that state...

---

### Post by bwallum on 2011-02-22
> **wonfineday said:**
> No I don't... OK, I'm sure we can. First let's get clear on the icons. The icon you put into the panel is a 'shortcut' to start the programme. The little black (green when mail arrives) icon is a context sensitive system indicator attached to which are context sensitive menus.

The indicator that shows your email also shows your sound. Can you see a speaker icon? If not you need to reinstall the Indicator Applet.

To do this right click on a blank area of the panel and select Add to Panel...

Then scroll down the list of applets until you find Indicator Applet. Highlight with a left click then click on the Add button.

Does that restore your envelope icon?

---

### Post by wonfineday on 2011-02-22
> **bwallum said:**
> OK, 
The indicator that shows your email also shows your sound. Can you see a speaker icon? If not you need to reinstall the Indicator Applet.

To do this right click on a blank area of the panel and select Add to Panel...

Does that restore your envelope icon?


Duh! Part of me feels so stoopid, but the other part of me is a true noobie on Ubuntu. All I had to do was re-install the Indicator applet. I suspect at some point I must have removed the speaker (because its not a setting I mess with). in the process I removed the indicator applet.

THANKS for your help bwallum!!

---

### Post by wonfineday on 2011-02-22
Now if only I could get the icons to be all arranged in a manner I like... e.g. I have the Network icon on the far-right with no option to "Unlock" or "Move" it

Thanks!

---

### Post by bwallum on 2011-02-22
Don't worry, no question is ever stupid, it actually helps the devs see where they need to be a bit more intuitive for the newcomer. You're doing well for 19 beans! Keep the questions coming.

---

### Post by bwallum on 2011-02-22
> **wonfineday said:**
> Now if only I could get the icons to be all arranged in a manner I like... e.g. I have the Network icon on the far-right with no option to "Unlock" or "Move" it  ..Thanks!

That sounds like a new thread topic. Try starting a new thread with a subject something like:- How do I fix top panel icons and remove the options to Unlock and Move?

I don't know the answer, there may be some customisation for top panel menus or not.

Good luck!

---

### Post by bwallum on 2011-02-22
If you are into personalised menus here's a googled return that may be of interest:-
[http://helpdeskgeek.com/linux-tips/change-the-panels-in-ubuntu-to-look-and-act-like-the-windows-taskbar/](http://helpdeskgeek.com/linux-tips/change-the-panels-in-ubuntu-to-look-and-act-like-the-windows-taskbar/)

---

