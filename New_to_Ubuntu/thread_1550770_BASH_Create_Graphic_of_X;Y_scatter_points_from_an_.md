---
title: "BASH: Create Graphic of X;Y scatter points from an ASCII  file"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-08-11
Hello,

I would like to generate a **JPG **file to plot an ASCII file of numerical data, **[COLOR="Red"]without X11 from the command line (bash)[/COLOR]**:

```
X   Y
1  12
2  14
5  19
10  200
250 12 
275  36
```
the data X and Y are separated by a TAB 

it would be intended to be creating a jpg or png, or else, with the command line (I will run a crontab)

Which ideally suited application (cmomand line) would do the trick ?

thank a lot in advance if it is possible using linux. Up to now I could only find X11 grapher app from linux repositories :(

---

### Post by DaithiF on 2010-08-11
**gnuplot**, available in the repositories: ([http://packages.ubuntu.com/search?keywords=gnuplot](http://packages.ubuntu.com/search?keywords=gnuplot))

homepage: [http://www.gnuplot.info/](http://www.gnuplot.info/)

---

### Post by frenchn00b on 2010-08-11
> **DaithiF said:**
> **gnuplot**, available in the repositories: ([http://packages.ubuntu.com/search?keywords=gnuplot](http://packages.ubuntu.com/search?keywords=gnuplot))

homepage: [http://www.gnuplot.info/](http://www.gnuplot.info/)

I found this page about gnuplot, but visibly **[COLOR="Red"]it requires X11[/COLOR]** for makign the graph, there is automatic plt file for automatic loading and plotting under X11 , but it seems that under bash (no x) there is not ... -well
[http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html](http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html)

---

### Post by DaithiF on 2010-08-11
maybe i'm misunderstanding what you want to do, but i don't believe X is required.  You can pass in data & plot commands and generate a png file, all from the command line.

of course for viewing the png file then you would need some graphical tool, so maybe thats where i'm misunderstanding you.  Are you wanting to generate a plot using ascii symbols that you could therefore view (e.g. using cat) from the command line?

---

### Post by apmcd47 on 2010-08-11
> **frenchn00b said:**
> I found this page about gnuplot, but visibly **[COLOR="Red"]it requires X11[/COLOR]** for makign the graph, there is automatic plt file for automatic loading and plotting under X11 , but it seems that under bash (no x) there is not ... -well
[http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html](http://t16web.lanl.gov/Kawano/gnuplot/intro/working-e.html)

From [The FAQ:]("http://www.gnuplot.info/faq/faq.html#SECTION00034000000000000000")

> **1.4 Is gnuplot suitable for scripting?** 
Yes. Gnuplot can read in files containing additional commands during an interactive session, or it can be run in batch mode by piping a pre-existing file or a stream of commands to stdin. Gnuplot is used as a back-end graphics driver by such higher-level mathematical packages as Octave, and can easily be wrapped in a cgi script for use as a web-driven plot generator. 


So clearly it doesn't need X11, as not every web server will have one. You may need to have to specify the terminal type to be a graphics file (I don't use it so I don't know the switches to gnuplot).

Andrew

---

### Post by achase79 on 2010-08-11
It may be more difficult but you may also be able to script a way of using imagemagick

---

### Post by frenchn00b on 2010-08-12
> **achase79 said:**
> It may be more difficult but you may also be able to script a way of using imagemagick

I checked too into imagemagick but still nothing found.

I guess that those guys that plot and update stat graphs into webpages are using windows XP very certainly :(

---

### Post by DaithiF on 2010-08-12
> **frenchn00b said:**
> I checked too into imagemagick but still nothing found.

I guess that those guys that plot and update stat graphs into webpages are using windows XP very certainly :(

I'm confused, two people have already mentioned that you don't need X11 for gnuplot.  Do you not believe us?

Heres some output from an ubuntu server (no x11 installed):

```
~$ cat data.dat                # this is your data file
1       12
2       14
5       19
10      200
250     12
275     36

~$ cat demo.plt                # heres some simple gnuplot commands
set title "Graph title"
set xlabel "X-axis"
set ylabel "Y-axis"
set term png
set output "data.png"
plot "data.dat"

~$ gnuplot < demo.plt        # pipe the commands into gnuplot and it creates the graph 


```
and attached is the graph

---

### Post by frenchn00b on 2010-08-12
> **DaithiF said:**
> I'm confused, two people have already mentioned that you don't need X11 for gnuplot.  Do you not believe us?

Heres some output from an ubuntu server (no x11 installed):

```
~$ cat data.dat                # this is your data file
1       12
2       14
5       19
10      200
250     12
275     36

~$ cat demo.plt                # heres some simple gnuplot commands
set title "Graph title"
set xlabel "X-axis"
set ylabel "Y-axis"
set term png
set output "data.png"
plot "data.dat"

~$ gnuplot < demo.plt        # pipe the commands into gnuplot and it creates the graph 


```
and attached is the graph


> 
I'm confused, two people have already mentioned that you don't need X11 for gnuplot. Do you not believe us?


In the example there no output to  > FILENAMEOUTPUTIMAGE.JPEG, or I am confused too :(

As said on top, the PC is headless, which means tthat there is no monitor, nor X11. It is an apache server, and it requires to create a JPG of it without X11. In your example, it displays the graph onto X11.

:( :(

---

### Post by DaithiF on 2010-08-12
> **frenchn00b said:**
> In the example there no output to  > FILENAMEOUTPUTIMAGE.JPEG, or I am confused too :(

As said on top, the PC is headless, which means tthat there is no monitor, nor X11. It is an apache server, and it requires to create a JPG of it without X11. In your example, it displays the graph onto X11.
:( :(
Hi, 
my server too is headless, no monitor, no X11.  This command: **set output "data.png"** tells gnuplot what **file** to write the graph to.  At no point does it get displayed on or by the server.  You can do whatever you want with then that file, e.g serve it on a webpage through your apache server, etc.  The format is png rather than jpg, but if the image format is important there are tools you could use to convert it from one to the other (imagemagick convert being one such).

---

### Post by frenchn00b on 2010-08-12
> **DaithiF said:**
> Hi, 
my server too is headless, no monitor, no X11.  This command: **set output "data.png"** tells gnuplot what **file** to write the graph to.  At no point does it get displayed on or by the server.  You can do whatever you want with then that file, e.g serve it on a webpage through your apache server, etc.  The format is png rather than jpg, but if the image format is important there are tools you could use to convert it from one to the other (imagemagick convert being one such).

wow !! it sounds fantastic. I try this command tomorrow on the server. Thank you so much ! I let you know 2morrow if it worked !

---

