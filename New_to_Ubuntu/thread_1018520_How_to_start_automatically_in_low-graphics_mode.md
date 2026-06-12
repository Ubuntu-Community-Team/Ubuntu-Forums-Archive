---
title: "How to start automatically in low-graphics mode?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by kramer65 on 2008-12-22
Hello,

The video drivers in Ubuntu have always worked perfectly until I upgraded to 8.10. When I now log in it first gives this error message that the driver doesn't work and then a prompt that I can start up in low graphics mode.

By now I am ok with it and I don't even want to spend the time fixing it. The only thing that really annoys me is that I always have to click ok three times before I get to the login screen. Is there a way to make ubuntu start up in low graphics mode by default so that I don't have all those annoying prompts anymore?

---

### Post by mikeyphi on 2008-12-22
Have a look at this guide:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by kramer65 on 2008-12-22
Hello,

Thank you for that. I guess I could use that somehow. I wouldn't have a clue what to edit to what in order to go into low graphics mode automatically though. I'm not that advanced.. (that I have 300+ posts simply means I ask a lot, not that I know a lot.. :)  )

A little more help would be greatly appreciated.. :)

---

### Post by mikeyphi on 2008-12-22
You would have to edit /boot/grub/menu.lst
find the line:

#kopt=

at the end, add:   

vga=771

save the altered file.....Note- there is a space before the 'vga=771'

other vga settings are here:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

However, a better option would be to let us help fix the graphics issue properly - if you can tell us the full name of the graphics card.

---

