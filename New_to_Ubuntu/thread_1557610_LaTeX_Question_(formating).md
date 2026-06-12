---
title: "LaTeX Question (formating)"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Metazeno on 2010-08-21
I would like to divide the body of my document in to two columns. In the left column go the section headings and in the right column go the section text.

My attempt is to make a new command:
 \[FONT=Courier New]newdimen\sectionwidth[/FONT]
 [FONT=Courier New]\newdimen\resumewidth[/FONT]
 [FONT=Courier New]\sectionwidth=0.25 \textwidth[/FONT]
 [FONT=Courier New]\resumewidth=0.75 \textwidth[/FONT]
 [FONT=Courier New]\newcommand{\ressection}[1][/FONT]
 [FONT=Courier New]{[/FONT]
 [FONT=Courier New]  \hbox to 0pt[/FONT]
 [FONT=Courier New]  {[/FONT]
 [FONT=Courier New]    \hss[/FONT]
 [FONT=Courier New]    \vtop to 0pt[/FONT]
 [FONT=Courier New]    {[/FONT]
 [FONT=Courier New]      \leftskip=0pt[/FONT]
 [FONT=Courier New]      \hsize=\sectionwidth[/FONT]
 [FONT=Courier New]      \textwidth=\sectionwidth[/FONT]
 [FONT=Courier New]      \raggedright[/FONT]
 [FONT=Courier New]      \bf[/FONT]
 [FONT=Courier New]      #1[/FONT]
 [FONT=Courier New]      \vss[/FONT]
 [FONT=Courier New]    }[/FONT]
 [FONT=Courier New]  }[/FONT]
 [FONT=Courier New]  \vskip-\baselineskip[/FONT]
 [FONT=Courier New]}[/FONT]
Unfortunately this puts the section text where it would be normally and the section headings far off to the left outside the document body.

Does anyone know how to fix this?

---

