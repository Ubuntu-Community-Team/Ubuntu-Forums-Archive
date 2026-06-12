---
title: "problem with ndiswrapper"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by charles woodward on 2005-10-11
I've just installed Linux (ubuntu 5.10) on one of my drives - I have a wireless network.  So

I followed instructions for compiling ndiswrapper - but it fails - cant find gcc-3.4 (command not found)

This is not surprising - as the only version I seem to have is gcc-4.0.   Can anyonw tell me how I get the makefiles to look for gcc-4.0 instead of gcc-3.4 (assuming that is the correct process) - I've at long last found a version of Linux that looks reasonable (I tried REDhat a few years back - but couldn't get wireless to work at all)

If I can get this wireless network running I'll be able to get rid of some of my windows stuff.

---

### Post by charles woodward on 2005-10-11
My years with unix seem to have come to my rescue - I `symbolically linked gcc-3.4 to gcc-4.0 (command is ln -s ) and it all seems to work ok now.  

As an aside I think this is one of the problems with linux - most end users don't know their way around a computer and would never fathom that one.

---

### Post by Mitt3ns on 2005-10-11
Well, if you have checked out Ubuntu then youll see that not all the packages are installed automatically. I thought the same thing, i tried to use gcc, but it didnt work. I am running windows right now, but, i think to install all of those programs (such as gcc) you have to go to package manager somewhere in one of the menus. Hope that i at least gave you a little help :/

---

### Post by knappen on 2005-10-12
You could not use synaptic to install ndiswrapper?

---

### Post by ralin on 2005-10-14
[QUOTE=charles woodward]My years with unix seem to have come to my rescue - I `symbolically linked gcc-3.4 to gcc-4.0 (command is ln -s ) and it all seems to work ok now.  

As an aside I think this is one of the problems with linux - most end users don't know their way around a computer and would never fathom that one.[/QUOTE]

what is the command line to do this?

---

### Post by brentoboy on 2005-10-14
[QUOTE=charles woodward]My years with unix seem to have come to my rescue - I `symbolically linked gcc-3.4 to gcc-4.0 (command is ln -s ) and it all seems to work ok now.  

As an aside I think this is one of the problems with linux - most end users don't know their way around a computer and would never fathom that one.[/QUOTE]

woooo, hold on their mate.
That might work short term, but your exerience is going to hang you.

There are incompatibilties between the two compilers.  those might be insignificant in many cases, but with low level modules (like ndiswrapper) an inconsistency could really kill you.

unlink it, and use synaptic to get gcc 3.4 - and the kernel headers, and build essential... all that stuff.

grab ndiswrapper from synaptic while you are at it - no need to compile from source, use the one the ubuntu-team put together and tested.

-just a thought.

---

