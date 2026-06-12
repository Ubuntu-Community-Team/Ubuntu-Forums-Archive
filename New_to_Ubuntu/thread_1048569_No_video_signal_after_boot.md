---
title: "No video signal after boot?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by scott_s_06 on 2009-01-23
I installed Ubuntu on a 5 year old Dell that had windows xp, Intel ~2.4GHz, and a Radeon X300.  When I turn my computer on I can select windows xp or Ubuntu, after selecting Ubuntu there is a count down saying press Esc to open a menu.  After the count down expires I get a loading screen that says Ubuntu with a shiny orange loading bar, but when the bar fills I hear a drum play and immediately my monitor goes blue and says "No signal". It remains this way until I press the power button on my computer and that same Ubuntu loading screen comes up and the computer shuts down.

Why is this happening? 

Should I update the Graphics card's drivers in windows and then boot in Ubuntu?

Thanks!

---

### Post by Muffinabus on 2009-01-23
Your monitor doesn't support the resolution that Ubuntu is displayed in.  Upgrading the graphics card drivers in Windows will do nothing to your Ubuntu install.  I'm not quite too sure how to go about fixing this, I'm sure there's a way you can do it from the Terminal, hopefully someone will post a fix for you.  Or if you have a CRT monitor around, you can plug that in, get into Ubuntu, install your proper drivers and make sure you're running a resolution your LCD supports.

---

### Post by RomeReactor on 2009-01-23
Hi. Try going to grub (just after the BIOS screen you should see a count down, then press ESC) and select **recovery mode**; there select **xfix** and see if you get your display back.

---

