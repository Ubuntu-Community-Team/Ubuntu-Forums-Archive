---
title: "Adobe Reader prints alternate pages upside-down with booklet printing"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-09-19
I'm having a big problem. I have a few large PDF documents that I need to print. To save paper, I want to use the "Booklet" (brochure) format (I have a printer that can print double-sided).

From the Adobe Reader print dialogue, the main setting is *Page Scaling > Booklet Printing*.

The problem is that Adobe Reader prints every reverse side of each page upside-down, so of course the result doesn't work out.

I've fiddled with the print settings in the Adobe print dialogue, but I haven't managed to solve this problem. I don't see anything useful in the Adobe help pages.

Can anyone help?

---

### Post by Paddy Landau on 2010-09-23
Bump?

---

### Post by lkjoel on 2010-09-23
> **Paddy Landau said:**
> I'm having a big problem. I have a few large PDF documents that I need to print. To save paper, I want to use the "Booklet" (brochure) format (I have a printer that can print double-sided).

From the Adobe Reader print dialogue, the main setting is *Page Scaling > Booklet Printing*.

The problem is that Adobe Reader prints every reverse side of each page upside-down, so of course the result doesn't work out.

I've fiddled with the print settings in the Adobe print dialogue, but I haven't managed to solve this problem. I don't see anything useful in the Adobe help pages.

Can anyone help?
Try any other double-sided formate than booklet.
Also try other readers, such as envice/okular/xpdf

---

### Post by Paddy Landau on 2010-09-24
> **lkjoel said:**
> Try any other double-sided formate than booklet.
How do you mean? I specifically want to print brochure.

> **lkjoel said:**
> Also try other readers, such as envice/okular/xpdf
Evince and xpdf don't have that option. Okular does the same thing as Adobe -- prints the underside upside-down.

OpenOffice, on the other hand, prints perfectly in brochure. I can't understand why Adobe and Okular should in invert the undersides whereas OpenOffice prints correctly.

Thanks for your ideas, unfortunately I'm no further.

---

### Post by &#5097;&#5103;waya on 2010-11-25
> **Paddy Landau said:**
> How do you mean? I specifically want to print brochure.


Evince and xpdf don't have that option. Okular does the same thing as Adobe -- prints the underside upside-down.

OpenOffice, on the other hand, prints perfectly in brochure. I can't understand why Adobe and Okular should in invert the undersides whereas OpenOffice prints correctly.

Thanks for your ideas, unfortunately I'm no further.

HRMMMMMMMMMMMM

The Adobe is forcing a duplex setting of 'flip on short side' when selecting booklet printing and will not let you change it.

It acts like adobe is flipping the other side, then telling the printer to flip it again, causing it to be upside down!

---

### Post by &#5097;&#5103;waya on 2010-11-25
I finally got it to work.

Here are my settings:

pages: xxx - yyy
subset: all pages
**[X] REVERSE PAGES**
Copies: nnn
Page Scaling: booklet
Booklet subset: both sides
**[X] AUTOROTATE PAGES**
Orientation: Portrait

---

### Post by Paddy Landau on 2010-11-25
OK, this is *really* weird...

Two days ago, I printed a 36-page PDF, booklet, double-sided, and it worked perfectly. I had forgotten about this problem so I thought nothing of it.

Today, after you posted, as an experiment I printed *the same document*, and this time it's printing upside down on the second page!

:confused:

---

### Post by Paddy Landau on 2010-11-25
> **&#5097 said:**
> I finally got it to work.
Here are my settings:
Yay! It works! Thank you so much!

---

### Post by Paddy Landau on 2011-08-08
Aargh! It's happening again. Even with the settings from &#5097;&#5103;waya ([post 6]("http://ubuntuforums.org/showthread.php?p=10160764#post10160764")).

Any help, anyone, please?

---

### Post by lkjoel on 2011-08-08
This might not be a problem with Adobe Reader. It might be a problem with your printer.

---

### Post by Paddy Landau on 2011-08-08
> **lkjoel said:**
> This might not be a problem with Adobe Reader. It might be a problem with your printer.
That did occur to me, and I did check the printer settings; but then why is it only with Adobe and not with LibreOffice? I am struggling to make sense of this, because it works correctly with LO. Maybe Adobe incorrectly thinks that the printer turns side 2 upside down and therefore "corrects" it?

---

### Post by lkjoel on 2011-08-08
Maybe that is the format of booklet printing for Adobe Reader?
Does it work sometimes?

---

### Post by Paddy Landau on 2011-08-09
> **lkjoel said:**
> Does it work sometimes?
It used to work; then it didn't; then it did again; now it doesn't again. Confusing, perplexing, and incredibly frustrating!

---

