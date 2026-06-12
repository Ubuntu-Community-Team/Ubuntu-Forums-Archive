---
title: "problem installing qt libraries on 8.10"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Sp1ck on 2009-01-24
i'm having a problem with qt libraries on ubuntu 8.10

i get to the 3rd step the "Building" step 

i get past the ./configure part

but on the 

su -c "make install"

it then asks for a password

i type my system password and is says authentication failure

the install doc that comes in the package says i need the "root password"

is this the same as the system password or something else

---

### Post by OutOfReach on 2009-01-24
Why are you manually compiling?
Is there a problem with the Qt libraries in the repository?

---

### Post by handydan918 on 2009-01-24
First off, there should be a truly compelling reason to compile anything rather than install it from the repos. 

The qt libraries in question aren't in the repos?

---

### Post by Michael.Godawski on 2009-01-24
hi,

do you have a special reason for compiling?

The Root Account is disabled by default in Ubuntu. You can access root privileges for commands by sudo - temporarily and by sudo -i for a longer period of time.

The sudo password is the root password is the login password.

---

### Post by Sp1ck on 2009-01-24
i'm trying to install qt libraries to then install dev c++ for school

as for compiling instead for using the repository there is nothing in there called qt libraries so me being totally new to ubuntu and linux didn't know that those things in the repository were the qt libraries

---

### Post by snova on 2009-01-24
Just open Synaptic, search for **libqt4**- they should be in there.

A basic installation of Qt would include libqt4-core and libqt4-gui.

---

