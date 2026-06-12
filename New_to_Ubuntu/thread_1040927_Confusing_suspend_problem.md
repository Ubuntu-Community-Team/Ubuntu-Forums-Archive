---
title: "Confusing suspend problem"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by PreviousN on 2009-01-16
I just bought a Kohjinsha SR8, since in these forums I found that it works pretty well with ubuntu. Link: [http://ubuntuforums.org/archive/index.php/t-517816.html](http://ubuntuforums.org/archive/index.php/t-517816.html)

Apparently suspend is *supposed* to work. And it does, sort of. Here's my problem:

Clicking on the power button in gnome, and choosing suspend, puts the computer into a suspend state. Upon powering back up/opening the lid, the video stays off in a black screen. IE: no backlight, no anything on the screen. The computer, it seems, has booted besides that, the fan turns on, etc. I've made the change to the acpi settings mentioned in the above forum conversation, and that didn't change anything at all!

What makes it very confusing, is that if I open a terminal and type "/etc/acpi/sleep.sh sleep" everything works PERFECTLY. 

I followed instructions in this part of the ubuntu wiki: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) to try to debug the problem. What makes debugging the problem confusing is that by using the command sync; echo 1 > /sys/power/pm_trace; /etc/acpi/sleep.sh force, I encounter no problems!

So, ubuntu intelligencia, how can I make my computer suspend properly through gnome's icon, rather than using a script (which asks me for my password every time I want to suspend, since I have to be root). 

Thanks in advance!

---

