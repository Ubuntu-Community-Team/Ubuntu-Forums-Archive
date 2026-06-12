---
title: "a python problem"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by sameer.india on 2009-02-20
Consider the square (&#8722;2.5,2 .5&#57503;×(&#8722;2.5,2.5&#57503; . Divide   the    square   into   a  1000×1000 lattice. Carry out 1000 iterations of the henon map [f(x,y&#57503;=(a&#8722;x2&#57475;by , x )] starting from each of the lattice points (You should break out of the iteration loop if the iterates get very large &#8211; say if either coordinate exceeds 10100 ). Print out the initial points whose final iterates are outside the initial square. Use gnuplot to plot these points (use the with dots option). You should see a fractal structure at the boundary of the region.

to do this i made a double-nested loop
i.e
while x<=2.5:
(indent)y=-2.5
(indent)while y<=2.5:
(indent)(indent)x1=x
(indent)(indent)y1=y
(indent)(indent)for i in range(1000):
(indent)(indent)(indent)print x1,y1
(indent)(indent)(indent)x1,y1 = f(x1,y1)
(indent)(indent)(indent)if abs(x1)>=1.0e+10 and abs(y1)>=1.0e+10:
(indent)(indent)(indent)(indent)break
(indent)(indent)if abs(x1)>2.5 or abs(y1)>2.5:
(indent)(indent)(indent)print >>g,x,y
(indent)(indent)y=y+dx
(indent)x=x+dx

but it works for a long time.
is there a faster possible program

---

### Post by rrashkin on 2009-02-20
I don't see where you ever define "dx".

---

### Post by sameer.india on 2009-02-20
i have only given you the loop the rest of the program is all definitions
dx=0.005=dy
x and y start from -2.5.

---

### Post by sameer.india on 2009-02-20
any solns

---

