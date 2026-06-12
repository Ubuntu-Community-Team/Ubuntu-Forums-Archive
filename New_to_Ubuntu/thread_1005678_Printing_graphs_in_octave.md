---
title: "Printing graphs in octave"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by mjstander on 2008-12-08
Hi

I am running octave in ubuntu hardy

I can set the axis limits using the axis([xmin xmax ymin ymax]) command and it seems to work when displaying the graphs. The problem is when i print the graphs to file the axis limits change back to what seems like the automatic scaling limits and not the limits I set. This is a problem because it makes comparing the graphs inconvenient.


Any help would be appreciated. 

From
Melch

---

### Post by jpkotta on 2008-12-12
I tried it on Intrepid and Hardy, and it works find for me.  
```
plot(randn(100,1))
axis([1 50 -1 1])
print -landscape plot.ps

```

My Hardy has a newer version of Gnuplot, though.
```
$ gnuplot --version
gnuplot 4.3 patchlevel 0

```

---

