---
title: "Suspend shortcut just shuts off the monitor (mini 9)"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Ru$$i@N on 2009-06-26
Hi.

I like the netbook remix, just need to work out some minor problems that i have with it.

Ok, i have a dell mini 9 with a recently installed UNR 9.04. I can suspend from the shutdown menu, and that works fine, but I can't suspend from a shortcut for some reason.

What i did was to change the shortcut, in Preferences->Keyboard Shortcuts, for Suspend to fn+1 (which is the suspend button). The shortcut value displays XF86Sleep, seems normal. I rebooted and tested it out. The shortcut only causes the screen to shut off but not suspend.

Also, if anyone knows, how can i set suspend on lid close?

Thank you much,


Ru$$i@N

---

### Post by Ru$$i@N on 2009-06-26
bump

---

### Post by mgmiller on 2009-06-27
This is S1 vs S3 sleep.  When you give it the XF86Sleep command it enters S1 sleep which puts the cpu, memory and drives into a low power mode and shuts off the monitor.  My Lenovo s10E does the same thing.

On closing the lid, it enters S3 sleep, which is barely powering cpu and ram and is a much lower energy state.  Not quite off, but close.

To get it to do this on lid close, go to: System > Preferences > Power Management
You can select different options for when on AC power and Battery power by clicking on the appropriate tab.  I have mine set to "Suspend" when laptop lid is closed.

If you want to, instruct the icon to alwayw be visible in the top panel by going to the General tab and in the Notification Area, Tick the "Always display an Icon" button.

The XF86Sleep command will allow the netbook to awaken from and external keyboard, the S3 sleep will not.

I don't know the command to force it to do S3 sleep from a keyboard command.  But once you google around a bit, you should find it.  You can then create a custom keyboard command at the bottom of the Keyboard Short cuts Menu.  Just click Add and put in what you want.

---

### Post by Ru$$i@N on 2009-06-27
Thanks! That helped a lot.
For some reason until recently i couldn't see suspend and hibernate options for AC and battery power on lid close, but now it's there and works perfectly.

Apparently, setting the machine to suspend on lid close also fixed the keyboard shortcut! :)

---

