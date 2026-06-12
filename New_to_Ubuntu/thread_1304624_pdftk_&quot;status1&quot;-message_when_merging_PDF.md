---
title: "pdftk &quot;status:1&quot;-message when merging PDFs"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by tazztone on 2009-10-29
i use pdftk with this GUI [http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

when merging or joining PDFs, with certain PDFs i get the message "PDF was created: Status:1" and no file was created. 

what's the cause of this problem? is it a bug in pdftk or in the GUI? does pdftk have trouble with handling certain PDF file contents? can i merge those merge resistant PDFs with an other method?

---

### Post by XCan on 2009-10-29
Are you sure that message is caused by pdftk and not the gui? Try doing it from the command line with pdftk.

---

### Post by KIAaze on 2009-10-29
Here's how to use pdftk by command-line:
```
/usr/bin/pdftk PDF1.pdf PDF2.pdf cat output out.pdf
/usr/bin/pdftk *.pdf cat output out.pdf

```

cf also: [http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

Guipdftk will always output a message of the form "PDF was created: Status:X", where X is the exit status of the pdftk command.
0 = success
any number other than 0 = failure

Run guipdftk from a terminal to see the error output.

---

### Post by tazztone on 2009-10-30
the errors in the shell led me to the problem: can't have spaces in the directory name :p. simple but effective: rename folders
thx for your hints. :popcorn:

edit: whitespaces in pdf's name are also causing the error...

with pdfsam i had none of these problems and it has some additional useful features compared to pdftk and guipdftk to merge and split pdf files! [http://www.pdfsam.org]("http://www.pdfsam.org/")
:popcorn::popcorn:

---

