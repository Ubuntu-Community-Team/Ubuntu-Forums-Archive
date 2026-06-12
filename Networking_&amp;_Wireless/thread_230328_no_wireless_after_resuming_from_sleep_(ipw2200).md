---
title: "no wireless after resuming from sleep (ipw2200)"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by yang on 2006-08-05
hi all, sometimes after suspending my dell latitude d600, my ipw2200 disappears from /proc/net/wireless. what's going on? can i fix this aside from rebooting? (i have all auto updates.) thanks in advance.

---

### Post by yang on 2006-08-05
ok, i figured it out, via trial & error:

sudo modprobe -r ipw2200 &&
sudo modprobe ipw2200

i suppose this can be put in a resume.d script but hopefully this ipw2200 bug gets fixed (if that's what it is).

---

### Post by Psquared on 2006-10-12
Well, at least you can fix it in Linux. XP does the same thing after a resume and I have to reboot.

---

### Post by H.E. Pennypacker on 2007-05-12
> **yang said:**
> ok, i figured it out, via trial & error:

sudo modprobe -r ipw2200 &&
sudo modprobe ipw2200

i suppose this can be put in a resume.d script but hopefully this ipw2200 bug gets fixed (if that's what it is).

I have a BCM4318 card, and I believe these commands would likely solve my problems, but whenever I type "sudo modprobe -r ndiswrapper" into the terminal, it is as if nothing happens.  Of course, I don't use ipw2200 so I changed the command to ndiswrapper.  I try this command after having tried to suspend or hibernate (this may be an unrelated problem, but suspend and hibernate do not actually work for me - I only *try* to suspend/hibernate with no luck).

Anyway, why don't the terminal respond to me when I enter sudo modprobe -r ndiswrapper?  I'll enter this command, and it does not provide me with an output.

I ask this, because I feel it may help my problem.

---

### Post by CM Xtasy on 2007-05-19
> **yang said:**
> ok, i figured it out, via trial & error:

sudo modprobe -r ipw2200 &&
sudo modprobe ipw2200

i suppose this can be put in a resume.d script but hopefully this ipw2200 bug gets fixed (if that's what it is).

I just did that and now my wireless wont woke at all.  Help please? :(

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

