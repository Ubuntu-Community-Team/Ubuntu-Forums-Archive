---
title: "converting file format"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Black Sun on 2010-01-07
hey friends, I have a portable media player that supports displaying text files that can be read over it's "very small screen" but the problem is it supports only *.txt files and all the books I want to read are in either html,chm or pdf format(mostly pdf), so is there any way I can convert my pdf files to txt files?

---

### Post by gradinaruvasile on 2010-01-07
Umm.. like open it in document viewer, press ctrl+a, copy, open Test Editor, paste it in, save it as a.txt? That is for pdf.
Html same thing, only open it in a browser.
Chm, i dunno, never used it (i know its compiled html, its the help documentation format aswell). Maybe brower also.

I dont recommend using OpenOffice for creating txt files. 

Also, the txt files may be unreadable (or with artifacts) by your player, because they use the unix text format. The formatting difference is the next line character, you can see it if you create a txt file and open it in Windows's Notepad.

There is a conversion tool package (terminal only) in the repositories, called tofrodos that has the todos and fromdos conversion tools to convert files to/from unix txt format to/from dos txt format.

---

### Post by Black Sun on 2010-01-07
> **gradinaruvasile said:**
> Umm.. like open it in document viewer, press ctrl+a, copy, open Test Editor, paste it in, save it as a.txt? That is for pdf.
Html same thing, only open it in a browser.
Chm, i dunno, never used it (i know its compiled html, its the help documentation format aswell). Maybe brower also.

I dont recommend using OpenOffice for creating txt files. 

Also, the txt files may be unreadable (or with artifacts) by your player, because they use the unix text format. The formatting difference is the next line character, you can see it if you create a txt file and open it in Windows's Notepad.

There is a conversion tool package (terminal only) in the repositories, called tofrodos that has the todos and fromdos conversion tools to convert files to/from unix txt format to/from dos txt format.

Actually I tried that trivial method of copy and paste but the text goes hay-weired in the text file due to formating reasons of pdf, for example say a single page, of the pdf I am trying to convert, is divided into 2 columns , like in magazines, then copying all the text from pdf to txt will keep that format intact, and since my PMP reads 1 line at a time it will actually reading a line consisting of 2 different paragraphs. all in all the problem persists...:(

---

### Post by aktiwers on 2010-01-08
There is a terminal app called pdftotext. You can use it by going to applications => accessories =>Terminal and type:
```
pdftotext <drag/drop PDF file here>
```[SIZE=1]Or type in the path to the PDF file manually[/SIZE]

Or go search Synaptic for "[Calibre]("apt:calibre")" without the quotes. (or install by clicking the link if you are in firefox)

Edit: or forgot to tell you that once Calibre is installed, you can find it under Applications => Office => Calibre
It will convert PDF to lots of formats including txt with lots of options.

---

### Post by Black Sun on 2010-01-08
hey [aktiwers]("http://ubuntuforums.org/member.php?u=80311"), I wasn't able to find the command line tool "pdftotext" that you have mentioned, and I need a command line tool only so that I can use it easily in the scripts. Can you please tell how to find the mentioned tool and install it...

---

### Post by Black Sun on 2010-01-08
oops, sorry, I tried running the tool, without doing anything else, and voila! it worked. Thank you very much...:D

There is one little more thing... ;)
The conversion inserts some unreadable character in the text (which unfortunately Iam not able to paste here), how can I remove such characters or this is due to the unix text file format and it needs to be converted to dos text format???

---

### Post by Black Sun on 2010-01-08
I tried the mentioned tool on one of the files with columns and I am facing the same problem and it mangles all the text form one column into other, so .... any suggestions?



Note: I am attaching the file I am trying to convert so you people can perform "tests" over it too.:D

---

### Post by kaibob on 2010-01-08
> **Black Sun said:**
> oops, sorry, I tried running the tool, without doing anything else, and voila! it worked. Thank you very much...:D

There is one little more thing... ;)
The conversion inserts some unreadable character in the text (which unfortunately Iam not able to paste here), how can I remove such characters or this is due to the unix text file format and it needs to be converted to dos text format???
By default, pdftotext inserts a page break which appears as an unreadable character. You can get rid of this with the -nopgbrk option. If that doesn't work, you can use the tr utility to filter out the characters and you can try a different encoding.

---

### Post by kaibob on 2010-01-08
> **Black Sun said:**
> I tried the mentioned tool on one of the files with columns and I am facing the same problem and it mangles all the text form one column into other, so .... any suggestions?



