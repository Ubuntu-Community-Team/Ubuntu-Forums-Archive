---
title: "trying to load emacs 23.1 on ubuntu 9.04"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by bantucrazed on 2009-10-07
When I configured 23.1, it offered the option to configure without x, so I did that.   The command the terminal suggested was:  ./configure --without-x.   I did this right after a ./configure, and that was what was suggested...I didn't undo anything.   Very new at this.  

Anyway, the terminal attempted to make the program, after ./configure, and took a long time doing it, too.    Now, when I enter this command, src/emacs -1, which is the command to make sure the program's been created, I get the following:  Cannot open termcap database file.   I'm interested in getting emacs and leaning to do more with the computer.   

In the alternative, is gedit able to get newsgroups?

I have ubuntu 9.04 remix on my netbook, and maybe should not load a lot of programs. 

Very new at this...

Thanks!

---

### Post by QIII on 2009-10-07
The easiest way to use Emacs if you are new to Ubuntu would be to install it from Synaptic and make sure you also install the GUI.

[http://books.google.com/books?id=-XLrpiHDYoQC&pg=PT170&lpg=PT170&dq=emacs+graphical+ubuntu&source=bl&ots=U8nC58ERdP&sig=yVx2EuAdUW5mEoAAxw06N0se8f8&hl=en&ei=LNHMSrLbApW3lAf06N3QBQ&sa=X&oi=book_result&ct=result&resnum=9#v=onepage&q=&f=false](http://books.google.com/books?id=-XLrpiHDYoQC&pg=PT170&lpg=PT170&dq=emacs+graphical+ubuntu&source=bl&ots=U8nC58ERdP&sig=yVx2EuAdUW5mEoAAxw06N0se8f8&hl=en&ei=LNHMSrLbApW3lAf06N3QBQ&sa=X&oi=book_result&ct=result&resnum=9#v=onepage&q=&f=false)

A good book for learning Emacs:

[http://www.powells.com/biblio/4-9780596006488-4](http://www.powells.com/biblio/4-9780596006488-4)

---

### Post by bantucrazed on 2009-10-07
i am very new to this, but i cannot find emacs in my synaptic package manager.   i did try sudo apt-get install emacs22, and this is what came-up:   Package emacs22 has no installation candidate

---

### Post by seamushc on 2009-10-07
Do the following:
```
sudo apt-get update
sudo apt-get install emacs22
or
sudo apt-get install emacs22-nox
```



Fyi, if you type a command in the terminal that isnt installed, ubuntu has a utility that will try and find a suitable package and tell you how to install it.

---

### Post by oldos2er on 2009-10-07
> **bantucrazed said:**
>  In the alternative, is gedit able to get newsgroups?

 No, gedit is a text editor, not a "kitchen sink" like emacs. However there is a very nice CLI Usenet client called slrn.

---

### Post by unutbu on 2009-10-07
The emacs-snapshot package provides emacs version 23.
One significant difference between emacs-snapshot and the other emacs packages is that with emacs-snapshot you can use nice-looking ttf fonts. To install, click System>Admin>Software sources, and enable the "universe" repository. Then click
System>Admin>Synaptic and install emacs-snapshot.

To set the default ttf font, just put something like this in ~/.emacs: 
```

(set-default-font "Monospace-12")
```

---

### Post by QIII on 2009-10-07
I would recommend against nox, only because I think someone new to Ubuntu and Linux would be more comfortable with a gui.

My opinion.

---

### Post by bantucrazed on 2009-10-07
i did sudo apt-get install emacs22-nox, and this is what was returned:  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs22-nox

---

### Post by bantucrazed on 2009-10-07
maybe i'm not using the package manager right, but i type in emacs or emacs-snapshot and no packagees show up...universe is enabled in software sources.    thanks anyway.  probably it's something really obvious i'm doing wrong, so obvious it never occurs that's the problem.

---

### Post by unutbu on 2009-10-07
Please post the output of 
```

sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by bantucrazed on 2009-10-07
not sure if my posts are showing up...i tried installing emacs-nox, and got this message:  sudo: unable to resolve host ria-laptop
: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package emacs22-nox
and that's it...no suggestions.    
then, i went into synaptic package manner to install emacs-snapshots, and enter it in the search term area, and nothing.   universe is checked in the software manager. 
i may try the simpler editor. 
again, i am probably not doing something really obvious, like not using synaptic correctly, and when i try to run the emacs command, it tells me there are all these packages but they don't sudo and they don't show up in synaptic. 
thanks anyway...either i'm doing something really dumb or maybe, possibly since the 9.04 version installed is for netbooks, these programs just aren't supposed to install b/c they're too big?

---

### Post by bantucrazed on 2009-10-07
seems to be working...emacs22's loading now.   i was afraid to update my packages b/c it seemed like so much was being downloaded, and package manager said it would take 8 hours, and that's with a wireless connection!   but, it just took a second.   we'll see! 
thanks again.

---

### Post by bantucrazed on 2009-10-07
i got emacs!   :).    thanks

---

