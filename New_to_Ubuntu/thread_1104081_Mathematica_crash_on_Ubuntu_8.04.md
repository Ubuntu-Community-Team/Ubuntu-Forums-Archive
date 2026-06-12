---
title: "Mathematica crash on Ubuntu 8.04"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by daroldl on 2009-03-23
I have installed Ubuntu 8.04 in a computer, and I am trying to use Mathematica 5 (I have proof with Math 5.2 and Math 6 also). If I start Mathematica with math command in a terminal it seems that it works. However when I run mathematica from a terminal, I obtain the following:

Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
Warning: translation table syntax error: Unknown keysym name:  osfActivate
Warning: ... found while parsing '<Key>osfActivate:PrimitiveParentActivate()'
Warning: translation table syntax error: Unknown keysym name:  osfCancel
Warning: ... found while parsing '<Key>osfCancel:PrimitiveParentCancel()'
Warning: translation table syntax error: Unknown keysym name:  osfBeginLine
Warning: ... found while parsing '<Key>osfBeginLine:PrimitiveTraverseHome()'
Warning: translation table syntax error: Unknown keysym name:  osfHelp

etc

The Kernel seems to work, because I can operate in the notebook, but if I try to save my notebook, or to open the Help menu, Mathematica shuts down and I obtain the following:

Mathematica has received the signal: SIGSEGV and has exited.
If possible, please report this problem to [email]support@wolfram.com[/email]
describing in in as much detail as possible what you were doing
when the problem occurred.

[1]+  Fallo de segmentación  mathematica

I would really appreciate help to solve this problem.

---

