---
title: "Adobe dialog box in German"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by edzell on 2010-06-22
Running 64-bit 10.04 on my laptop.
When I try to open a pdf document via a link in Firefox, an adobe dialog box opens, in the German language. Although I can select English at the top, the diallog remains in German which I don't understand. I've tried clicking all the options (Druken, etc.) in turn but the pdf doesn't open. What's going on?

---

### Post by diesch on 2010-06-22
Could you please post a screenshot of that dialog box?

---

### Post by lovinglinux on 2010-06-23
I don't know what is going on, but I solved my PDF issues with [gPDF](https://addons.mozilla.org/en-US/firefox/addon/14814/) extension. It opens the links through Google Docs PDF viewer and works like a charm.

---

### Post by edzell on 2010-06-23
> **diesch said:**
> Could you please post a screenshot of that dialog box?

When dialog first appears, all is in German

After clicking on the language drop-down & selecting English, it looks like his: Note the options at the bottom are still German

:[ATTACH]161381[/ATTACH]

---

### Post by diesch on 2010-06-24
You have installed the German version of Acrobat Reader. 

If you have it from the partner repository: For some reasons the package with the German version is called *adobereader-deu*  while English version's package is called *acroread*.

Clicking on "Akzeptieren" (that "Accept") should open the PDF in the German version, but as you can't switch the language you may want to install the English version anyway.

---

### Post by edzell on 2010-06-24
> **diesch said:**
> You have installed the German version of Acrobat Reader. 

If you have it from the partner repository: For some reasons the package with the German version is called *adobereader-deu*  while English version's package is called *acroread*.

Clicking on "Akzeptieren" (that "Accept") should open the PDF in the German version, but as you can't switch the language you may want to install the English version anyway.

Done - Thank you.

---

