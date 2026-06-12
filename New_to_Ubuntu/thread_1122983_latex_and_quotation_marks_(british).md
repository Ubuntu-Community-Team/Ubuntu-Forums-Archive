---
title: "latex and quotation marks (british)"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Tweedicus on 2009-04-11
I have a problem that is driving me mad.

When I use British single quotation marks on any Latex editior (Kile, Texmaker, gedit (latex plugin), or Lyx) then compile the work as a .pdf the quotation marks are always displayed uncorrectly.

So 'quotes' will display with the first quotation mark as a 9 shape rather than a six shape (i.e. it's the wrong way round). The end quotation mark shows correctly as a 9 shape.

Double (American) quotation marks display correctly.

As this is a problem across all editors I suspect the underlying problem is with Texlive supplied in the repositories. I have the full version so have every possible extra.

Any ideas to get these quotation marks displayed correctly.

Thank you.

---

### Post by llamabr on 2009-04-11
Hi.  This isn't really an ubuntu question, it's a tex one.  They have an excellent group, which you can post to here:

[http://tug.org/mailman/listinfo/texhax](http://tug.org/mailman/listinfo/texhax)

Since I'm not too familiar with that symbol, I'll just state the obvious.  You're making sure to open quotes with the ` and then close them with the ' so it'll look like this:

`words inside quotes'

right?

---

### Post by Tweedicus on 2009-04-11
Thank you. You've just solved days of frustration by stating what is obvious to you.

I had no idea that you had to write `quotes' rather than 'quotes', I just did it like I would on a word processor.

It now works perfectly.

Thanks.

---

### Post by llamabr on 2009-04-11
Right.  Glad to help.

FWIW, latex is great, but it involves a pretty steep learning curve.  you'd do well to buy a book, or at least start reading a tutorial, such as:

[http://frodo.elon.edu/tutorial/tutorial/](http://frodo.elon.edu/tutorial/tutorial/)

(You could have skimmed down to 'quotation marks' for your answer).

Glad it's working.

---

