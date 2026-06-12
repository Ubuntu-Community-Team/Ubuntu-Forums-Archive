---
title: "very slow booting sometimes"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by zhanglini on 2009-10-10
Dell inspiron 1000, 512 mb.  Ubuntu 9.04.
Recently after I used Alt+Sys Rq REISUB to reboot my frozen computer (although I don't know if this is the cause), I am starting to have problem rebooting my computer (although it does NOT happen all the time, 50% maybe).  
It's very slow, the step from pushing the power button to login ID shows up is OK; but from login ID to desktop takes 20/30 TIMES the normal time, and of course the computer would be freezingly slow after that.  I then would have to reboot a few times to fix the problem.
Is there a file or two that is corrupt and I need to fix?
If I can't fix it, I might wait till 9.10 is official and have a clean install.....
Thanks for reading

---

### Post by hal10000 on 2009-10-10
if it happens the next time look into your logfiles (/var/log/messages, /var/log/syslog etc.) and run dmesg to see if there are error messages or something else unusual things

---

### Post by NightwishFan on 2009-10-10
Yes, the log may seem like a lot of DATA, but look for lines that repeat or seem out of place. You can also temporarily disable the splash screen to read the boot messages.

To do so: (This is easier than it sounds)

[LIST=1]
[*]When logging in if you dual-boot you get to a screen where you select your OS, if not you may have to press ESC when prompted to force the screen to appear. You can also hold SHIFT.
[*]Highlight the top Ubuntu option, and press E, you will be greeted with another screen. Highlight the line that starts with KERNEL and press E.
[*]You will see a line of text. At the end it has the words 'quiet' and 'splash'. Delete 'splash'. (Do not worry it is only temporary, it automatically does the original options next boot).
[*]After deleting splash, press ENTER, and then at the next screen press B. This will show the kernel booting.
[*]You can also delete 'quiet' but it shows a lot of text.
[/LIST]

---

