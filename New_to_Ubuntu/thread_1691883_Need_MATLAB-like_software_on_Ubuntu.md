---
title: "Need MATLAB-like software on Ubuntu"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by puntigamer on 2011-02-20
Hi guys,
which Matlab-like Linux software is the more similar (or the most compatible) to MATLAB?
I don't want to buy MATLAB for Linux or use a pirated one on Windows :(
Pls help!!

---

### Post by davidmohammed on 2011-02-20
[this]("http://ubuntuforums.org/archive/index.php/t-121078.html") thread is a little old - but hopefully will give you some stuff to look at and consider which is best for you.

---

### Post by puntigamer on 2011-02-20
Thanks, I will give them a try :)

---

### Post by kwacka on 2011-02-20
Check SciLab - it uses a language similar to matlab.

Another choice is GNU Octagon.

Windows 7 will run in a virtual set-up e.g. VirtualBox

---

### Post by deconstrained on 2011-02-20
To hell with Octave and GNUPlot. 

It's all about Python with the NumPy and MatPlotLib modules.

You get the advantage of working with a widely-used, easy to learn and very well-structured language that's built around the concept of modularity, ease of reading, OOP and code re-use. MatPlotLib and NumPy add loads of great numerical analysis and plotting tools.

---

### Post by puntigamer on 2011-02-20
We have to program in Matlab, so I have to create / be able to use a matlab code...

---

### Post by deconstrained on 2011-02-20
> **puntigamer said:**
> We have to program in Matlab, so I have to create / be able to use a matlab code...
Well...Matlab **is available for Linux/Unix** if you really want nothing else. The closest FOSS alternatives to it are Octave and SciLab. I recommend against Octave, however; although it's syntactically similar to Matlab it's sort of a halfhearted clone, so anything more advanced than basic plotting that you write in Octave isn't guaranteed to work in Matlab, and vice-versa.

---

### Post by puntigamer on 2011-02-21
I DON'T WANT to use Matlab, till it isn't necessary! Today it the teacher telled us, that we can do (almost) everything in Octace, we won't do any Matlab-specific :)

---

### Post by deconstrained on 2011-02-21
Okay fine, you can write Matlab scripts in Octave, just be aware that the larger and more complicated your program gets the more little elusive problems you may end up having to weed out once you try to use it in Matlab. Believe me, I've dealt with this before.

Since you'll be using Octave, I recommend QToctave if you want a nice interface ;-)

---

### Post by maqtanim on 2011-02-21
Octave is better, it can handle .m files. But there are some library issue.

---

### Post by puntigamer on 2011-02-23
I belive Octave will be enough for now... The QT interface is nothing extra, so I use it in terminal with a text editor... But it's ok, I'm learning from the official MATLAB book, and everything does the same in Octave.

---

