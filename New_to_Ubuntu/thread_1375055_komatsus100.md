---
title: "komatsus100"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by komatsu100 on 2010-01-07
I have Windows XP and Ubuntu 9.10 running on a Acer Aspire 3000. 
I can not log into Ubuntu, it seem something has happened to the splash screen.  I will open unto splash screen is suppose to open and them everything goes blank.  I am needing to get Ubuntu started, because I have some doc. there I am needing.

---

### Post by halitech on 2010-01-07
was it running previously and it did some update that stopped it from working?

---

### Post by -kg- on 2010-01-07
[LIST]
[/LIST]

Depending on how urgently you need access to the doc(s), you could boot to the Live CD and extract it with that.

If you have access to Windows, you could copy the doc(s) to the Windows partition and deal with it with Windows until you can get Ubuntu back on track.  Otherwise you could copy it to a flash drive or something and transfer it (or them) to another computer.

---

### Post by komatsu100 on 2010-01-07
Yes last night the update manager do a update, and it wanted to restart, but I was ready to quit, so I just shut down for the night. This morning it boots up to spash screen and then a blank screen.

---

### Post by halitech on 2010-01-09
from what I can tell you have an SiS Mirage 2 Shared video memory adapter. It might have updated the video card drivers which has messed up your display. when the unit is booting, can you select Single User mode and run xfix to try and resolve the issue?

---

### Post by komatsu100 on 2010-01-09
I am the only user of so I am the only user, but I still don't how to run xfix, could you tell me how to do that?   Thanks for all the help.

---

### Post by tom.swartz07 on 2010-01-09
> **komatsu100 said:**
> I am the only user of so I am the only user, but I still don't how to run xfix, could you tell me how to do that?   Thanks for all the help.

When you boot, select (recovery mode) rather than the regular version. This will allow you to select xfix.

---

### Post by komatsu100 on 2010-01-09
When I select (recovery mode) all I get is resume, clear, dpkb, (which is to repair a package), netroot,and root.  I have tried all of these and it hasn't helped any. I am new to this and if you could give me a command when I am in one of these modes it would sure help me.  It get fusterating when you know so little about something you are trying to use.  
Thanks a lot for any information.

---

### Post by halitech on 2010-01-10
if you select root does it allow you to type something in? if it does, type in
```
xfix
```

---

### Post by komatsu100 on 2010-01-10
I typed in xfix in root, and it gave me back a command that it was not a command it understood, I even used sudo-apt get and it still said it was not a good command.  I was about to quit MS windows but if Ubuntu is going to leave me this high and dry, I am giveing it second thought. 
I went to a broadband wired connection and typed xfix in root, it still said it was a bad command.  But I then tried to log onto kernel 9.10 and it did. But when I went back to my wireless connection it wouldn't log back in to kernel 9.10, I had to go back to the wired broadband connection to get log back in.  But at the log in screen I got a error message that the configuration default for GNOME power manager have been installed incorrectly.  See your Admirations team."
Thanks for the help you have been so far, I can at least down load the doc. I was needing.  But if you can tell me what to use from terminal or some other fix, I will try to get loged back in.

---

### Post by komatsu100 on 2010-02-04
> **komatsu100 said:**
> I typed in xfix in root, and it gave me back a command that it was not a command it understood, I even used sudo-apt get and it still said it was not a good command.  I was about to quit MS windows but if Ubuntu is going to leave me this high and dry, I am giveing it second thought. 
I went to a broadband wired connection and typed xfix in root, it still said it was a bad command.  But I then tried to log onto kernel 9.10 and it did. But when I went back to my wireless connection it wouldn't log back in to kernel 9.10, I had to go back to the wired broadband connection to get log back in.  But at the log in screen I got a error message that the configuration default for GNOME power manager have been installed incorrectly.  See your Admirations team."
Thanks for the help you have been so far, I can at least down load the doc. I was needing.  But if you can tell me what to use from terminal or some other fix, I will try to get loged back in.

It is the video drivers because I can type in my log in password and the hard drive lite will lite back up and stay on about as long as it does when I can log on with the screen lit up. Can anyone help me?
komatsus100

---

