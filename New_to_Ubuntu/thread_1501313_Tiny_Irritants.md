---
title: "Tiny Irritants"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jalirious on 2010-06-04
Hi, does anyone know a fix for these random issues?

1) When I use a text editor (e.g. emacs) can I set it to default that the terminal remains operational (i.e. no need for the "&")

2) I use pdflatex a lot, is there a way to make the autocomplete function recognise I want to open the file with extension ".pdf" rather than .aux, .tex etc

e.g. 

evince ne [->tab to complete]

goes to 

evince new. (?)

instead of 

evince new.pdf (the only pdf in the directory - obviously what I want)

3) Often I open up something CPU heavy, like GIMP or Synaptic Package Manager. It takes a few seconds to load and as I'm impatient I start doing something else. 

Then the application finally starts, blocking out what I just started doing.

I know it's there. I opened it 5 seconds before. Can I set it to open in the background so I can get to it after I finish the last thing? Just put a notifier on the toolbar or something.


None of these start to approach significant, but they are tiny vexes I would like to eradicate.

Ben.

---

### Post by kerry_s on 2010-06-04
1) & 2) your just being lazy there, how hard can it be to add & on the end or to type 1 more letter & <tab>

3) gconf-editor-> apps-> metacity-> focus_new_windows, change smart to strict.

---

### Post by SoFl W on 2010-06-04
> **jalirious said:**
> 
evince ne [->tab to complete] 

It isn't the only "new." in the directory though.  The tab feature has no idea what the letters "evince" are, "evince" doesn't get processed until after you hit return.

---

### Post by wojox on 2010-06-04
1. Open a tab or another terminal.

---

### Post by jalirious on 2010-06-04
Fair points. I plead ignorance rather than apathy. 

I know it's lazy not to want to "shift-7" after every application command, but surely the point of linux is the flexibility to customise? That said, I would have expected there to be an option to set the "&" as default.

Those haitians think they've got it bad..

Anyway, thank you for your comments.

---

