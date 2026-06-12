---
title: "How to run PDFtk"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by haydemon on 2009-02-05
I recently installed a program called PDFTK that supposedly allows me to manipulate PDF files. Right now I have a form that I need to fill-out online, but I cannot type anything inside any of the cells, as the file appears to be static (i.e., no editing allowed). My question is: how do I run PDFtk? I tried running it from the console, but all I get is this:
SYNOPSIS
       pdftk <input PDF files | - | PROMPT>
        [input_pw <input PDF owner passwords | PROMPT>]
        [<operation> <operation arguments>]
        [output <output filename | - | PROMPT>]
        [encrypt_40bit | encrypt_128bit]
        [allow <permissions>]
        [owner_pw <owner password | PROMPT>]
        [user_pw <user password | PROMPT>]
        [flatten] [compress | uncompress]
        [keep_first_id | keep_final_id] [drop_xfa]
        [verbose] [dont_ask | do_ask]
       Where:
        <operation> may be empty, or:
        [cat | attach_files | unpack_files | burst |
         fill_form | background | stamp | generate_fdf
         dump_data | dump_data_fields | update_info]
but still the app doesn't run. Any suggestions? Thx!:p

---

### Post by Pollox on 2009-02-06
PDFtk is a command line program, so you just run it in terminal and provide it with arguments.  Their site has some [simple examples]("http://www.accesspdf.com/article.php/20041129175231241").  You can also get a [gui for PDFtk]("http://www.paehl.de/pdf/gui_pdftk.html").

If you're just trying to fill out a PDF form, and Document Viewer/Evince isn't working, you might try "acroread" (Adobe's Acrobat reader, installable from Synaptic).  If you want more advanced editing features, you might try PDFedit, although I've found it to be a bit complicated to use at first.  If you're just trying to type onto a PDF that doesn't have form fields, you might try doing so in GIMP and printing to PDF.  You could also check out "flpsed" for some basic PDF editing.

---

### Post by haydemon on 2009-02-06
Thanks. I'll try it.

---

