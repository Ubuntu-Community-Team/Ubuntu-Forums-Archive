---
title: "My Ubuntu hang after lock the screen"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by blodstone on 2009-12-10
Hi, I just installed Ubuntu Karmic in my computer which use Intel 82845G board. Every time I lock the screen then leave it for about one or two hours, my Ubuntu stops responding and the screen goes black. I have to restart it by pressing restart button on my PC. Can somebody help me solve the problem?

---

### Post by mikewhatever on 2009-12-10
May I ask how you know it stops responding if the screen is black? Is you computer set to suspend to ram or to disk under power management?

---

### Post by Geoff918 on 2009-12-10
Your problem is more likely with the "sleep" or "hibernate" setting. The "locked screen" is probably just coincidental. I bet that if you walk away without the screen locked that it will still hang.

There are some guides related to this. Let me look them up and post some links for you. Links to follow in an edit soon.

Also, are you on a laptop or desktop?

*****

Found some information regarding enabling linux-backports-modules karmic (you can read more about backports and the Ubuntu definition of "stable" on the main website--link below).

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

That link has several items that hang on suspend / hibernate / resume.

Information about Backports:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by blodstone on 2009-12-10
Thx for all your reply.
@mikewhatever
I didn't set it to anything. I just locked the screen and go somewhere for one or two hours. After I get back, my computer just stop responding and the screen is pitch black. My PC is still on.
@Geoff918
I'm on desktop. I'll read your given references. Is it because my Ubuntu 9.10 is incompatible with my Intel? Because yesterday when I tried to install Linux Mint Helena, I  also get the same problem.

---

### Post by Geoff918 on 2009-12-10
Well, okay. One thing to note is that Mint isn't really a different distro.

Mint is just Ubuntu with a couple interface changes, essentially. If you do a uname -a from the CLI it will show you "Ubuntu..."

And, Ubuntu is from Debian--but it's modified enough to really be a different distro.

Let me look some more. I'm just getting back to this thread.

---

### Post by mikewhatever on 2009-12-10
> **blodstone said:**
> Thx for all your reply.
@mikewhatever
I didn't set it to anything. I just locked the screen and go somewhere for one or two hours. After I get back, my computer just stop responding and the screen is pitch black. My PC is still on.

Would it be more accurate to say that the screen doesn't wake up, so that you can't get to the GUI? I don't know what 'not responding' means in the sense you are using it. For example, when Firefox hangs, and you try closing it, a message appears saying it's not responding. Do you see similar messages? If so, how is it possible with the black screen?

---

### Post by Geoff918 on 2009-12-11
Mike raises a good point. Are you able to ctl-alt-F1 into a different login?

I suspect this really is a suspend / resume issue. It *is* possible to disable the power management settings that cause this.

One thing that may be happening is that the power management is disabling access to the peripherals you are using. E.g. if you have a USB keyboard and mouse and power management is turning off the USB root HUB--the system won't wake-up because the source of the UI (user interface) is "powered-down".

Do you have a USB mouse and keyboard? Does the system not respond on all input attempts (have you tried both the mouse and keyboard to wake the system)?

The second item is perhaps it IS waking up from these devices and the system is not sending the signal through to the video card which is *possibly* powered-down and/or that is not the case and the monitor itself is not waking up when a signal is coming from the video card.

(Complicated seeming, eh?) Best bet with any computer issue is to just try one of the early root potential problems. Test and see. If that doesn't change, move down the chain. :)

Do check your power management set-up in System - Preferences - Power Management

Maybe disable the power management altogether and see if that works. (Obviously unfriendly on the electo bill)

---

### Post by blodstone on 2009-12-13
@mikewhatever,@geoff918

I'm sorry for my late reply. I've been updating my linux using Update Manager for these two days. I was hoping that by updating it can solve my problem. But it didn't. 

What Mike said is true, I can't get back to my GUI after I locked my screen (sorry for my English, I'm not a native speaker). But recently, I found out that it wasn't the case. I left my linux for about 2 hours or so without locking anything, and when I got back to my Linux, it stops responding except for my mouse (I can see my mouse moving but nothing else can be clicked and keyboard didn't function also). 

I have set my power management settings to "never" except the screen that sleep when left idle for 30 minutes. Well, when I got back, my screen haven't sleep yet, so I suspect my linux hang before 30 minutes has passed.

---

