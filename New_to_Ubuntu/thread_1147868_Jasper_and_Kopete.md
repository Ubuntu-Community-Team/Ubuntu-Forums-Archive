---
title: "Jasper and Kopete"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by gatoguts on 2009-05-03
I am getting an error message when i try to use webcam in Kopete, telling me to install Jasper.  Can I do this in synaptic package manager, and if not what is the easiest way, step by step please

---

### Post by Alterax on 2009-05-04
Considering that synaptic has a search function, you might want to check it out first, before asking for help.

---

### Post by canadiandude007 on 2009-05-04
Unfortunately you need to install it yourself.

First, go here: [http://www.ece.uvic.ca/~mdadams/jasper/#download](http://www.ece.uvic.ca/~mdadams/jasper/#download)

Download the source code and then do the following.

> 
# go to the folder you downloaded the source from
cd <jasperFileNameHere> 

# you need to ensure you have all the necessary files to build the program
./configure 

# provided you have no errors then do
sudo make

# and if still no errors then do
sudo make install

# that should be it!


Good luck!

Jasper allows you to view Yahoo webcams within Kopete.

---

### Post by canadiandude007 on 2009-05-04
One other thing, this is helpful to build all sorts of programs (the ones that don't come from .deb files):

> sudo apt-get install build-essential

---

