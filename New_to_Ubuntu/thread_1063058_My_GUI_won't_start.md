---
title: "My GUI won't start"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by card_ace on 2009-02-07
I have ubuntu 8.10 installed and i'm dual booting it with windows xp pro.  Both were working fine until yesterday.  I used keryx to download the updates for ubuntu to a flash drive and came home and installed them.  No problems there.  Next i tried to install compiz from a package i downloaded and it said my system had several broken dependencies and told me to run either "sudo synaptic" or "sudo apt-get install -f"  I used "sudo synaptic" and it said i think 16 broken dependencies and started fixing them.  I went to watch some tv in the other room while i was waiting and the computer was asleep so i woke it up but the screen stayed black.  It gave me my mouse, but nothing else, just a black screen with a little white arrow on it.  I let it sit for another hour and when i checked back there was no change so i just turned the computer off.  I booted it back up and tried to go into ubuntu, it gave me the logo and the loading bar as usual, but then instead of giving me the usual login screen, it gives me some messages about normal boot and no image.  After all the messages are over(about halfway down the screen) i get an option to log in using this prompt.  After i log in it doesn't give me my desktop or anything, just a terminal.  Is there a way to get my GUI back without reinstalling?

---

### Post by sleepyjon on 2009-02-07
Your computer going to sleep might have interupted the install(s).

before checking that, try logging in and typing

```

startx

```

If startx worked, you just don't have gdm enabled. I think in gnome you go:
administration -> services

If startx doesn't work, try 

```

sudo dpkg --configure -a

```

The first one try's to start x, the second one trys to configure any downloaded but uninstalled packages.

---

### Post by avtolle on 2009-02-07
I would also advise you to, in the future, change the settings in the power manager to avoid the computer "going to sleep" if you decide to leave it unattended when downloading updates; and, if a laptop, to have it on AC power during the process. For now, do as sleepyjon recommends and let us know how you come out.

---

### Post by card_ace on 2009-02-07
ok i tried "startx" and it seemed like it started to do something.  the screen flashed and i got the little x on the mouse that usually means its loading.  the background wasn't my picture but just a bunch of alternating colored lines and i didn't get the toolbars at the top and bottom.  it was like that for about 2 seconds then flashed back to the terminal and give me stats about my system, then said "waiting for x server to shut down" and gave me another terminal prompt.  when i used "sudo dpkg --configure -a" it had me put in my password, then went right back to the terminal.  is it supposed to take a while before it does anything?

---

### Post by sleepyjon on 2009-02-09
> **card_ace said:**
> ok i tried "startx" and it seemed like it started to do something.  the screen flashed and i got the little x on the mouse that usually means its loading.  the background wasn't my picture but just a bunch of alternating colored lines and i didn't get the toolbars at the top and bottom.  it was like that for about 2 seconds then flashed back to the terminal and give me stats about my system, then said "waiting for x server to shut down" and gave me another terminal prompt.  when i used "sudo dpkg --configure -a" it had me put in my password, then went right back to the terminal.  is it supposed to take a while before it does anything?

Did you try to startx after dpkg --configure -a? I forgot to tell you to do that, sorry.

If x still doesn't start, your xorg may be messed up. That or your video drivers.

You have several options if it's the xorg:

1) I think there's a fix x option in recovery mode, just reboot and select recovery mode in grub.

2) If that's not there, try:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by card_ace on 2009-02-09
I know the problem isn't my video drivers as the same thing happens when i boot to it on different computers (its an external USB hard drive).  That means it must be the xorg right?  Well i tried the xfix in recovery mode and it didn't seem like anything happened.  the screen flashed and that's about it.  i also tried to fix the broken dependences while i was there.  there are 3 broken dependencies in my system, and i can't seem to get rid of them.  it asks me if i want them removed and i say yes, but then as its working it runs into problems and none of them get deleted.  my other question is how do i become a "superuser"?  now whenever i do "sudo dpkg --configure -a" it says i must be a superuser to do that.  what now?

ok correction, i must have forgotten to type in "sudo" before dpkg --configure -a.  sorry

---

### Post by card_ace on 2009-02-13
well i still don't have a solution and i'm missin my ubuntu too much so i'm just gonna reinstall it i guess.  thanks for tryin to help.

---

