---
title: "How to install application &quot;pdfcrop&quot; (install file is of type python script) ?"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by swarup on 2010-01-08
I am trying to install the application pdfcrop, a Python script that crops the white margins of PDF pages and rescales them to fit a standard size sheet of paper.

I have downloaded the application, to install it. The install file is of type python script. Now, what do I have to do to install it?

Here is the [web page]("http://pdfcrop.sourceforge.net/") describing the application, if that is helpful.

Here are the install instructions given on that page:

> How do I install PDFCrop?

PDFCrop depends on the following packages, which (I think) are included in the default installation of Debian (with one exception):

    * ps2pdf
    * pdf2ps
    * poster
    * pdftk (this is the exception)

Assuming that you have already installed these packages, then simply make sure the file "pdfcrop" is executable (i.e.: chmod +x pdfcrop) and copy it to a directory in your $PATH. For example: /home/eric/.bin/pdfcrop  Alternatively, you could (as root) copy it to /usr/local/bin/pdfcrop 

---

### Post by cariboo on 2010-01-08
Install pdftk, using Software Center, Add/Remove Applications, Synaptic, or the command line.

Next copy pdfcrop to /usr/local/bin you can do this by running the file-manager as root, Press Alt-F2 and type:

```
gksudo nautilus
```

or open an Applications-->Accessories-->Terminal and type:

```
sudo cp pdfcrop /usr/local/bin/
```

Once you have copied the file, you have to make it executable, if you are still in Nautilus, right-click the file and select Properties-->Permissions, make sure the file is owned by root, and mark **Allow executing file as program** is marked.

From the terminal type:

```
sudo chmod +x /usr/local/bin/pdfcrop
```

This is probably a command line program, so you will more than likely have to create a launcher for it.

---

### Post by swarup on 2010-01-08
Thank you. Worked perfectly.

---

