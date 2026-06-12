---
title: "ugghh won't boot again..."
date: 2010-02-23
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-23
I screwed it up again. I was trying out linux mint via the live cd... looked nice, got further with connecting my phone to the computer than I ever have with hardy...

Then it froze.  Ok so I tried ctrl+alt+del with no luck then just restarted the computer.  Tried to boot into hardy and got this message on the blue screen...

> could not start x server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose.  In the meantime the display will be disabled.  Please retart GDM when the problem is corrected.

<Then a login prompt> 

Well since I didn't know what to do with any of that info I tried rebooting with the same results.  The I rebooted with the mint live cd shutdown properly and tried again.  No luck that's why I'm here.

I'm using the mint live cd since I lent out my hardy CD. 

Any suggestions on how to get back into my hardy OS?

---

### Post by hortstu on 2010-02-23
Just in case someone runs into the same problem...

I ran the system off the live disk for a few minutes trying to figure out how to solve the problem.

After no luck I rebooted.  This time for some reason I never made it to the blue screen.  I ended up with an @root prompt and noticed that somewhere above it said fsck failed run manually.

So I typed in fsck and answered yes to all the questions.

At the end I hit ctrl+alt+del and ended up at the blue screen.  I hit ctrl+alt+del again and it reloaded and did a disk check.  This time it booted normally.  

I imagine if I had run fsck at the blue screen I would have gotten the same results.

My issue is solved.  I hope this helps you solve yours.

---

