---
title: "Installing &amp; using programs HOW to, re: teX live"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Nbala on 2009-11-18
Hello, 
I am very new to linux and I am used to click the install package and there you go!
I am trying to use teX live for some graduate work.
I succesfully installed teX using synaptics after searching the web.
Then I couldnt find the "program" anywhere, so searched some more, found out you need an app to run it and downloaded Kile. So now Kile is extracted, but what now?
The forums I've found say things like ' type install-tl in terminal etc' ok, so I access the dir and do this in terminal- it tells me install is not a command.......
Basically I just want to use teX thats it, I love Ubuntu so far, but why is it SO confounding and obscure in regards to installing apps? Whats wrong with "click on the item, it is installed, shows up in programs, then you run it" - seems like its uneccessarily complex to be honest. If it is a wiser OS, then shouldnt simplicity be germain?
Anyways my true question is ( in plain linux nuub English ) how do I USE teX live???
Where is it when installed? how do I run it??
Im using Karmic.
Thank you very much!

---

### Post by Tholley on 2009-11-18
I'm not familiar with teX, but do know if you download a program, it needs to be a .deb file (like windows .exe files) to work in Ubuntu.
 
If it is a .deb file, then once you download it, Ubuntu should automatically install it from there. 
 
Did you look in the repository to see if it was already part of a Linux package?

---

### Post by soni1770 on 2009-11-18
hi  so latex is allready on your computer when you install ubuntu
.................. 
                                                                                       things like kile are a graphical front end to the program  
..............
 for latex it's fine to just write the code and save it to a txt file, 
using gedit in applications/accessories menu is one way to do this
.........................                                                                                                                                                      
when you have your .txt file you will want to compile it
 in the command line navigate to the folder the .txt file is contained and type 
 ........... 
                                                                            latex example.txt 
to compile to .dvi  .
...................
or for a .pdf
 pdflatex example.txt
 .......................................                                                                                                                                               
you do this in the terminal, again this is found in  applications/accessories menu (look at the top left of your screen)
when first in the terminal type 
ls
to see what is contained in your current directory
you start of by default in your home directory
if you make a folder there called latex you can keep all you work together
to navigate to this folder type
cd latex
then type
ls 
to see what is contained there


maybe it's easier for you to use kile as it makes things a little more obivious, 
 ......................................
 it should have a button to press to compile the file
 check out  tobi.oetiker.ch/lshort/lshort.pdf or
 .............................                                                                            
The Not So Short Introduction to LATEX2&#949;  for lots of hints and tips. good luck

---

### Post by Nbala on 2009-11-19
Ok thank you very much- but I am not clear on the part: 
"for latex it's fine to just write the code and save it to a txt file, "
(**but then what do I do with this .txt file to run it as teX?)**

when you have your .txt file you will want to compile it
 in the command line navigate to the folder the .txt file is contained and type 
 ........... 
                                                                            latex example.txt 
to compile to .dvi  .
[COLOR=Red] (**Sorry, what do I type? I save it as name.txt, then _how_ do I compile it through terminal? Also, how to I access/execute said file once executed- if you search for posts by Nbala the only other is about my total confusion on how to execute a file, executables seem to be opened as documents automatically or not opened at as by error- Im a wiz at windows but this is like playing piano with your tounge to me!)**[/COLOR]

[COLOR=Blue]Thank you So much Soni1770 (and everyone else who is helping me, I really appreciate it- and I am doing this in order to help disabled children as a grad student, so its a good cause too!) 
**[COLOR=Navy]THX- Drew/Nbala[/COLOR]**
[/COLOR]

---

### Post by soni1770 on 2009-11-19
hello nbala, :popcorn:

whats up.

don't worry, that's just what i though when i first seen this stuff to, i'll try to talk you through it one step at a time, don't be afraid to ask any questions.

first.
we're going to need a latex file containing some words that the latex program will understand, 
it's easiest at this point to just copy and past all the text from my next post(will follow in a sec) into a .txt file 

