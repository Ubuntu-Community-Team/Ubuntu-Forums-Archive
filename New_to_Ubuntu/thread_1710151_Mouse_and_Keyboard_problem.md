---
title: "Mouse and Keyboard problem"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by matthewcb on 2011-03-19
Hi,

I installed ubuntu 10.10 and installed latest updates as at 18th March.

I have XBMC and PCSX installed.

I now have an irritating problem - on bootup neither mouse nor keyboard work.

If I unplug them, and then plug back in again they work fine, but clearly this isn't a very satisfactory user experience...

Does anyone have any advice?  I have seen some suggestions of editing the xorg.conf file, but that did not work.

Thanks...

---

### Post by RBLevin on 2011-03-19
Two questions:
1 - Are they plugged into a USB hub or directly into the PC?
2 - Have you tried toggling your BIOS setting for "Legacy USB support" on or off?

---

### Post by matthewcb on 2011-03-19
Hi, they are plugged directly into PC (Acer R3700).

Tweaking BIOS doesn't work unfortunately.  Additionally, the keyboard works during boot up as the caps lock button toggles fine (light comes on keyboard), but as ubuntu uis booting, this facility is disabled.

Really odd, as they working just fine until yesterday.  I'm very new to Linux so struggling a fair bit.

---

### Post by RBLevin on 2011-03-19
What happens if you disconnect all other USB devices, put the keyboard and mouse into different USB ports, and reboot?

Also, what happens if you use a different keyboard and mouse?

---

### Post by matthewcb on 2011-03-19
Ok, tried both of those, here's what happened...

1. Used different mouse and keyboard (wireless) and the same thing happened.  The hardware is ok as the 'connect' function for both worked fine, just wouldn't work in ubuntu until I unplugged and then reattached.

2. Tried unplugging and insert into different USB ports.  I only have one other device attached - an MCE remote controller.  Also tried rebooting without the receiver for the remote being plugged in (and the keyboard mouse in different USB ports) and the same thing happened.

I'm truly stumped!

---

### Post by RBLevin on 2011-03-19
Hmmm. Strange indeed. A few more random thoughts:

1 - Disable all startup apps. Perhaps a startup app is messing with the keyboard (hotkeys, macro apps can do this). See Preferences | Startup Applications, uncheck everything, reboot.

2 - Does your BIOS have a setting for the USB keyboard support that offers a choice of "OS" or "BIOS" support? If so, toggle that.

3 - Try resetting your BIOS to its default settings. I'd also check and see if there's a flash BIOS update for your PC.

---

### Post by matthewcb on 2011-03-19
Hi,

Tried all those things (just checking if there's a BIOS update).

It doesn't feel like a BIOS problem though for what it's worth.

The keyboard works during the POST process, it's as it's loading ubuntu it seems to disable all usb recognition.

Like I said, it was working fine yesterday so at a loss to explain why it's suddenly doing this.

---

### Post by RBLevin on 2011-03-19
> **matthewcb said:**
> The keyboard works during the POST process, it's as it's loading ubuntu it seems to disable all usb recognition.

Long shot, but try this: [http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html](http://www.ubuntugeek.com/how-to-fix-usb-stops-working-problem-in-ubuntu.html)

---

### Post by matthewcb on 2011-03-20
Sadly that didn't work either I'm afraid.

Very frustrating!

---

### Post by RBLevin on 2011-03-20
If you boot from the Live CD, do you get the same behavior?

---

### Post by matthewcb on 2011-03-20
Don't have a DVD drive - I could try booting from the install USB?

I'm thinking perhaps the best thing is complete reinstall and don't accept updates...

---

### Post by RBLevin on 2011-03-20
Sure, that would work.

Booting the Live image would boot an older version. If you still have the problem using the Live image, then you know the problem was not introduced by an update.

Another thing to try is to set up a new user, logout, then login as that new user and see if you get the same behavior. If you don't get the same behavior, then you know if's something specific to your logon config.

No real fixes here, but the results might be illuminating.

---

### Post by matthewcb on 2011-03-20
Ran ubuntu from the usb and the mouse + keyboard worked fine.

So I'm guessing there's something in the updates that affected it.

As I didn't have a lot installed, I've decided to just do a complete reinstall.

Thanks for the advice though.

---

### Post by RBLevin on 2011-03-20
Complete reinstall? Isn't that a lot of work to solve a minor problem? Why not just tolerate it for a little while, and see if a future update reverses the problem? It's possible. Not that big a deal to have to reinsert the USB plug, is it? More of an annoyance. You might find after a few updates that the problem goes away. And even if you do a full reinstall, you might find that the automatic updates re-create the problem again, and you'll be right back where you started.

---

### Post by matthewcb on 2011-03-20
I guess so, but the intention is for the PC to be used as media centre by partner/daughter, so expecting them to unplug/replug on each boot is not very satisfactory.

Anyway, have done complete reinstall, installed nothing but did updates to check and... same problem.

So, will try again, but will not update this time.

Of course, now I'm very nervous about doing any updates!

---

### Post by RBLevin on 2011-03-20
Very strange. Well, good luck with it! I'm out of ideas!! :)

---

