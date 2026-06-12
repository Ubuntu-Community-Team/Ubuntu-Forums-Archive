---
title: "Programming language for physics simulation"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by bwallum on 2011-06-12
Hi, I'm looking for a programming language that will enable me to define 50,000 points of different sized energy bundles (half positive, the other half negative), throw them out randomly from a central point and then graphically display how they combine and merge together in a 3D visualisation.

I expect heavy maths processing as the co-ordinates and velocity of each energy bundle (think particle if that word helps) change. The graphics bit will probably be a much lighter processing affair.

Any thoughts on which programming language to use given that I'll be running this on an AMD processor and would like a language that can best handle the maths computations.

---

### Post by idoitprone on 2011-06-12
I believe you should rephrase your question, since any programming language can do that. Heck you can do all of that in bash scripts or machine language, if your insane lol. I wonder how do you arrays in machine language or 3d arrays bash scripts lol.

The best choice is usually, c, c++, and java since they all have a rich set of mature utilities.

You should ask what tool-set or game engines you should use. Like image processing ImageJ is a good choice.
[http://en.wikipedia.org/wiki/Physics_engine#Scientific_engines](http://en.wikipedia.org/wiki/Physics_engine#Scientific_engines)

Do you ever consider buying a graphics card? Graphic cards handle these calculations better than an cpu

---

### Post by l3vity on 2011-06-12
As a physics student, we used C++ for all our programming. It may take longer to code than others such as python, but in a large simulation, the faster processing speed of c++ is noticeable.
I'm not sure which would be the best graphics option for you though, I have generally only needed to do histograms and simple graphs, and so ROOT has been great for me. It can handle other graph types, but I haven't played with it much to be honest. Their website is [http://root.cern.ch]("http://root.cern.ch/") 

If your going to be doing a lot of simulations, I'd recommend installing the GNU Scientific Library, it has a lot of useful functions, such as finding eigenvalues/vectors from matricies and the legendary Monte Carlo integrations, which are extremely useful in modelling.

---

### Post by bwallum on 2011-06-14
Thanks for the info. I think I could handle Fortran95 or even c++ to generate data tables of particle positions at any point in time. I could then use gnuplot to generate frames. Any suggestions for a renderer to run the frames as a simulation?

---

