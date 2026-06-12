---
title: "Laptop on battery, boot halts"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by Dr Small on 2009-08-10
Hello, I installed Ubuntu Jaunty Jackalope (9.04) on my best friend's laptop for her, and everything works fine and dandy, except this one small issue. If the laptop is running on battery, and not AC power, the system gets to the splash screen, and just halts.

I let it set for awhile, and it never moved on, and the status bar on the splash screen never moved. If I press CTRL+ALT, and hold them in, the status bar moves, and the HDD led begins flashing. If I let off of the keys, the bar quits moving and HDD led goes out.

I can get the system to boot to the desktop, while on battery, by holding in the CTRL+ALT keys. Otherwise, it won't get to the desktop, and it just sits there idling.

Like I said, the system boots excellent and fine when the AC adapter is plugged in. It never halts, and boots in 43 seconds.

Is this a bug, or is there some way to fix this problem? The laptop is a HP Pavilion dv6000 widescreen.

Any help, opinions or suggestions would be greatly appreciated!
Thanks,
Dr Small

---

### Post by Dr Small on 2009-08-10
I did a little reading, and found this thread:
[http://ubuntuforums.org/showpost.php?p=7575302&postcount=9](http://ubuntuforums.org/showpost.php?p=7575302&postcount=9)

I added "acpi=noirq" to the grub kernel line, and then rebooted. It worked fine for me. The system never halted at bootup, nor at shutdown, and I was running on battery the entire time.

---

