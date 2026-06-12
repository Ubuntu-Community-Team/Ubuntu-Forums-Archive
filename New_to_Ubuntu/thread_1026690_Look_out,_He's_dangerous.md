---
title: "Look out, He's dangerous"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by joejoe148 on 2008-12-31
I suppose I could have titled this "now what?" also.  I started a few weeks ago interested in LEARNING linux and since then have installed and setup ubuntu twice, loaded and changed a bunch of programs, customized the crap out of it and realized that after the computer is running all you are doing is learning applications, not linux.  So i jumped off into Bash. I know enough to start trouble but not enough get out.  I need recommendations for a project that will take the basic knowledge that I have and apply it to unique linux situations.  so here is the question.  What is the next logical step to really learning linux? Is it a file and print server, a web server?  I hope you dont say compile my own:)

---

### Post by minsf on 2008-12-31
a quick reference: look at bash scripting in [http://www.linuxcommand.org](http://www.linuxcommand.org)

---

### Post by retskrad on 2008-12-31
Yo should really change the title.

---

### Post by LowSky on 2008-12-31
What are you going to be using the computer for? That really is the best way to learn. If you need a print or file server try to set one up. If not then learning its great but you have no actual use and the info will leave you as quickly as you learned it.

---

### Post by donkyhotay on 2008-12-31
Depends entirely on what your wanting to do with your computer. If your just wanting to delve more into bash I would recommend compiling some random programs from source if you haven't done so already. From there depending on how much you want to know about the CLI try start learning the basics of VI or emacs. Just using will give familiarity that gives proficiency. Now if you *really* want to learn how to use the CLI then use ctrl-alt-f2 to get yourself out of the GUI and into a straight CLI screen and start messing around with that (ctrl-alt-f7 will get you back to the GUI).

---

### Post by juanoleso on 2008-12-31
What I am doing is applying it to my work place.  I am trying to come up with ways that I can save the company money and improve work flow with linux.  Right now I am looking at HowTo setup Thin Clients with LTSP.

---

### Post by joejoe148 on 2008-12-31
OK, this is the deal.   I understand that reading about bash or Linux without daily use is not going to provide the kind of deep learning that I want.  I am looking for a progression from dipping my toes into linux with Ubuntu to what would be a logical next step.   my ultimate goal is to be more marketable in a tough economy.  How did you guys progress.  I know the way to learn it is to use it and that is what I am trying to do.  I just wanted a direction.

---

### Post by donkyhotay on 2008-12-31
I just used it, being a previous windows user I started out being heavily dependent on the GUI however after copying/pasting enough commands into the CLI based on recommendations on this forum I just learned what the various commands do and how to navigate my way around. Now I'm comfortable in either environment and just use whatever is better for the specific task I'm trying to do.

---

### Post by Stan% on 2008-12-31
> **joejoe148 said:**
> I suppose I could have titled this "now what?" also.  I started a few weeks ago interested in LEARNING linux and since then have installed and setup ubuntu twice, loaded and changed a bunch of programs, customized the crap out of it and realized that after the computer is running all you are doing is learning applications, not linux.  So i jumped off into Bash. I know enough to start trouble but not enough get out.  I need recommendations for a project that will take the basic knowledge that I have and apply it to unique linux situations.  so here is the question.  What is the next logical step to really learning linux? Is it a file and print server, a web server?  I hope you dont say compile my own:)

joejoe, 

I'm new to Linux too. I started with minsf's suggestion (post number 2).

Then went to this: [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) Here there are exercises at the end of each section.

Next will be here: [http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)

These are the best I've found so far.

---

### Post by scorp123 on 2008-12-31
> **joejoe148 said:**
> What is the next logical step to really learning linux?  Try Gentoo or "Linux from Scratch" ;)

Even though I am not using the two "for real" on any of my machines I found their "P.I.T.A." way of installation (everything is done manually!!) very helpful as far as learning and understanding were concerned.

---

### Post by joejoe148 on 2008-12-31
Thanks Stan and scorp, Now I have something to do tomorrow

---

### Post by minsf on 2009-01-09
after the tldp.org links mentioned above (regarding bash), you may want to cosider two directions (in terms of marketability)
1. System administration
2. LAMP 
of course there are many other directions, just a couple of ideas.

for the first option, i suggest checking [http://tldp.org/guides.html](http://tldp.org/guides.html) especially
The Linux Network Administrator's Guide, Second Edition
(nag2)
and The Linux System Administrators' Guide
(sag)
and the previously mentioned Linux From Scratch (but don't get it from tldp.org, but rather from the LFS website)
they are a bit outdated but good
[COLOR="Red"]Actually, if someone knows better links (more up to date for instace)- I would really appreciate their post![/COLOR]

For the second option (LAMP), you probably want to install it with 
```
 tasksel install lamp-server 
```
and then put your php scripts in /var/www 
and test them by directing your firefox to the url localhost/your_script_name.php
To learn PHP, start with the PHP wikibook and with the documentations in php.net
and a little (relevant) hijack: [COLOR="Red"] is there a LAMP forum inside ubuntuforums.org? [/COLOR]

---

### Post by joejoe148 on 2009-01-11
thanks for the suggestions.  System administration is something that need to evaluate.  and I already had lamp written somewhere.  Still playing with bash but have been sidetracked by my day job.  who needs sleep right?

---

