---
title: "FATAL:  Battery Module Not Found"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by jburrell on 2008-12-29
Hi all.  I have a quick question.  I have noticed when I turn on my Sylvania GBook Meso which is running 8.04.01, that as its going through the start up process there's a quick message that flashes on the screen that says: "FATAL: BATTERY MODULE NOT FOUND."  

The computer runs great so there does not seem to be an issue -but- is this an issue?  Is something wrong that I can fix?

Thank you for your time.

---

### Post by moonoo on 2008-12-29
Quick search on the forums gives a similar problem here:

[http://ubuntuforums.org/showthread.php?t=167440&highlight=persistent]("http://ubuntuforums.org/showthread.php?t=167440&highlight=persistent")

Hope this helps.

---

### Post by jburrell on 2008-12-31
> **moonoo said:**
> Quick search on the forums gives a similar problem here:

[http://ubuntuforums.org/showthread.php?t=167440&highlight=persistent]("http://ubuntuforums.org/showthread.php?t=167440&highlight=persistent")

Hope this helps.

Hi again,
I went to the thread link embedded in the post and followed the commands on post #2 of the link.  The following is the terminal output of those commands:
anna@anna:~$ sudo rmmod acpi_sbs
[sudo] password for anna: 
ERROR: Module acpi_sbs does not exist in /proc/modules
anna@anna:~$ sudo rmmod battery
ERROR: Module battery does not exist in /proc/modules
anna@anna:~$ sudo modprobe battery
FATAL: Module battery not found.
anna@anna:~$ sudo acpi -V
     Battery 1: discharging, 81%, 02:23:27 remaining
No support for device type: thermal
  AC Adapter 1: off-line

There were 3 commands mentioned and of the 3 only 1 worked which was (sudo acpi - V).
The commmand sudo modprobe battery gave me exactly the message I see when my machine boots up:  "FATAL: Module battery not found."  This is the error message I am trying to correct.
What is strange is that my computer detects the battery because the command "sudo acpi -V" gives me the status of my battery.
How do I fix this discrepancy?

---