Note: I am attaching the file I am trying to convert so you people can perform "tests" over it too.:D

You can use the pdftotext -layout option, which retains the columns. But, the resulting text file is far from perfect. I don't know of any way to get a good result with pdftotext with a multi-column PDF document.

---

### Post by Black Sun on 2010-01-08
> **kaibob said:**
> By default, pdftotext inserts a page break which appears as an unreadable character. You can get rid of this with the -nopgbrk option. If that doesn't work, you can use the tr utility to filter out the characters and you can try a different encoding.


Thank  you very much, "-nopgbrk" option seems to solve the "unreadable character" problem, so I didn't try the "tr" utility but definitively would like to learn about it.

There still remains the problem of mangled text from columned pdf files...

---

### Post by Black Sun on 2010-01-08
OK, Now since I have checked my documents and found that most of them are not multi-column pdf files but rather simple pdf file, so the matter of multi-column can rest for a little while, but I also found that my shitty PMP is too idiotic and displayed garbeled text even for a text file that was perfectly viewable on my computer screen, so I decided to find out what is needed to be done so as to make the text file compatible with my PMP. Here are the steps...

1.) Convert the pdf file to text using no page break option 
                   pdftotext -nopgbrk *.pdf
2.) Then convert the resunting text file to dos format
                   unix2dos *.txt
And them following replacements are needed to be done in order to make the text properly viewable in PMP
3.) replace  &#8212;  with  -
4.) replace  &#8217;  with  ' 
5.) replace  &#8220;  with  " 
6.) replace  &#8221;  with  " 
7.) replace &#8211; with -

It is a tedious job to do this every time I want to transfer a file to PMP. How can I write a script for the above procedure? I assume there would be need to use "awk" inorder to perform the replacements and that is something I haven't learnt yet. 
Please Help...

---

### Post by Black Sun on 2010-01-08
Hey friends, I tried to write the needed script but I am not able to make the replacements that I intend to make. Can anyone please tell me why the sed commands seem to have no effect on the text file? Here is the script ...

```

#!/bin/sh

#Usage txt2pmp pdf_file_name

#Converting pdf file to text so that it is compatible with my PMP,i.e, Transcend MP840(4GB)...
#Following steps are to be followed
#1.) convert the pdf file to text format
#2.) the converted file is in unix format, convert it to dos format and then make the #     following replacements
#3.) replace  —  with "-"
#4.) replace  ’  with  ' 
#5.) replace  “  with  " 
#6.) replace  ”  with  " 
#7.) replace – with -

fileName=`basename "$1" .pdf`
pdftotext -nopgbrk "${fileName}.pdf"
unix2dos "${fileName}.txt"
sed "s/—/-/g" "${fileName}.txt" > "${fileName}_pmp.txt"
sed "s/’/'/g" "${fileName}.txt" > "${fileName}_pmp.txt"
sed 's/“/"/g' "${fileName}.txt" > "${fileName}_pmp.txt"
sed 's/”/"/g' "${fileName}.txt" > "${fileName}_pmp.txt"
sed 's/–/-/g' "${fileName}.txt" > "${fileName}_pmp.txt"
rm "${fileName}.txt"
# "${fileName}_pmp.txt" is the intended text file

```

---

### Post by kaibob on 2010-01-09
You can combine commands in sed as in the following. The -i option tells sed to edit and overwrite the existing file. Each sed command in your script appears to overwrite the file created by the previous sed command. 

```
sed -i 's/&#8212;/-/g ; s/&#8217;/'/g ; s/&#8220;/"/g ; s/&#8221;/"/g' inputfile
```

I'm not familiar with the unix to dos utility, but you can use sed to make this conversion. Also, my guess (and it's only a guess) is that you should make the character replacements before converting the file to dos newline format. 

[http://www.catonmat.net/blog/sed-one-liners-explained-part-one/](http://www.catonmat.net/blog/sed-one-liners-explained-part-one/)

---

### Post by Black Sun on 2010-01-10
Hey All, Thank you very much, the file is now fully compatible with the PMP , that "sed -i " command did the trick, however there was a problem due to double and single quotes (',") but that is solved, and just to remove the doubt of [kaibob]("http://ubuntuforums.org/member.php?u=595193") , I used the sed command after the conversion and it worked fine.

However if someone stumbles on the solution for the multi-column pdf to text conversion, I would be eagerly waiting...:popcorn:

Thank You All
fLiDe

---

