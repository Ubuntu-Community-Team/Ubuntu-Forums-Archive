---
title: "White screen of death..."
date: 2010-01-11
forum: New to Ubuntu
---

### Post by jermza on 2010-01-11
Twice today, out of a few boot-up sessions (I'm moving between Windows and Ubuntu 9.10), Ubuntu has loaded, after I've logged in, into a blank white screen.  Both times, I pushed 'reset' on my box.  Meanwhile, Windows has booted up fine every time today.

Why am I experiencing this bit of instability with Ubuntu?  What is this white screen of death I'm getting?

---

### Post by muteXe on 2010-01-11
Dunno what that's about but if you push CTRL+ALT+F1 you should be able to get into a virtual console and shutdown/reboot your machine properly from there if it happens again ("sudo shutdown -h now").
Sorry I can't help with the actual problem though.

---

### Post by scrooge_74 on 2010-01-11
Video card problem most likely, what brand you have? if you go into a console then your problem is the video card.

---

### Post by Sylslay on 2010-01-11
Agree with that "Video card problem most likely"

Are You have compiz on?

Siwtch off ( if any) visual efecct.

I have intel 845G and lots of trable.
I got now and than black screen.

What realse of Ubuntu You using.

If its 9.04 or older You maght change video mode when load grub ( in munu.lst)
 wite " vga=792"

---

### Post by Cabs21 on 2010-01-11
Was getting a similar issue with compiz reloading and turning my screen all white.  After I installed my video card drivers it worked perfectly with no issues.  That could be the problem.

---

### Post by jermza on 2010-01-11
Well, I'm having endless hassles with my graphics card (it's old), so perhaps that is the problem.  New card coming soon...

---

