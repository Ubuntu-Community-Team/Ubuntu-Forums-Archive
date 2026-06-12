---
title: "Notes in OOo documents not showing after PDF export"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by tdmoore on 2009-01-11
Fairly new to Ubuntu but 100% committed to use at home.

Running Ibex 8.10.

Situation: using OOo 3.0 and fairly proficient with it.  I create document in Writer, export to PDF, toggle the export notes box and create my PDF file.

Open in Evince or even xpdf and for some reason the "notes" do not show up.  However if I open the same file in Adobe Acrobat Reader on my Windows PC, the notes are there.

I think Evince does a great job but wonder why it will not show my notes?

Can someone advise solution please?  Oh...and I have msfonts loaded.

Thanks in advance...the community has been a big help before and expecting same again!

---

### Post by Xiong Chiamiov on 2009-01-11
Sounds like Evince is using a cached version of the file (or Evince doesn't support notes).  Try deleting the file, then rewriting it, and see what happens.  An alternate name may help too.

---

### Post by NoBugs! on 2009-01-11
Sounds like you want Acrobat reader since it is the only one to support this?

It is available for Linux: [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

---

### Post by tdmoore on 2009-01-11
Have tried other very simple files and it seems as if Evince does not support notes.

Will try loading Adobe Reader to see if that works which would not be my preference.  Would like to see Evince do the trick...however do need to have the capability.

Thanks for the response.

---

### Post by tdmoore on 2009-01-11
OK...have downloaded Adobe Reader but these tar.gz files always give me problems.

No Bugs...can you assist me in loading this properly?  I have downloaded to my home folder, realize tar is like a zip file however the Read Me file is pretty technical to me.

Can I use Synaptic for this?

Thanks for the help!

---

### Post by tdmoore on 2009-01-11
<SOLVED>

Used the .deb package and gdebi installer.

As well, the Adobe reader package recognizes the notes from the OOo file.

Wish Evince would as well but I have the solution.

Thanks for the help again community!

---

