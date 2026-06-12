---
title: "After 2 hours machine goes dead"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Phil Usher on 2010-03-13
I'm not very experienced with ubuntu - I dabble from time to time in hopes of making Linux a regular part of my world but typically end up returning to Windows after tripping over a gotcha or two.

I have ubuntu 9.10 x64 installed on MSI PC Wind Nettop 100 and I have a problem with the computer becoming unresponsive after being left ~2 hours unattended.

I have checked (or rather unchecked) everything I could find via the UI which might be causing the machine to suspend or hibernate.  I allow screen-saver after 5 mins and monitor shutdown after 10 but otherwise it is configured to stay on.

After ~2 hours the machine enters a catatonic state - power is on, monitor off, no response to keyboard, mouse or pushing of power button.  Any remote desktop session is unresponsive.

Only recovery from this condition is to hard boot by either push and hold power button or killing power.

This problem is in my critical path as I intend using this computer to be accessed via remote desktop (VNC) and to be left unattended for extended periods (days).  

Thanks in advance for any help solving this problem.

Cheers ... Phil Usher

---

### Post by mbzn on 2010-03-13
Can it be that the computer is set to suspend in BIOS?
Disable power saving in the bios and see. It's worth a try...

---

### Post by MichealH on 2010-03-13
> **mbzn said:**
> Can it be that the computer is set to suspend in BIOS?
Disable power saving in the bios and see. It's worth a try...

Now we wait...

---

### Post by coldraven on 2010-03-13
> **MichealH said:**
> Now we wait...

...........my coffee has gone cold!................

---

### Post by MichealH on 2010-03-13
Mine is frozen!

---

### Post by Desert Sailor on 2010-03-13
Speaking of cold coffee...  It could be heat related.  If the CPU or Video card is over heating, that could be shutting down the computer.

---

### Post by MichealH on 2010-03-13
I could cook my beans on that *daydreams*

---

### Post by Phil Usher on 2010-03-13
Sorry, I went to sleep.

BIOS - On the MSI there seems no clear way to disable the power saving - just a choice between S01 & SO3.

However, I think I have nailed the problem - Screen Saver Crash.

I disabled the Screen Saver and now the machine stays alive.  I allow the monitor to shut down.

Next I will try allowing the HDD to spin down.

But I think I am there.  Thanks to those who responded.

---

### Post by MichealH on 2010-03-13
> **Phil Usher said:**
> Sorry, I went to sleep.

BIOS - On the MSI there seems no clear way to disable the power saving - just a choice between S01 & SO3.

However, I think I have nailed the problem - Screen Saver Crash.

I disabled the Screen Saver and now the machine stays alive.  I allow the monitor to shut down.

Next I will try allowing the HDD to spin down.

But I think I am there.  Thanks to those who responded.

When you have used Trial and Error post It back so then everyone knows what EXACTLY caused the problem Thanks also Can you mark this as solved?

---

