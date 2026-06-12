---
title: "pdf editing, merge even &amp; odd pages???"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by stinger30au on 2009-02-25
i have a 100 page book with double sided pages and a single sided scanner


can i scan the even pages and save as say "even.pdf"

and scan the odd pages and save as "odd.pdf"

can i use pdftk or similar to merge the even.pdf and odd.pdf to create the entire book so it comes out with all pages in correct order???


thanks

---

### Post by llamabr on 2009-02-25
My guess is that you could mess with it until it works.  pdftk will split it into all hundred pages.  Then you could sort them by even and odd, create two directories, and then use pdftk to join them back again.

Not the most elegant, but for a one time thing, it would work

---

### Post by kaibob on 2009-02-26
I do not know how to do what you want with a simple pdftk command line. I've been working to learn shell scripting and decided to write a shell script instead. You need to change the /target/directory in the script. Also, the files, even.pdf and odd.pdf, need to be in the target directory. When you execute the script, you will be asked for the total number of pages in even.pdf and odd.pdf. These numbers should be separated by a space. I've tested this script but a backup of all PDF files should be retained.

```
#!/bin/bash

cd /target/directory

echo -n "Enter pages in even.pdf and odd.pdf separated by a space: "

read allpages

evenpages=$(echo "$allpages" | cut -s -d ' ' -f1)
oddpages=$(echo "$allpages" | cut -s -d ' ' -f2)

if [ -z "$oddpages" ] ; then
echo "You did not type both page numbers!"
exit 1
fi

epage=1
opage=1

while [ $epage -le $evenpages ] ; do
     echo A$epage >> .pdf.tmp
     epage=$(($epage + 1))
     if [ $opage -le $oddpages ]; then
          echo B$opage >> .pdf.tmp
          opage=$(($opage + 1))
     fi 
done 

numberlist=$(cat .pdf.tmp)

pdftk A=even.pdf B=odd.pdf cat $numberlist output final.pdf

rm .pdf.tmp
```

---

### Post by stinger30au on 2009-02-26
sweet, thansk for the replies guys

will try it out over the weekend

---

### Post by chrisse13 on 2010-10-17
check out this simple recipe, no scripting required:
[http://binarystatic.wordpress.com/2010/10/17/interleaving-two-pdf-files/]("http://binarystatic.wordpress.com/2010/10/17/interleaving-two-pdf-files/")

---

### Post by ianni67 on 2010-11-27
> **chrisse13 said:**
> check out this simple recipe, no scripting required:
[http://binarystatic.wordpress.com/2010/10/17/interleaving-two-pdf-files/]("http://binarystatic.wordpress.com/2010/10/17/interleaving-two-pdf-files/")
That worked perrfectly for me, thank you very much!

---

### Post by omrico1 on 2012-01-26
There is a simple yet very efficient application I wrote, which provide a solution for that 
problem exactly.
[http://www.cs.tau.ac.il/~omricohe/pdfmerger/](http://www.cs.tau.ac.il/~omricohe/pdfmerger/)

if you like please leave a useful comment over there

---

### Post by HermanAB on 2012-01-26
pdfshuffler

---

