---
title: "linux-server install"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by allenbradley on 2009-07-19
I installed the linux-server package from the repos so that I could use PAE to see all 4 GB of my RAM. However, after GRUB shoes the linux-server package, the screen goes blank and nothing happens. What should I do?

---

### Post by jerome1232 on 2009-07-19
Can you get to a virtual terminal? (ctrl+alt+f1) Does your system still work if you boot your old kernel?

---

### Post by allenbradley on 2009-07-19
Yeah, the system works with the old kernel. But with the new server one, the bootup sequence is something like this :
The splash screen appears
Then screen turns black, with a white border slowly increasing in size
Then goes completely blank, unresponsive to all input except the power button.
How do I pull out any kernel errors?

---

### Post by jerome1232 on 2009-07-19
The only thing I can think of is before booting the server kernel, hit "e" to edit the boot line, arrow down to the one that boots the kernel and hit "e" again, remove quiet and splash from the end of the line, then hit "esc" then "b" to boot the modified startup line and watch for where it hangs up. I might be slightly off on the keys it tells you what you need to press at the bottom of the grub screen though.

---

### Post by allenbradley on 2009-07-19
Thanks for the quick replies. I removed the options and rebooted. There seem to be no error messages; The last message I saw before the screen went blank was "starting music player" or something like that. No particular error message before the screen went blank.

---

