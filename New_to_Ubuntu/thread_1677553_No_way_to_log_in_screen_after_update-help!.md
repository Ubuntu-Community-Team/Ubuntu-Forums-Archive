---
title: "No way to log in screen after update-help!"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by llmunro on 2011-01-28
Hi Friends,

I installed Ubuntu 10.10 via a USB drive on a brand new Samsung lappie this afternoon.  I had to run lots of updates, which I did and rebooted a few times.  It seems the kernel was updated. All seemed fine until I was asked to activate a NVIDIA (sp?) driver and reboot to finish the driver install.  So I did and now...the lappie boots fine, GRUB seems to work, it gets to the splash screen, and then I get a black screen and this:

Ubuntu 10.10 lisa-Samsung tty1
lisa-Samsung login: _

And that's it!  I can't get to the login screen.  I've tried rebooting a few times (sudo reboot) and nothing.

I am a little worried as this has never actually happened to me on a brand new Ubuntu install.

Advice? Thoughts? Suggestions? Next steps?

Thanks much.

Lisa

---

### Post by jd2012 on 2011-01-28
Just spit-balling, but perhaps check your BIOS settings? Maybe pasword protected?

---

### Post by llmunro on 2011-01-28
Hi,

I don't think its the BIOS password, which I haven't set and wasn't a problem before the update to the driver.

Here are some other things I've tried:
Booting from recovery mode (with ethernet cable attached).  No dice.  Messages about failed to get packages.

Tried Resume Normal Booting from Recovery Mode. Zilch.

Tried sudo apt-get update and got a long list of packages that failed to be fetched.

Tried sudo-apt get upgrade and nothing seems to have been upgraded.

Do y'all think I have to reinstall at this point? Is it super broken?

Thanks.
Lisa

---

### Post by kn0w-b1nary on 2011-01-28
What happens when you hit:

Ctrl+Alt+F7
Ctrl+Alt+F8

---

### Post by llmunro on 2011-01-28
If I hit Ctrl+Alt+F8, nothing happens.

If I hit Ctrl+Alt+F7:

speech-dispatcher disabled; edit /etc/default/speech-dispatcher
*PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*Enabling additional executable binary formats binfmt-support
*Checking battery state
fsck from util-linux-ng 2.17.2
/dev/sda6: clean 165024/7389184 files 1395425/25931392 blocks
#Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable:usr/bin.firefox

*Setting sensors limits

(blinking cursor)

I don't know what this means.

Thanks.
Lisa

---

### Post by jd2012 on 2011-01-28
Try

Ctrl + Alt + F5
or 
Ctrl + Alt + F6

Works for me toggling in and out of that login screen.

---

### Post by Bright_View on 2011-01-28
When you get to the grub menu, do you have a recovery mode in the list?  If so, try booting with that and either running in failsafe graphics mode or reconfiguring the graphics from the recovery menu.  

Hope that helps.

Dave.

---

### Post by llmunro on 2011-01-28
All the Ctrl+Alt F's don't seem to do much, with the exception of F7 as reported above.

Thanks for the help!

Best,
Lisa

---

### Post by llmunro on 2011-01-28
Dave,

Eureka!  This worked! And I have confirmed it by rebooting normally with GRUB and I am able to log in as usual! 

Many thanks to all! :)

Goodnight!

Lisa

---

### Post by Bright_View on 2011-01-28
> **llmunro said:**
> Dave,

Eureka!  This worked! And I have confirmed it by rebooting normally with GRUB and I am able to log in as usual! 

Many thanks to all! :)

Goodnight!

Lisa

Excellent!  I don't usually help people on here much (usually receiving it instead).  Kind of a nice feeling.

Dave.

---

