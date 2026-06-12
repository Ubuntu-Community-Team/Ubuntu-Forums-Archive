---
title: "Video lagging"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Rckejser on 2011-04-21
Hello 

I resently installed Ubuntu on my HP mini, i havent had any problems playing HD videos on my laptop at all, but as soon as Ubuntu came on it keeps lagging, i have tried with GnomePlayer and put cache on, drop framining, nothing seems to help. Funny enough winblows had no problem playing the same videos. Any solution to this problem?

---

### Post by Mark Phelps on 2011-04-21
There may not be, as your HP mini may use a video card/chipset that does not support hardware acceleration in Linux.

To see what you have, open a terminal in Ubuntu and enter "lspci".  Look for the line containing "VGA" -- and post the results back here.

If you have a legacy ATI chipset or an Intel chipset, you are probably stuck with your present video performance.

---

### Post by Rckejser on 2011-04-21
Thanks for the quick response. 

The VGA line goes:

Vga compatible controller: Intel Corporation Mobil 945GME Express Integrated Graphics controller (rev03)

---

### Post by Rckejser on 2011-04-22
Anyone else that knows a solution to this problem ?

---

