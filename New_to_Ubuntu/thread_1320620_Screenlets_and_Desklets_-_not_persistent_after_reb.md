---
title: "Screenlets and Desklets - not persistent after reboot"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-11-09
Last night, I spent some time adding some screenlets and desklets to my set-up.

Today, I've booted up my PC and only one of them is there.

Is there some flag in the Properties of each xxxxxlet that tells it to persist? If so, what is it usually called?

Or is there some other setting that I must have overlooked?

And another dumb question - what is the difference between a screenlet and a desklet? They seem pretty much identical to me!

---

### Post by bawilson2 on 2009-11-12
Might be another way to do it but what I'd try is going into System->Preferences->Startup Applications->Options and click on the "Remember Currently Running Applications" when you have your desktop exactly as you'd like it to boot up.

---

### Post by Roger Allott on 2009-11-12
> **bawilson2 said:**
> Might be another way to do it but what I'd try is going into System->Preferences->Startup Applications->Options and click on the "Remember Currently Running Applications" when you have your desktop exactly as you'd like it to boot up.

Thanks for the suggestion, but it didn't work.

My settings for screenlet options are as the attached screenshot. I have ticked the 'Enable Widget Layer' on CCSM.

But I still only get to see my screenlets when I press F9, and they vanish as soon as I click on just about anything.

If anyone can suggest what I'm doing wrong, I'd be very grateful for input.

---

### Post by JJNova on 2009-11-12
Hello Roger,

I'm just going to show you how I manage to get screenlets to start automatically when logged in. 

If you navigate to Applications > Accessories > Screenlets, you will be presented with the screenlet manager [Attached]. 

As you can see in the screenshot, the highlighted portion at the bottom left has two checkboxes. The Start/Stop box will create a running session of the selected screenlet, where the "Auto start on login" will, well, automatically start on login ;)

I hope this has been helpful. I am running Ubuntu 9.10, but have been upgrading for the last couple of releases, so your mileage may very. Please let us know if this is successful.

-jj

---

### Post by Roger Allott on 2009-11-13
> **JJNova said:**
> Hello Roger,

I'm just going to show you how I manage to get screenlets to start automatically when logged in. 

If you navigate to Applications > Accessories > Screenlets, you will be presented with the screenlet manager [Attached]. 

As you can see in the screenshot, the highlighted portion at the bottom left has two checkboxes. The Start/Stop box will create a running session of the selected screenlet, where the "Auto start on login" will, well, automatically start on login ;)

I hope this has been helpful. I am running Ubuntu 9.10, but have been upgrading for the last couple of releases, so your mileage may very. Please let us know if this is successful.

-jj

Thanks for the tip, but both of those were already ticked on my screenlets manager.

---

### Post by corncob on 2009-11-13
> **bawilson2 said:**
> Might be another way to do it but what I'd try is going into System->Preferences->Startup Applications->Options and click on the "Remember Currently Running Applications" when you have your desktop exactly as you'd like it to boot up.

Try not going to the Options tab but stay on the Startup Programs tab.  There's an ADD button that lets you enter the program or browse to select it.  I'm running a fresh install of 9.10 -- I need to update my profile.

---

### Post by Roger Allott on 2009-11-14
> **corncob said:**
> Try not going to the Options tab but stay on the Startup Programs tab.  There's an ADD button that lets you enter the program or browse to select it.  I'm running a fresh install of 9.10 -- I need to update my profile.

I've looked at that and all of my screenlets are already in the list, and all are ticked to load up at start.

---

### Post by corncob on 2009-11-14
> **Roger Allott said:**
> I've looked at that and all of my screenlets are already in the list, and all are ticked to load up at start.

Sometimes I think something isn't opening but its opened minimized and I have to click the icon on the task bar.  Clicking the link on the email to get here was the latest example.  "Where's ubuntuforums?", I said.  I don't know why this happens; its not the usual.  Also I've had things open in the other work space and didn't notice it until after I got a little exasperated.
Nothing to do with this, I'm sure, but kinda a funny story.  I have a dual monitor system in the guest house.  The guy that was staying there didn't see the need for two monitors and turned one of them off and then wondered what happened to half the stuff.

---

### Post by BigSilly on 2010-10-24
This is happening to me too, exactly the same as the OP. I've already posted elsewhere about it. Can anyone help?

---

### Post by fubofo on 2011-04-25
The 'Enable Widget Layer' option needs to be unchecked.

This option actually adds the 'screenlets' to an invisible layer (the widget layer) that is used by compiz when pressing F9.

The widget layer can be configured in compiz settings manager to display with key combinations or touching specific edges of screen.

Or

The screenlets can be configured to be on all desktops and below all windows and not on an invisible widget layer.

Hope this helps.

---

