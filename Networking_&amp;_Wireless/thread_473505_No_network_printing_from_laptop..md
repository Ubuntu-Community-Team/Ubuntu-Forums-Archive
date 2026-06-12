---
title: "No network printing from laptop."
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by DavidNW on 2007-06-14
I have set-up a network between my Linux (Ubuntu installation) and my XP laptop. I can now transfer and share files across both. However, I cannot get the printer - which is hooked up to the Ubuntu installation (desktop pc) to print out files that I have on the XP laptop.

Curiously, when I first set-up the network ages ago, I could get the printer on the desktop to print out files direct from the laptop.

Any suggestions?

Cheers,

David

---

### Post by mitch.c on 2007-06-15
You don't say how you are making the printer connection from Win XP -> Ubuntu. My favorite way is via IPP (cups native). Basically make sure cups is configured to listen on the local interface, and then on the XP machine, Add Printer -> Network Printer -> URL = [http://ubuntumachine:631/printers/printername](http://ubuntumachine:631/printers/printername)

Click the blue link in my sig for more info.

[[COLOR="Red"]UWResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

