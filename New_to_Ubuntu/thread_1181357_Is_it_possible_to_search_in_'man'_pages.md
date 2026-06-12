---
title: "Is it possible to search in 'man' pages?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by j-g-faustus on 2009-06-07
Quick question: 'man' documentation is often very long, and it's a lot to read through if you are just looking for one particular item.

Is it possible to search in the page? Similar to Ctrl+F in Firefox or Ctrl+S in emacs?
I tried 'grep' ```
man ls | grep directory
``` but it is only moderately useful as you lose most of the text around the hits.

So is search possible?

---

### Post by 73ckn797 on 2009-06-07
Try this as one source: [http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

---

### Post by kaibob on 2009-06-07
Type forward slash then search term then enter.

---

### Post by jpkotta on 2009-06-08
If you're an Emacs user, try M-x woman.  Then you can use C-s or even C-M-s.

---

### Post by andrew.46 on 2009-06-08
Hi kaibob,

> **kaibob said:**
> Type forward slash then search term then enter.

and then press the 'n' key to find the next match...

Andrew

---

### Post by glotz on 2009-06-08
And 'N' to find the previous occurrence.

---

### Post by andrew.46 on 2009-06-08
Hi glotz,

> **glotz said:**
> And 'N' to find the previous occurrence.

Hey I didn't know that! Thanks :-).

Andrew

---

### Post by j-g-faustus on 2009-06-08
Very nice :) Thanks!

---

### Post by glotz on 2009-06-08
Glad to be of use. **man** uses **less** to display the manual pages, for the complete keyboard shortcut reference, hit h.

I love manual pages!

---

