---
title: "Need Adobe reader"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Autodave on 2010-11-15
Dowloaded and installed newest version from Adobe website.  I can read PDFs while online, but I cannot save or print them.  It says to make sure it is in the path variable.  Does Linux have a path like Windoze?  If so, how do I edit it?  Or, if there is a completely different method for doing this, what is it?
I am running Ubuntu 10.4  32 bit.

---

### Post by Chronon on 2010-11-15
This page should answer your questions:
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by Frogs Hair on 2010-11-15
Here is another option I just tried it out . [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by beew on 2010-11-16
The document viewer (evince) bundled in Ubuntu can open pdf inline, save and print the documents. It is a lot faster than adobe too.

To use the document viewer to read pdf on line, install mozplugger from the repo (use Synaptic for example) Then open the terminal and type 

```
sudo gedit /etc/mozpluggerrc
```

Then scroll down to the section that says "Documents" and go to the block about pdf documents and edit mozpluggerrc so that it looks like this

> application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
        repeat noisy swallow(evince) fill needs_xembed: evince "$file"
	ACROREAD()
	repeat noisy swallow(Xpdf) fill needs_xembed: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(okular) fill needs_xembed: okular "$file"
        repeat noisy swallow(epdfview) fill needs_xembed: epdfview "$file"
	GV()
	repeat noisy swallow(evince) fill needs_xembed: evince "$file"


Basically this just involves moving the line with evince to the top of the block.

Then save and restart firefox (or whatever browser you use since mozplugger is the universal browser plugin) and you would be able to read pdf in your browser.

EDIT: The smilies are actually colons followed by a "p" for pdf.

---

