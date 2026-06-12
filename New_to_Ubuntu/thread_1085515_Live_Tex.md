---
title: "Live Tex"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by amylase on 2009-03-03
Hi everyone, a quick basic question. I installed Live Tex using Synaptic Package Manager. After installation, I can't find anything in the Applications menu to allow me to load the application. Where is it?

Thanks very much.

---

### Post by skymera on 2009-03-03
Can you run it from the terminal?

---

### Post by romitm on 2009-03-03
Run latex from the terminal. Enter 'man latex' to get the details.

---

### Post by Stefan_K on 2009-03-03
Hi,

consider to use a LaTeX editor like Kile or TeXmaker.

Stefan

---

### Post by amylase on 2009-03-07
Thanks everyone. Problem solved. Turned out Live Tex was probably only the Tex engine. I found Texmacs in applications menu which let me do Tex stuff in GUI environment. Went on to try a few other Tex utilities namely: Kile, Lyx, Texmaker, OooLaTeX, Texworks and Bakoma. Last three (OooLaTeX, Texworks and Bakoma) I found easiest to use.

---

### Post by David Biau on 2009-03-07
Hello,

i am new to Ubuntu and beginner to latex. I have installed tex live (full and then kile and I encounter some problems: I cannot edit any latex file with kyle: I had problems with okular something then with latex that could not be found, etc.

For those who have installed ubuntu 8.10, tex live and kile: have I missed something somewhere?

thanks


ps: I am not even sure I'll be able to find my message bc I am new to forums too...

---

### Post by amylase on 2009-03-08
> **David Biau said:**
> Hello,
i am new to Ubuntu and beginner to latex. I have installed tex live (full and then kile and I encounter some problems: I cannot edit any latex file with kyle: I had problems with okular something then with latex that could not be found, etc.
For those who have installed ubuntu 8.10, tex live and kile: have I missed something somewhere?
thanks
ps: I am not even sure I'll be able to find my message bc I am new to forums too...

Hi David,

Not too sure what you mean by "cannot edit any latex file". I installed my Kile straight from Synaptic Package Manager. I'm using Kile 2.0 on Ubuntu 8.10. To test it I opened a test file whose content is like this:
> \documentclass{article}
\title{Cartesian closed categories and the price of eggs}
\author{Jane Doe}
\date{September 1994}
\begin{document}
   \maketitle
   Hello world!
\end{document}
I could add and delete things freely in Kile. Next I pretty much pressed these buttons in order: "Quick Build" -> "DVItoPS" -> "PS->PDF". The output files went directly onto my desktop and display fine.

I suspect I'm as new as you (if not newer) to both Ubuntu and LaTeX. Not sure how proficient at coding Tex you are interested in becoming but to tell the truth I closed Kile about 60 seconds after I had a initial look at it. It was too complicated for me. Here are four Tex editors I found easier to use:

(1) **Texworks**. Let's you input code on one half of the screen and generates output on the other half of the screen.[http://www.tug.org/texworks/](http://www.tug.org/texworks/)
To install it, you best add it to your repository by typing this single line in command line:
> addrepo deb [http://ppa.launchpad.net/martin-texberatung/ubuntu](http://ppa.launchpad.net/martin-texberatung/ubuntu) hardy main
(space bar between ubuntu and hardy)

Once it's added, you can just go to "System" -> "Administration" -> "Synaptic Package Manager" and search for "Texworks" and install it automatically from there.

Note: if you don't have addrepo command on your system, just type these two lines in commandline to get it installed:
> sudo wget [http://mac4deb.googlepages.com/addrepo](http://mac4deb.googlepages.com/addrepo) -O /usr/bin/addrepo
sudo chmod +x /usr/bin/addrepo


(2) **OOoLaTeX** is quite handy also. It lets you insert small pieces of Tex into Open Office. Here is a thread explaining step by step how to install it. 
[http://ubuntuforums.org/showthread.php?t=334218&highlight=ooolatex](http://ubuntuforums.org/showthread.php?t=334218&highlight=ooolatex)

(3) Here is an interactive online tool called **Equation Editor**. It lets you build your equation by clicking a few simple buttons like building a lego model. TeX code is generated for you.
[http://test.izyba.com/equationeditor/equationeditor.php](http://test.izyba.com/equationeditor/equationeditor.php)

(4) **BaKoMa Tex** is probably the easiest to use in my opinion unfortunately it's not free, is closed source, and does not run natively in Linux. 31-day evaluation version is available from [http://www.bakoma-tex.com](http://www.bakoma-tex.com) and runs well via WINE. 

Hope these help.

---

