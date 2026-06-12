---
title: "using pdflatex"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by arun ganesh on 2011-03-16
hi all,
I have installed the latex in Ubuntu 10.04. I'm a beginner and i'm working with pdflatex..i googled for Pdflatex pdftex followed some examples but didnt got the output..???
I typed some pdftex commands in gedit as
\pdfinfo{
/Author (name)
/title       (Getting Help in Pdflatex)
}

when  i compile from terminal i get the following errros..as

root@raju-desktop:/home/raju# pdftex my.tex
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
(./my.tex)
*

      Can someone suggest which is the best for getting started with pdflatex/pdftex???   Also what editor is required for latex beamer...

---

### Post by ChipOManiac on 2011-03-16
This might be a little off topic... but instead of editing everything by hand there is the alternative of doing it graphically with "LyX"... Of course doing manual is a good experience... :D

---

### Post by arun ganesh on 2011-03-16
> **ChipOManiac said:**
> This might be a little off topic... but instead of editing everything by hand there is the alternative of doing it graphically with "LyX"... Of course doing manual is a good experience... :D


So installing Lyx is a better option  ??? my main concern is that i want to use latex beamer...

---

### Post by ChipOManiac on 2011-03-16
LyX will, according to the the input you supply it (which is  incredibally word-processor like) create the LaTeX file and feed it to  the LaTeX program if everything is setup correctly (which allmost all  the time is)... It also supports beamer... so if you're going to give a  long presentation... LyX would be better...

Or if you want to have manual with a little help... try TeXMaker...

BTW: I have seen you say that you have a slow internet connection... :(

---

### Post by arun ganesh on 2011-03-17
> **ChipOManiac said:**
> LyX will, according to the the input you supply it (which is  incredibally word-processor like) create the LaTeX file and feed it to  the LaTeX program if everything is setup correctly (which allmost all  the time is)... It also supports beamer... so if you're going to give a  long presentation... LyX would be better...

Or if you want to have manual with a little help... try TeXMaker...

BTW: I have seen you say that you have a slow internet connection... :(

thanks man.
well yes i do remember quoting that my internet connection is slow,actually thing is that i'm a tarinnee here and the oragnisation has provided me slow net connections...well i will try to install lyx..and i tried to install manually but required dependicies...but some how i managed to install the latex beamer by using
sudo apt-get latex-beamer....now i'm trying to install 

sudo apt-get install lyx

---

### Post by rosencrantz on 2011-03-17
There's a difference between pdftex (plain tex) and pdflatex - you have to use the latter. There's nothing wrong with running it from CLI, as you get all compilation errors spewed out unfiltered right away. 
There is no special editor to use with beamer, in the end of the day, all .tex files are plain text anyway. I am quite happy with Kile (on KDE), it's got higly usable autocompletion, inline spell checking and various compilation profiles. However, you probably don't want to download all the KDE libs, if you're on Gnome and have a slow connection.
If you just want a lightweight editor, try TeXworks: [http://www.tug.org/texworks/](http://www.tug.org/texworks/)
With LyX they tried to get the WYSIWYG experience to LaTeX, IMHO not very successfully, as the rendering tends to differ a lot from the compiled PDF, and I'm not sure it can cope with prerendering beamer properly (it doesn't seem to have a lot of success with my beamer slides).

---

### Post by arun ganesh on 2011-03-17
> **rosencrantz said:**
> There's a difference between pdftex (plain tex) and pdflatex - you have to use the latter. There's nothing wrong with running it from CLI, as you get all compilation errors spewed out unfiltered right away. 
There is no special editor to use with beamer, in the end of the day, all .tex files are plain text anyway. I am quite happy with Kile (on KDE), it's got higly usable autocompletion, inline spell checking and various compilation profiles. However, you probably don't want to download all the KDE libs, if you're on Gnome and have a slow connection.
If you just want a lightweight editor, try TeXworks: [http://www.tug.org/texworks/](http://www.tug.org/texworks/)
With LyX they tried to get the WYSIWYG experience to LaTeX, IMHO not very successfully, as the rendering tends to differ a lot from the compiled PDF, and I'm not sure it can cope with prerendering beamer properly (it doesn't seem to have a lot of success with my beamer slides).

So exactly what should i do...I read the beameruser guide and they arent specific about the editors..So far i'm just using gedit and trying some commands ....and i save it as file.tex(for eg) and compile in terminal as
pdflatex/pdftex file.tex

and with many warnings somehow a pdf file name file.pdf is generated....
So i please let me know in depth is gedit is good and what i've doing is correct?????/ will that be helpful for beamer??????/

---

### Post by arun ganesh on 2011-03-17
To all ,
Thanks a lot for helping out ...Well  gedit is best editor and learned to create some pdf file and slides using beamer........

---

### Post by rosencrantz on 2011-03-17
Exactly. Use pdflatex, not pdftex. You can use any text editor you like, that's just a matter of taste and convenience. Gedit has no special latex features (compiler shortcuts, code insertion and so on...), so if you are as lazy as the rest of us, you'll probably want to look at TeXMaker [http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/) or at least GEdit's latex plugin [http://sourceforge.net/projects/gedit-latex/](http://sourceforge.net/projects/gedit-latex/) at some point. Right now, gedit is fine. There is no specific software for editing beamer documents.
pdflatex generates a lot of messages during compilation, as long as you get a PDF and it looks like you intended, don't worry. 
On the other hand, if you haven't used LaTeX a lot up to now, learning it from the beamer user guide is hard. The Not So Short Introduction is probably a good place to get to know the basics:
[www.ctan.org/tex-archive/info/lshort/english/lshort.pdf](www.ctan.org/tex-archive/info/lshort/english/lshort.pdf)

---

### Post by arun ganesh on 2011-03-17
> **rosencrantz said:**
> Exactly. Use pdflatex, not pdftex. You can use any text editor you like, that's just a matter of taste and convenience. Gedit has no special latex features (compiler shortcuts, code insertion and so on...), so if you are as lazy as the rest of us, you'll probably want to look at TeXMaker [http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/) or at least GEdit's latex plugin [http://sourceforge.net/projects/gedit-latex/](http://sourceforge.net/projects/gedit-latex/) at some point. Right now, gedit is fine. There is no specific software for editing beamer documents.
pdflatex generates a lot of messages during compilation, as long as you get a PDF and it looks like you intended, don't worry. 
On the other hand, if you haven't used LaTeX a lot up to now, learning it from the beamer user guide is hard. The Not So Short Introduction is probably a good place to get to know the basics:
[www.ctan.org/tex-archive/info/lshort/english/lshort.pdf]("http://www.ctan.org/tex-archive/info/lshort/english/lshort.pdf")

absolutely 100% right...i too figured out that..thank u

---

