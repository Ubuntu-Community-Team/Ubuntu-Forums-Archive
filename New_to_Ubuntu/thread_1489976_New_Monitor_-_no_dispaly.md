---
title: "New Monitor - no dispaly"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by george3095 on 2010-05-21
I moved my Ubuntu computer to another desk to avoid sharing a monitor with another computer. During bootup, the BIOS screen is visible, followed by Ubuntu's white icon in the middle of the screen. Then,the login screen (text only, as usual) is briefly displayed; then, the screen goes dark. I KNOW that Ubuntu's running because, after a typical delay, the screen saver is activated, sending the monitor into standby mode. Moving the mouse causes the monitor's power lamp to go from amber to green. Obviously, I'm stumped; I don't know how to have the new monitor recognized. I will appreciate suggestions.

---

### Post by sydbat on 2010-05-21
> **george3095 said:**
> I moved my Ubuntu computer to another desk to avoid sharing a monitor with another computer. During bootup, the BIOS screen is visible, followed by Ubuntu's white icon in the middle of the screen. Then,the login screen (text only, as usual) is briefly displayed; then, the screen goes dark. I KNOW that Ubuntu's running because, after a typical delay, the screen saver is activated, sending the monitor into standby mode. Moving the mouse causes the monitor's power lamp to go from amber to green. Obviously, I'm stumped; I don't know how to have the new monitor recognized. I will appreciate suggestions.Let me see if I understand - you changed monitors, yes? Try going into the recovery mode (at the grub screen during boot up - it is the one with the OS options) and there should be an option to "fix x" or something similar. After it "fixes" the graphical interface, you should be able to boot into a normal gui.

Let us know if this works.

---

### Post by george3095 on 2010-05-22
Yep, you understood what I was seeing. Your suggestion did not result in a "fixit." From what seems to be a full-screen of Terminal, I was able to login. At this moment the cursor is at the prompt "george@Presario-Ubuntu:~$" and typing LS, gives me this: Desktop   Downloads   Firefox_wallpaper.png   Pictures   Templates   Documents   and example.desktop. So, it seems I'm communicating with Ubuntu, at some level.

---

### Post by sydbat on 2010-05-22
If you are still getting the text (george@Presario-Ubuntu:~$) type in ```
startx
```and see if that starts the gui.

Are you getting any error messages during boot? Might have something to do with the graphics card?

Also, if you plug the old monitor in, does it work?

---

### Post by george3095 on 2010-05-25
Sydbat, I'm looking Ubuntu, in all its glory, on the old monitor. Actually, the "old" monitor (an LCD) is newer than the one (a CRT) that gave me the problem. So, it would seem the video interface could not or would not work with the CRT monitor. But, now that's not important because I wanted to dump the CRT monitor anyway.

Thanks for jarring me loose. I "knew" the problem had to be between the video system and the monitor, but I hoped there could be a way to "force" the video and the monitor to come together. Not so. Moving the monitor was the answer. Thanks

---

