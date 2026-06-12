---
title: "'system restore' in ubuntu?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by danny_galaga on 2009-06-25
Was doing something this evening and i somehow lost sound in ubuntu. If i reboot into xp i have sound so it;s obviously not a hardware issue. Is there some sort of 'system restore' function in ubuntu? Seems to me the easiest way to fix it would be to go back in time a day or so. When i turn on the pc and there are the options of ubuntu or xp, there is a growing list of 'ubuntus'. Could that be the equivalent of system restore? If i pick the second most recent one?

---

### Post by mhh91 on 2009-06-25
try booting a different kernel from the grub menu

---

### Post by decoherence on 2009-06-25
> **danny_galaga said:**
> Could that be the equivalent of system restore? If i pick the second most recent one?

Not really, but it could fix your problem. Don't select the "recovery mode" options unless you want to try fixing the problem yourself. Boot with an earlier kernel first and see if that fixes it. If so, check launchpad and see if it's a known issue and whether there's a workaround or if it's fixed in the next kernel release.

If you don't know your way around launchpad, I might prevail upon you to run a few commands in the terminal so we can track down the issue.

If you want to give launchpad a try, here's a useful document.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by danny_galaga on 2009-06-26
Thanks for replies. Ok,so ive tried it in an earlier version. Normally i am booting up in 

ubuntu 9.04 kernel 2.6.28-13 generic

so i tried 

ubuntu 9.04 kernel 2.6.28-11 generic

still the same thing. i then booted into xp just to make sure and sound hardware definitely still works. I can type a few things into terminal to try and diagnose if you like. What should i type in?

---

### Post by pissedoffdude on 2009-06-26
> **danny_galaga said:**
> Thanks for replies. Ok,so ive tried it in an earlier version. Normally i am booting up in 

ubuntu 9.04 kernel 2.6.28-13 generic

so i tried 

ubuntu 9.04 kernel 2.6.28-11 generic

still the same thing. i then booted into xp just to make sure and sound hardware definitely still works. I can type a few things into terminal to try and diagnose if you like. What should i type in?

Do you remember exactly what you were fiddling with? If you did something via the command line, you can push the up button on the keyboard to see which commands you ran. Post any commands you did.  
Commands to 'diagnose' the issue can be found here [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by danny_galaga on 2009-06-28
No command line stuff. I rarely do in fact. About a month ago i installed Castle Wolfenstein Enemy Territory. Only recent unusual thing i can think of was i used a USB memory stick that was a bit flakey. Not sure why that would wreck my sound though.
So is there no way to fix this other than reformatting?

edit: and like this guy-

[http://ubuntuforums.org/showthread.php?t=1196700&page=2](http://ubuntuforums.org/showthread.php?t=1196700&page=2)

I don't even have the 'bongo' on startup...

---

### Post by Paddy Landau on 2009-06-28
Does the sound work when you boot off the Live CD?

---

### Post by danny_galaga on 2009-06-28
I can't imagine why it wouldn't. The sound works when i boot into XP. I'll see if i can find the CD. I think i only have 8.04...

---

### Post by goog64 on 2009-06-28
I installed 9.04 5 days ago. I have no sound. I also have no sound when I boot from the Live CD. I have done all the usual suggestions in the various posts I have read, with no success.
This was the most promising link:[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
but I soon ran into trouble when the author said his driver was 1.0.18, when his screen said it was 1.0.18rc3. This of course snowballed into many questions and different possible paths (all of which I followed), and 4 hours later I am no better off. 
I am using a Compaq Presario B3800.
DEVICE MANAGER says that my audio controller is Intel 82801DB-ICH4 with AD1981B Sound Card.
One of the posts mentioned adjusting audio devices in the BIOS. How do I do that, pleeaaase?? When I press F10 during startup I get a BIOS page, but there are definitely no options for anything like this.
Thanks
John

---

### Post by danny_galaga on 2009-06-29
I don't think i made it very clear to start with. I'm starting a new thread with a better heading...

---

