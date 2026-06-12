---
title: "Installing drivers from source code"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Chris62 on 2009-06-25
Hi,

Could anyone help with this, please?

I have downloaded a file from the Edimax web site called EW-LinuxDriverCode.zip which contains the source code for a driver for an Edimax wireless PCI card.

What I don't know is how to create and install the driver from the source code.

My computer is a dual boot machine with Windows XP and Ubuntu 9.04. It seems (at the moment, at least) an easy matter to install the driver for Windows but I haven't a clue how to get the WiFi card set up in Ubuntu.

The Edimax web site says that the PCI card in question works with both Windows and Linux.

---

### Post by Locutus_of_Borg on 2009-06-25
please post the output of lspci|grep Network

there might be an easier way of getting your wireless to work

but to get started, first unzip the archive
```
unzip EW-LinuxDriverCode.zip
```
then cd to the directory
```
cd EW-LinuxDriverCode
```
and if there is a Makefile, you can see if it will just compile as is, or check if there is a configure script, in which case run ./configure first
e.g.
```
make
```
or
```
./configure && make
```
if either of these complete without error, you can then run
```
sudo make install
```
to actually install the driver, but then you might also need the firmware for your card, but all of this will be a lot easier for us to assist with if you post the output of that first command here

---

### Post by Chris62 on 2009-06-25
Many thanks for your help. I will be in touch next week partly because I have to go to the UK tomorrow for a few days (the computer is in France) and partly because the PCI card hasn't arrived yet so I can't post anything about the firmware yet.

So far, it doesn't look as daunting as I thought it would be.

Many thanks again

Chris

---