go to the top left of your screen,
and find your way to
 Application/accessories/gedit text editor

open up the gedit

then copy and paste my next post into gedit. 
save the file somewhere

prob best to go to top left of screen again and open
places/homefolder

now go to top left of the box that opens and go to
file/create folder

create a folder with a name like 
latex, 

now save your gedit file to this folder.
lets save it as 

example.txt

ok

---

### Post by soni1770 on 2009-11-19
%  This is an example of a report prepared with LaTeX. 


\documentclass[12pt]{article}

%   Use \documentclass[12pt]{report} for a dissertation with seperate 
%   chapters. 


% Define add-on packages. graphicx allows for including graphics, 
% amssymb and amsmath for American Mathematical Society mathematical 
% symbols and notation, and color allows coloured text. 
\usepackage{graphicx,amssymb,amsmath}
\usepackage{color}


% Define the layout of the page 
\setlength{\oddsidemargin}{3mm}
\setlength{\textwidth}{154mm}
\setlength{\topmargin}{-23mm}
\setlength{\textheight}{252mm}
\renewcommand{\baselinestretch}{1.0}
\headheight 10mm
\headsep 10mm



% Begin the document itself. 
\begin{document}


% Define the text that will be put into the title. Using \Huge\bg 
% will use a very large font and make it bold. 
\title{\Huge\bf Example for Nbala}



% Define the author's name. 
\author{soni1770}

% Make the title, including putting the author's name and the current date.
\maketitle 

% You could make the title manually, if you prefer to have more control 
% over it. 





\begin{abstract}
This LaTeX file gives an example of typesetting a basic document 
using simple LaTeX commands. The document is laid out in the 
style of an article. 
\end{abstract}





\section{Introduction} 
\label{sec_intro}

This is the Introduction. It introduces things. 

