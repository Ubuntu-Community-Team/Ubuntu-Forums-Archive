---
title: "Open Office Solver - linear models only?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by joeboe on 2009-02-10
The open office solver seems to give me a problem when I am trying to optimize non linear models. Under  excel solver, there seems to be no problem when I put the same numbers in. However, with open office solver I get: 

No solution was found. The model is not linear. 

Now can the open office solver do non-linear optimizations or is there some option that I am missing somewhere. 

Unfortunately this is a deciding factor on whether I switch back to windows as I need a spreadsheet based non-linear optimization solver for some of my economics courses...

Any help is much appreciated!!

---

### Post by Temposs on 2009-02-10
So, here's the wiki page for the Solver: [http://wiki.services.openoffice.org/wiki/Optimization_Solver](http://wiki.services.openoffice.org/wiki/Optimization_Solver)

From what I can tell, a linear model is assumed by default...I think because the linear solver in OO.org is better than the non-linear solver.

In the solver, click Options. Uncheck the "Assume linear model" box, and try your non-linear model again.

EDIT: To make sure the change was made, restart OpenOffice and then check to see that the option has persisted when you've started it up again.

---

### Post by Hospadar on 2009-02-10
It appears this feature is planned but not yet working well:
[http://wiki.services.openoffice.org/wiki/Optimization_Solver#Non-Linear_Programming](http://wiki.services.openoffice.org/wiki/Optimization_Solver#Non-Linear_Programming)

I don't really know anything about it, there may be other options, but unless you are interested in a more math heavy solution like octave or sage, you're probably out of luck

---

### Post by Leoncio on 2011-06-23
The libreoffice-nlpsolver package is still a beta, but might solve your problem (pardon the pun). ;)

---

### Post by frncz on 2011-06-23
how do you install nlpsolver?
I downloaded 
libreoffice-nlpsolver_0.9~beta1-6_all.deb

from [http://packages.debian.org/sid/all/libreoffice-nlpsolver/download](http://packages.debian.org/sid/all/libreoffice-nlpsolver/download)
installed it, updated the sources.list, but cannot seem to find it in Calc. I still have the Sun solver installed, which I cannot remove.
Can you help please?

Mike

---

