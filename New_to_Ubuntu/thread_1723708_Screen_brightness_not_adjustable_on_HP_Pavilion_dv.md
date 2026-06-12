---
title: "Screen brightness not adjustable on HP Pavilion dv6-3210us"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by awkisopen on 2011-04-07
I've been searching the forums all day and have seen lots of situations similar to mine, but none of the solutions so far have worked for me! Here's hoping this thread can fix that :)

I recently installed Ubuntu 10.04.2 on my new HP Pavilion dv6-3210us and can't get the screen brightness to adjust. My shortcut keys (F2 and F3) don't work, Fn + Up and Fn + Down don't do anything, and the brightness applet doesn't do anything either. I can adjust it manually by typing
```
echo "50" > /proc/acpi/video/VGA/LCD/brightness
```
but that's about it. Additionally, when I run xev, I get no response when I press F2 or F3.

Any help would be much appreciated! Let me know if there's any other information I should provide.

---

### Post by awkisopen on 2011-04-08
Update... managed to fix the issue by adding acpi_osi=\\"Linux\\" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub. However, the issue persists if I suspend or hibernate - the brightness increases to 100% again! And this time, changing it manually (running the command I mentioned in the previous post) doesn't work either, so I'm stuck with an eye-meltingly bright screen.

EDIT: Ran dmesg after a suspend and found one reference to ACPI:
```
ACPI handle has no context!
```

---

### Post by el_Salmon on 2012-05-14
I have an HP Pavillion DV6-6b11ss with the same problem in Ubuntu 12.04, have you solved the issue?

---

