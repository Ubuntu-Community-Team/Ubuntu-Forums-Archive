---
title: "gnome system monitor showing 100% CPU usage on one tab and 30% on another"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by austinium on 2010-09-03
Hi,

I couldn't think of an appropriate title, but here is the problem iam having:
The Gnome System Monitor shows 100% Utilization on both cores of my CPU on the Resources tab, whereas on the Processes tab when i sort the processes based on CPU utilization i see only 20-35% CPU utilization.

I am using Ubuntu 10.04 x86_64. 
Kernel -> 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

The top command also has a similar output as the Processes tab on gnome system monitor.

I am running rarcrack, but i dont see how that may be causing this.

thanks in advance

---

### Post by Pollox on 2010-09-04
Have you tried going to the "View" menu in system monitor and selecting "All Processes"?

---

### Post by austinium on 2010-09-05
hi Pollox,

Thanks for your response.

Yes, I have tried Clicking View and selecting All Processes, its still the same...the %CPU usage displayed for individual processes dont add up to the CPU usage being displayed on the Resources tab.

I am running rarcrack, it support multi-threading, so i run it with 12 threads(thats the max possible). I have noticed that the same thing happens when i run a simple C Program that does nothing but print text onto the screen in an infinite loop. The CPU usage displayed in the Processes tab and that on the resources tab are not the same. The value on the Resources tab is always higher.

---

### Post by Mindless Automaton on 2011-04-06
> **austinium said:**
> Hi,

I couldn't think of an appropriate title, but here is the problem iam having:
The Gnome System Monitor shows 100% Utilization on both cores of my CPU on the Resources tab, whereas on the Processes tab when i sort the processes based on CPU utilization i see only 20-35% CPU utilization.

I am using Ubuntu 10.04 x86_64. 
Kernel -> 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

The top command also has a similar output as the Processes tab on gnome system monitor.

I am running rarcrack, but i dont see how that may be causing this.

thanks in advance

Fixed bug since 2008?  [URL="https://bugzilla.gnome.org/show_bug.cgi?id=507797[/URL]

Anyways, I have this issue running 10.10 32-bit.  Oh well.

Thanks!

---

