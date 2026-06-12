---
title: "Single Step Start"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by fballem on 2009-03-23
I am seeing an error when Ubuntu starts. The error is displayed after GRUB starts. There is an ATA1 error, and then there is some message that starts 'Fatal Error ...'. The system appears to boot, but I am getting some strange happenings when I put a CD in the CD Drive (multiple instances of Audio CD appears on the Desktop).

I'd like to step through the startup process so that I can read and record the error message, but I don't know how to do that. I would expect it to be a boot option, but there is nothing there that is obvious.

Could someone tell me how to do this please?

Thanks,

---

### Post by Yuki_Nagato on 2009-03-24
Will disabling the Ubuntu bootup splash screen help?

When GRUB first appears, look around the screen for the key to press to send additional commands with the bootup process.  It might be "c".

When you have that line of commands that is going to be sent to bootup the system, look for the command "splash".  Edit that command so it reads "nosplash".  Press Enter.

Ubuntu will boot up without the orange bar.  The text will instead fly by.  I believe you can stop it with the "Scroll Lock" key on your keyboard.

---

### Post by blazemore on 2009-03-24
so that's what scroll-lock does...
As an aside, I assume these messages are logged somewhere?
It might be useful to know where, presumably they are under /var/log somewhere.

---

### Post by fballem on 2009-03-24
Not sure that disabling the Splash screen will help - I still want ubuntu to start, which it does.

Now I know what a scroll lock key does! Unfortunately, I have a Logitech EX-110, which I have discovered does not have a Scroll Lock Key! I never realised that before, because I never needed a Scroll Lock Key.

If someone knows where the log is, then I can have a look and see if it has the information that I need.

If there are other suggestions, I would be most grateful!

Thanks,

---

### Post by Yuki_Nagato on 2009-03-24
Google seems to suggest that 

/var/log/syslog
/var/log/messages

would be the log files you are looking for.

Entering "dmesg" into a terminal immediately after logging in may provide some feedback.  My system wipes that after every reboot, so you may want to copy those contents to a more stable file.

---

### Post by fballem on 2009-03-24
Thanks - I'll have a look through those files!

---