This is an example LaTeX document. A good place to look for answers is {\em The Not So Short Introduction to LATEX2&#949;}.




\section{The Development of the Field}
\label{sec_devel}

This is the second section. It describes the development of the 
field. The field was introduced in Section~\ref{sec_intro} 
and the method is described in Section~\ref{sec_method} later. 

This is a new paragraph. Note that the first paragraph of a 
section is not indented, but later paragraphs are indented. 





\section{The Method}
\label{sec_method}

This is the third section. It describes the development of the 
field. The field was introduced in Section~\ref{sec_intro} 
and the results are presented in Section~\ref{sec_results}. 



This paragraph uses a table. The methods are listed in the 
table which is called Table~\ref{table1}. 


\begin{table}
\begin{center}
\begin{tabular}{ccc}
Method & Description & Usefulness 
%\hline
\\
 1  &  First method  & Failed 
\\
 2  &  Second method & Failed 
\\
 3  &  Third method  & Failed 
\\
 4  &  Fourth method & Failed 
\\
 5  &  Fifth method  & Worked 
\\
\end{tabular}
\caption{This is table lists things.}
\label{table1}
\end{center}
\end{table}








\section{Results}
\label{sec_results}

This is the fourth section. It describes the results. 
The field was introduced in Section~\ref{sec_intro} and 
the method described in Section~\ref{sec_method}. 
The results are discussed in Section~\ref{sec_discuss}. 

This paragraph uses a table. The methods are listed in the 
table which is called Table~\ref{table1}. 






\section{Discussion}
\label{sec_discuss}

This is the fifth section. It discusses the results. 
The field was introduced in Section~\ref{sec_intro} and 
the method described in Section~\ref{sec_method}. 
The results are presented in Section~\ref{sec_discuss}. 

This paragraph uses a figure. The figure shows something. 
It is called Figure~\ref{that_nice_figure}. 





\begin{figure}
\begin{center}
\includegraphics[height=70mm]{fig1.eps}
\caption{This is the figure.}
\label{that_nice_figure}
\end{center}
\end{figure}


Figures and tables are called floats: they can float around in the 
document and LaTeX will try to judge the best place to put them. 




\section{Conclusions}
\label{sec_conclude}

Here are the conclusions. 





\section{Acknowledgements}
\label{sec_acknow}

The author wishes to thank everyone who contributed to this work. 
They helped a lot. 






% This References section is set out in a very basic manual way. 
% It works effectively, but many people prefer to put the references 
% in a thebibliography environment using \begin{thebibliography}{99} 
% and \end{thebibliography}. Preceeding each reference then with 
% \bibitem uses BibTeX. However, BibTeX is a bit more difficult to 
% get working in the correct format (it usually requires using 
% \bibliographystyle{astron} with a astron.sty file to get it to 
% format correctly. 
% The method used below is basic but works adequately. 



\section{References}
\label{sec_refs}


\begin{list}{}{ 
     \setlength{\leftmargin}{7mm} \setlength{\itemindent}{-7mm} 
     \setlength{\labelwidth}{0mm} \setlength{\itemsep}{-1mm} }
\item  Copernicus, N., 1543. {\em De Revolutionibus Orbium Coelestium}, 
       first edition. 
\item  Galilei, G., 1610. {\em Siderius Nuncius}, first edition, 
       publ. Venice. 
\item  Herschel, W. F., 1781. Phil. Trans. Roy. Soc., 71, 492. 
\item  Newton, I., 1687. {\em Philosophiae Naturalis Principia 
       Mathematica}, first edition, publ. London. 
\item  Saha, P., Burgess, D., Jones, B., Murray C., Malik, K. 2008, 
       {\em ASTM005 Research Methods in Astronomy} course notes, 
       publ. Queen Mary,  University of London. 
\end{list}

\end{document}

---

### Post by soni1770 on 2009-11-19
you'll notice that line that start with
% are there to tell you stuff about whats going on, 
when you run latex the program will ignore these.


ok, now you've got a .txt file in a form that latex will understand

next we want to compile this .txt file with the latex program

we're going to open the terminal to do this
again top left,
 applications/accessories/terminal 

a terminal will pop up. you should be able to type stuff in.

first type in 

ls

and hit enter
this will give you a list of all the files and folders in your home directory,
 somewhere on this list you should see a folder called 

latex

we want to move into this folder, to do this we use the command

cd

for change directory

type into the terminal

cd latex 

and hit enter

how type in

ls
and hit enter

this should list all the files in this folder,
at this point there should be only one listed
the one we saved with gedit


example.txt



now type into the terminal


latex example.txt

the latex program will run, 
you'll prob get some errors,  just keep hitting enter untill the terminal returns to the command promt


now if you go to the top left of the screen and fine the folder
places/home folder/latex
open this folder,
you'll see a few files all starting with example

double click on the one that says 

example.dvi

you'll see that there are a few question marks and other problems, 
this is because latex uses it's first run to fiqire some stuff out.

go back to the terminal and again type 

latex example.txt

again open up the example.dvi file

the question marks should have gone.

now .dvi is allright but .pdf is i think better.

to make a pdf

again in the terminal type

pdflatex example.txt

check out the latex folder again
there should be a file called 
example.pdf,

---

### Post by soni1770 on 2009-11-19
now, you talked about kile.

kile is just a front end to what we've just done.

the compile button in kile is just like typing 

latex example.txt


but it can be very usefull as it can make different parts of your code be different colours depending on what they do, easier to find mistakes to a the lines will have numbers and stuff.

well, try it out, after you've got it working you can mess around with kile. 
sometimes i use it but sometimes not.

regards
soni

---

### Post by XCan on 2009-11-19
It seems you are completely new to latex (I assume you want latex and not tex). Thus I think it is wise for you to read up a bit on what latex is by, for example, reading [http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/](http://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/) and the manual [http://tobi.oetiker.ch/lshort/lshort.pdf](http://tobi.oetiker.ch/lshort/lshort.pdf) .
 
I assume it will take you a while to get into it. But if you get over the initial threshold, you'll realize why people find Word and other WYSIWYG editors completely rediculess for typesetting.

---

