---
title: "My Printer Prints Color In Firefox..."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-15
However, I have told it to print black/white (draft) in the printer settings.

---

### Post by Psumi on 2010-01-20
Bump

---

### Post by lyall on 2010-01-20
try printing using the grayscale settings

I did a test to print to PDF using the grayscale and it works

good luck and have fun learning

---

### Post by Psumi on 2010-01-20
> **lyall said:**
> try printing using the grayscale settings

I did a test to print to PDF using the grayscale and it works

good luck and have fun learning

It's already grayscale, as seen here:

[img]http://i50.tinypic.com/28vx0md.png[/img]

---

### Post by lyall on 2010-01-20
Like I state I did a test to print to PDF using the grayscale and it works

install the cups-pdf and try printing to it so grayscale
and look at the pdf file that it creates.
it should be  grayscale.

then you can print the pdf file.  if you do print it and you do not need it any more delete it.

it is a place to start, until somebody else can give you a better answer

good luck and have fun learnig

---

### Post by Psumi on 2010-01-20
> **lyall said:**
> Like I state I did a test to print to PDF using the grayscale and it works

install the cups-pdf and try printing to it so grayscale
and look at the pdf file that it creates.
it should be  grayscale.

then you can print the pdf file.  if you do print it and you do not need it any more delete it.

it is a place to start, until somebody else can give you a better answer

good luck and have fun learnig

That's the problem, a test page is printed fine in grayscale, but in firefox, no.

---

### Post by Methuselah on 2010-01-20
See if you can pick the color tab when actually printing (that is, in the dialog that comes up when you choose print in firefox) and select grayscale there...it might make a difference.

---

### Post by Psumi on 2010-01-20
> **Methuselah said:**
> See if you can pick the color tab when actually printing (that is, in the dialog that comes up when you choose print in firefox) and select grayscale there...it might make a difference.

Already set to the same thing, still prints color:

[img]http://i48.tinypic.com/243j677.png[/img]

No other tabs or sections have color options than the ones I have shown.

---

### Post by Psumi on 2010-01-22
bump

---

### Post by 311005901 on 2010-01-22
What version of Ubuntu are you using?

---

### Post by 311005901 on 2010-01-22
If you're using Karmic, go to System>Administration>Printing and right click on your printer and go to "Properties".

On the left menu, select "Printer Options" and change the Printout Mode.

[IMG]http://img27.imageshack.us/img27/4292/pring.png[/IMG]

---

### Post by Psumi on 2010-01-22
> **311005901 said:**
> If you're using Karmic, go to System>Administration>Printing and right click on your printer and go to "Properties".

On the left menu, select "Printer Options" and change the Printout Mode.

See posts 3 and 4 in this topic, it's already set to grayscale, and yes, I do use karmic.

---

### Post by Psumi on 2010-01-22
Okay, so now I had to do a roundabout way to fix it.

1. Go to [http://localhost:631/](http://localhost:631/)

2. Go to Administration

3. Select the printer

4. Select Set Default Options under Administration Dropdown

5. Set the Printout Mode to grayscale.

Now it works apparently. :| But choosing draft causes it to use FastDraft and not Draft.

---

