---
title: "graphic card problem with regnum"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by cybuss on 2009-07-10
when i starts it it says. error! unsupported graphic card
there are three possibilitys for this error
1 graphic cards too old
2 unsupported video drivers
3 directx not installed

im not sure what drivers is in here
but i got jaunty jackalope
not sure if this old laptop has a graphics card recently bought it
may i get a code to check if i got a graphics card for a start?

---

### Post by masux594 on 2009-07-10
post the ```
[FONT=monospace]lspci | grep VGA[/FONT]
``` output =)

Sysc, A

---

### Post by cybuss on 2009-07-10
the response from terminal code is
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

is there a way to get radeon Xpress 200m to work with regnum?

---

### Post by masux594 on 2009-07-10
From the minimun requirements who wants ATI 7500 or better card, you can play.. [Requirements]("http://www.regnumonline.com.ar/index.php?l=1&sec=13")..

Sysc, A

---

### Post by masux594 on 2009-07-10
Let's check the other specs..

Sysc, A

---

### Post by Mark Phelps on 2009-07-10
The problem is most likely to be "unsupported video drivers".

As has been reported numerous times in this forum, AMD/ATI dropped support for accelerated drivers with all but the newer "HD" series cards.  The new drivers won't work with the older cards (including the version you have) and the older accelerated drivers won't work with the newer Xserver in Jaunty.

So, you're stuck, like so many of the rest of us, using unaccellerated open source drivers.

---

### Post by cybuss on 2009-07-13
> **Mark Phelps said:**
> The problem is most likely to be "unsupported video drivers".

As has been reported numerous times in this forum, AMD/ATI dropped support for accelerated drivers with all but the newer "HD" series cards.  The new drivers won't work with the older cards (including the version you have) and the older accelerated drivers won't work with the newer Xserver in Jaunty.

So, you're stuck, like so many of the rest of us, using unaccellerated open source drivers.

ok ill just buy a nvidia modern 1
where can i browse laptop nvidia graphic cards?

---

### Post by masux594 on 2009-07-14
change graphic card in a laptop? .. I seriusly think that u can't change the graphic card in a laptop.. The GC is welded in the laptop's motherboard!!

Sysc, A

---

