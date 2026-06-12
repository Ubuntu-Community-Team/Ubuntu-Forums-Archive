---
title: "How to print a PDF without xorg/x11 using console?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-13
Hello,

There is  a printer on a distant server, and I have quite some lot of pdf to print. Is there any ways to print a PDF without X11?

Usually I print with evince, rather than acroread ; but in this case, no X.

---

### Post by NCLI on 2009-12-13
Try [JPDFPrintCLI]("http://www.qoppa.com/pdfprintcli/index.html").

---

### Post by falconindy on 2009-12-13
Convert to postscript using pdftops and pipe it to lpr.

---

### Post by freak42 on 2009-12-13
I was successful printing on a remote machine with lpr (on a remote console with a remote pdf) simply like this
lpr filename.pdf

of course this uses all the default settings which you can change with command line options i guess so look at
man lpr

hth
matthias

---

### Post by frenchn00b on 2009-12-13
> 
If CUPS is handling the printing then you should be able to directly print PDF files from the command line as far as I know. I've printed PDF from commandline to CUPS printing queue on remote server at the office and it works perfectly. No need for other tools. Also according to the [CUPS documentation]("http://www.cups.org/documentation.php/options.html") it should print at once. 


ok here we try:

here we go let's try:```

~$ lp -d LEXMARK linux.pdf
request id is LEXMARK-13 (1 file(s))

```

It works

Cups prints PDF !!

---

