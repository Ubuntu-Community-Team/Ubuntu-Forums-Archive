---
title: "Advice on how to install no repository software"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by neophyte_of_linux on 2010-07-11
Hi, I would love some advice in simple terms (hand holding) on how to go about installing a special software program not in the repositories.  I am interested in nomographs and want to try making some with Pynomo ([www.pynomo.org](www.pynomo.org)). Yes I am a little wierd, I also ride a Moto Guzzi too.

I downloaded the tar file and have the Pocket Ubuntu Guide to help me when I get to that point.

But the website says I need certain other package files and this is some of my confusion.  It says I need a:

TeX/LaTex distro, i.e. MikTeX, teTeX

NumPy
SciPy
PIL
PyX

I was able to find numpy, scipy, pyx in Synaptic and I marked them and installed them.

I am not sure about the MikTeX, teTeX and PIL.  I could find some things that looked like TeX something or other but I'm not really sure if you can understand a newbie's confusion.  Also I didn't find anything called PIL.

I suppose I need to find and install the LaTeX distro and PIL before I try following the steps to install Pynomo from a tar?

Kind of stuck at the moment.  I don't know what to do specifically.

---

### Post by masque7 on 2010-07-12
Those are dependencies that PyNomo needs. 

You should untar the tar.gz of Pynomo first (Ubuntu has some of the requirements for it already). If it asks for dependencies, you can track these down using Synaptic package manager, as you have done.

miktex and tetex don't seem to be in the repos'; I think they are suggestions. Ubuntu comes with texlive-base preinstalled I believe, which may suffice.

The ubuntu pocket guide contains how to untar files. Whether you want to do it on the terminal/command-line or graphically, it should cover that. Here's my take on it:

1. Download PyNomo [here](http://sourceforge.net/projects/pynomo/files/pynomo/0.2.2/PyNomo-0.2.2.tar.gz/download)
2. If using Firefox, I believe by default files are downloaded to /home/[U]username
[/U](where username is your username e.g. 'masque7')
3. Double click the tar.gz file: Archive manager will open
4. Extract the tar.gz file to your /home/username directory
(This is the graphical way to do it)

This is a Python script. How to use it
5. Open a terminal. Applications > Accessories > Terminal
6. type pwd - this shows where you are
7. By default you will be in /home/username
8. type: python setup.py install

Hope that helps.

---

