---
title: "Monitor problem black screen - how to fix with no xorg.conf"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by getut on 2009-09-16
I have put together a 32bit Jaunty desktop machine for a friend who has a Westinghouse LCD monitor.

His Jaunty machine works fine when connected to my Samsung LCD monitor, but when connected to his it boots to a black screen. Switching to a terminal works fine and he can see the text but switching back to the graphical terminal goes back to the black screen.

The same PC works fine on the Westinghouse in Windows. I'm sure its a refresh rate or resolution issue, but why isn't it detecting the monitor properly.

Can I force a complete re-detection if it thinks it is still connected to my Samsung? or any other recommended fixes?

---

### Post by getut on 2009-09-18
bump... please help.

---

### Post by wojox on 2009-09-18
What do you mean by no xorg.conf file?

---

### Post by getut on 2009-09-18
> **wojox said:**
> What do you mean by no xorg.conf file?

Well.. its just a shell of its former self in older versions of Ubuntu and linux. There really isn't much in it and it doesn't do much.

I think it is all detected in real time by the hal now.

Which brings my question. The machine with the problem was installed while connected to a samsung monitor. It works fine if I bring it back to that monitor. The text mode sessions work fine on the westinghouse monitor but the graphical session is just black.

The monitor was working fine with that same PC running windows. So between the fact that it displays the text mode fine and the fact that it was working with windows, I have no reason to suspect the westinghouse monitor is bad.

Which only leaves a resolution or refresh rate issue with the PC itself while it is running Ubuntu jaunty. But since there are really no settings to change in the xorg.conf, I don't know how to begin to resolve the issue since I can't see anything to change anything in the graphical session while it is connected to the westinghouse.

---

### Post by mgmiller on 2009-09-18
You need to redetect the monitor to make sure its refresh rates are set properly.
On boot up, when it pauses for a few seconds on the screen that shows the kernel versions, use the up down arrow keys to select the second line with the "recovery kernel"  That one will allow you to fix it.

When it finishes booting, you will have a screen with a few simple choices, select the last one, which is "xfix" fix the x server.

That will redect both the video card and the monitor.

It will only take a few seconds to do it's thing and will drop you back to the same screen you started at.

Just tell it to boot normally, I think that is the first choice that will be high lighted by default anyway.

It should now work, except, it you had any proprietary drivers installed, they will be back to open source.  So, if you need to, just reload the drivers from System > Administration > Hardware Drivers

You should be good to go now.

---

