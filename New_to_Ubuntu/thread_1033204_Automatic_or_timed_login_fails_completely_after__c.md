---
title: "Automatic or timed login fails completely after  change"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by taffyviking on 2009-01-07
As the sole user of my PC I thought it would be a neat idea to have it log me in automagically, so I made the necessary changes in the "system administration -login window" GUI and restarted.

At login I got a pop-up that said "Authentication failed", with no chance to stop the process.

I thought, "OK so I'll re-install and specify an auto-login while reinstalling".  That went great, but after I was (auto)logged in I thought I'd try and specify a manual login instead (so made the necesary changes); at bootup all I got was the same "authentication failed" popup.
It seems that making any changes at all to the auto/manual login that was specified at install time is just pure poison!

I've gone to a terminal with ctrl+alt+F1 and tried editing /etc/gdm/gdm.conf-custom to no effect.  I've tried editing /etc/gdm/gdm.conf, but no effect, whatever I try to do gdm just won't let me log in.

Anyone out there got any silver bullets?  I'm looking at yet another re-install.  I know that my low level of Linux savvy is a hindrance, but somebody out there must be able to tell me in simple words how I can get out of this!

---

### Post by Michael.Godawski on 2009-01-07
hi,

don't worry. Do you know how often I have reinstalled in the beginning? :P

First check if you do everything according to 

[LIST]
[*][https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)
[/LIST]

---

### Post by taffyviking on 2009-01-07
Oh yes,  I followed everything to the letter, which is why I'm so puzzled.  I can believe you about the re-installs.  I could just go ahead and install again, but I don't learn much that way, apart from finding out which areas to keep away from!

---

### Post by markbuntu on 2009-01-07
I never use autologin. If something goes wrong you are truly screwed. Next time use timed login. That way you can get to safe mode or login manually if it fails. 10 seconds is definitely worth the wait.

---

### Post by taffyviking on 2009-01-08
Yes I thought that was a good strategy too, so I tried setting it after the second reinstall.  Exactly the same symptoms however.  I would use it during the OS reinstall, but don't recall being offered the option of timed login during reinstall.

And my PC is still un-login-to-able.  Any suggestions on how I might get it working again? Yes, I know, boot to CD, install Ubuntu.....

---

### Post by cariboo on 2009-01-08
Can you login, in recovery mode? If you can't, just set a new password for your user. At the prompt type:

```
passwd <user>
```

where <user> is your user name.

Jim

---

### Post by taffyviking on 2009-01-11
I'm sure recovery mode is the way to go since one can log in as root from there, but changing my user's password didn't help.  I've tried renaming /etc/gdm/gdm.conf-custom to remove it from the picture altogether, but even as root it won't let me; comes up with some nonsense about "strict subs".

What's the surest way of setting the login back to normal non-automatic through the root shell?

---

### Post by taffyviking on 2009-01-14
Thanks for trying guys, but last night I succumbed to the inevitable and re-installed.  I've learned my lesson, no more of that automatic login stuff for me!

---

### Post by primaxx on 2009-02-03
You can view the solution "I found" to this problem [here]("http://ubuntuforums.org/showthread.php?t=992070").

---

