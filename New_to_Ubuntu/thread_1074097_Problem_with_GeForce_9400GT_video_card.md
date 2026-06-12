---
title: "Problem with GeForce 9400GT video card"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by leclerc65 on 2009-02-18
Computer: AMD64, 2G ram
O/S: WinXP dual boot with Ubuntu 8.10 (64)

Prob# 1: When connecting the HDMI output of the card to my Panasonic HDTV, my old LG monitor quits.

Prob# 2: When applying the drivers (I tried both the nVidia 173 and the recommended 177) the screen doesn't work right. I lost both top and bottom Panels. As a newbie I cannot manage with a diet of command lines alone.:p

Please help, I am more than happy if Prob# 2 is solved (I will buy a set of wireless mouse/keyboard to use with my 50" Panasonic). I absolutely need the HDMI output to play a LG Bluray DVD (it works with WinXP right now).

---

### Post by Ben Page on 2009-02-19
You have pretty similar system like me, I also have 9400GT 512 MBRAM Palit GPU. I had no problems applying the nVidia 177 driver in Ubuntu 8.10 64, it worked flawlessly. Maybe panels disappeared just because you turned them off...I am not in the gnome desktop right now, but I remember that it is possible to delete the panels and it is also possible to re enable them (as many as you need, and put them where ever you want them). Try to find the option "new panel", maybe in the right click (don't remember). If the right click doesn't appear then you have a Gnome (desktop shell) issue not the graphics. I dont use HDMI, so I can't help you there, but I also use dual output, and it works fine if it's set up right (TV+LCD). For this, you need to edit your xorg.conf in /etc/x11/ and put an option under the "screen" section to enable dual view and write correct meta modes (resolutions) for the dual output.
Just ask what you don't exactly  understand out of this and I'll try to explain it better ;)

---

### Post by leclerc65 on 2009-02-19
Thanks, Ben.
I saved your suggestions and will try them later (maybe in a few weeks) when I can afford a good wireless mouse/keyboard set, for the moment I have to live with that other ugly OS.;)
There is one thing, Ubuntu 8.10 64 bits is a screamer, I never seen a PC that fast, at work or at home, even with my lo speed DSL line.

---

### Post by jtb_90 on 2009-03-31
I've just purchased a second monitor hoping for dual monitors extended desktop, both 20" exactly the same 1680x1050, the outputs on this card is 1 DMI and 1 VGA, I'm planning on using an adaper to plugin one of the VGA monitors into the DMI port. [Can I even do that?]

Either way can someone tell me what to put in my xorg.conf to enable dual screens?

Cheers!!

---

