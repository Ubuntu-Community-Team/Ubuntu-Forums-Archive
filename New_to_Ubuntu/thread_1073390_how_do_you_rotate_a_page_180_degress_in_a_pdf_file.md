---
title: "how do you rotate a page 180 degress in a pdf file you created?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by stinger30au on 2009-02-18
i have used gscan2pdf and i have pieced together a 60 page document and saved it as a pdf a few days ago

stupidly i did not check the file before i saved it and today i open the pdf file and find that page 21 is upside down

there is no security or password on the file in anyway shape or form

i was thinking pdftk might do the trick
i used it to piece togther the pdf part files i saved

i saved my work every 15 pages or so and pieced it together like this

pdftk file1.pdf file2.pdf file3.pdf cat output complete.pdf verbose

and again to make it even tougher i stupidly deleted my part files before i checked it
man i feel so stupid right about now

anyone got any ideas???

thanks

---

### Post by cbtengr on 2009-02-18
Install pdfedit from Synaptic.  You should be able to select the page & rotate it.

---

### Post by wangsuda on 2009-02-18
> **stinger30au said:**
> i have used gscan2pdf and i have pieced together a 60 page document and saved it as a pdf a few days ago

stupidly i did not check the file before i saved it and today i open the pdf file and find that page 21 is upside down

there is no security or password on the file in anyway shape or form

i was thinking pdftk might do the trick
i used it to piece togther the pdf part files i saved

i saved my work every 15 pages or so and pieced it together like this

pdftk file1.pdf file2.pdf file3.pdf cat output complete.pdf verbose

and again to make it even tougher i stupidly deleted my part files before i checked it
man i feel so stupid right about now

anyone got any ideas???

thanks

You could try Adobe Reader for Linux systems. They are located at [http://get.adobe.com/reader/?promoid=BUIGO](http://get.adobe.com/reader/?promoid=BUIGO)

---

### Post by kaibob on 2009-02-18
The pdftk man page explains how to rotate pages. The following command rotates page 21 of the document, in.pdf, and creates the document, out.pdf. The rotation is 180 degrees. 

```
pdftk in.pdf cat 1-20 21S 22-end output out.pdf
```

It seems there should be a way to rotate just one page without specifying the other pages, but I couldn't find it. I tried the above command on a 49 page PDF document, and it did work. Still, you should have a backup copy of your original.

---

### Post by stinger30au on 2009-02-18
> **kaibob said:**
> The pdftk man page explains how to rotate pages. The following command rotates page 21 of the document, in.pdf, and creates the document, out.pdf. The rotation is 180 degrees. 

```
pdftk in.pdf cat 1-20 21S 22-end output out.pdf
```

It seems there should be a way to rotate just one page without specifying the other pages, but I couldn't find it. I tried the above command on a 49 page PDF document, and it did work. Still, you should have a backup copy of your original.


thanks i will make a backup of my original and try it


worked a treat!!!

thank you so much!

---

### Post by wangsuda on 2009-02-18
> **cbtengr said:**
> Install pdfedit from Synaptic.  You should be able to select the page & rotate it.
This worked great for me in compiling various PDF documents into one file. Thank you!

---

