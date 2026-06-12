---
title: "A bash script for \LaTeX to pdf"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2009-06-11
If you're preparing a pdf document from \LaTeX that can not be compiled using pdflatex- for example your document might contain .eps files- then as far as I know you have to go through dvips, and then ps2pdf (please correct me if I'm wrong). This being the case, you will have to run the same commands lots of times. I have put together a bash script which can be used on any .tex file from any directory- improvements and suggestions are welcome!

1.  Put the following code in a file called (something like) makepdf.sh

#! /bin/bash

ERROR="Too few arguments : no file name specified"
[[ $# -eq 0 ]] && echo $ERROR && exit                 # no args? ... print error and exit

# check that the file exists
if [ -f $1.tex ] 
then
	# if it exists then latex it twice, dvips, then ps2pdf, then remove all the unneeded files
	latex $1.tex
	latex $1.tex
	dvips $1.dvi -o $1.ps
	ps2pdf $1.ps

	# these lines can be appended to delete other files, such as *.out
	rm *.aux
	rm *.log
	rm *.ps
	rm *.dvi
	rm *.toc
	rm *.lof
else
	# otherwise give this output line with a list of available tex files
	echo the file doesnt exist butthead! Choose one of these:
	ls *.tex
fi

2. Now make the file executable:

chmod +x myscript.sh

3. Finally move it to

/usr/local/bin

You can now use the script in any directory- to use it on myfile.tex, you would type:

makepdf.sh myfile

This would create myfile.pdf, and get rid of all of the intermediate files that \LaTeX needs to be the beautiful thing that it is.

Note: I typically only use this file when the document is completed- when I'm in the process of editing I usually just view the .dvi file after 1 compile. I put this bash script together to get the pdf and to clean up the directory.

---

### Post by ad_267 on 2009-06-11
For eps files I just use epstopdf to convert them to pdf before using pdflatex. I think rubber automatically does this conversion too. Rubber is a python script for automating LaTeX document compilation, it also handles things like running bibtex when requied and automatically running latex or pdflatex multiple times when required.

---

### Post by C. M .Hughes on 2009-06-11
So you make your .eps files into .pdf? That sounds interesting, I've not done that before. Thanks for the info about rubber, it sounds like it'll be worth looking into.

---

