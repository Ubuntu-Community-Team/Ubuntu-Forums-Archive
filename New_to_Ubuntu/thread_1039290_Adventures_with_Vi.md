---
title: "Adventures with Vi"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-14
Using Intrepid 8.10 and it uses a really old version of vi that doesn't display an "INSERT" message, neither does it quit when I type "q" or "q!".

So how do I upgrade to a newer version of Vi and how do I quit? and where can I find the commands?

Thanks. ;)

---

### Post by Simian Man on 2009-01-14
It sounds like you are using vi instead of vim.  Try entering the command vim and see if that behaves more like how you expect.  I always alias vi to vim for just this reason.

---

### Post by Terl on 2009-01-14
Using package manager you can download vim (the improved vi).

Note your quit should be :q! and not just q!  To leave insert mode just hit escape and then you can hit :q! to just leave or :wq to write changes and quit.

There are lots of tutorials on the net for VI.  Just google a bit.  ;)  The command ```
man vi
``` brings up some useful info as well.

---

### Post by DGortze380 on 2009-01-14
try vim

---

### Post by mayagrafix on 2009-01-14
Thanks a lot wonderful Ubuntu counselors :D

I will download and install ViM as per sugestion. BTW, the thank you gizmo is not available any more? I will mark this thread solved.

Oops! not available any more either. Oh well, Thanks a lot.

---

### Post by DGortze380 on 2009-01-14
> **mayagrafix said:**
> Thanks a lot wonderful Ubuntu counselors :D

I will download and install ViM as per sugestion. BTW, the thank you gizmo is not available any more? I will mark this thread solved.

Oops! not available any more either. Oh well, Thanks a lot.

vim is installed by default, just type vim at the cl to start it.
you may also want to consider nano.
don't know anything about gizmo.

---

