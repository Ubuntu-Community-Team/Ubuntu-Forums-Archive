---
title: "Printing Business Cards in Open Office Word"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Loren Bliss on 2011-06-22
Anybody know how to print business cards with Ubuntu/Open Office Word? I need the Avery 8376 or 8371 formats (2 columns 5 up), but neither are available in Open Office and their on-line counterparts won't download in any usable form. 

Thanks all, 
Loren Bliss

---

### Post by owiknowi on 2011-06-22
due lack of time a workaround that worked for me:
make one card in the required size, create a new document and split it into 2 columns.
next copy and paste the original card into the columns (10 on one a4).

---

### Post by Loren Bliss on 2011-06-22
Thanks, **owiknowi**. What I finally did -- this after eight hours of trial, error and cussing -- was copy the Avery format from an earlier pre-Ubuntu document, paste it into a new Open Office document, then enter the type into each of the ten rectangles. Took lots more trial-and-error to get the spacing right, even more such effort to get the page margins right (all of this a monumental pain, not the least because though I know printing terminology and technology backwards and forwards, I will probably never learn the comparable computer technology), but I finally got 50 cards (all I had the perforated Office Depot paper for). 

Alas, as soon as I saved my document, it de-formatted, which means I'll have to go through this same ordeal the next time I need cards -- unless of course somebody comes up with a better solution.

Meanwhile thanks again. 

Loren Bliss

(I'm signing off for the night -- done in by the struggle -- but will be back tomorrow.)

---

### Post by owiknowi on 2011-06-22
there are undoubtedly better ways since business cards are pretty common, also when created yourself.

on the re-formatting when saving: try to export it as a .pdf
on the margins: you can set them in the document properties
on the aligning: select all in one and the same column (hold down the ctrl-key and click on each card) and choose from a menu 'align'.

i'm not familiar with non metric formats so it's all a bit unprofessional... i think there are pre-formatted templates for open office in the size you require.

---

### Post by mike555 on 2011-06-22
I use "gLabels" , easy to use and set up templates.

---

### Post by dannyboy79 on 2011-12-27
I am now in the same boat. The problem is that I am unfamiliar with how to get them repeated. So I have created 1 in the top left corner from the template i found online. it's awesome BUT how do i repeat it the other 9 times?

I am using Avery 8371 matte white business card stock and am using Open Office 3.3.0

Any help would be appreciated

---

### Post by robert shearer on 2011-12-27
doing this with glabels is much easier. It is set up to print multiples for the Avery forms et al.
Download from Ubuntu software centre or...
In a terminal run..
```
sudo apt-get install glabels
```

glabels home page here...
[http://www.glabels.org/](http://www.glabels.org/)

---

