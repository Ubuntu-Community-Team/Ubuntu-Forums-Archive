---
title: "can't save pdf"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by heron7 on 2010-12-08
I am having trouble saving pdf's .I noticed yesterday too it happened .It turns off almost reboots the hole machine,why?
I have also read here that firestarter is not maintained any longer,yet I  read on issue six of Ubuntu user mag nothing about it from Marcel G. 
In  fact that's where i first noticed the pdf problem trying to get a copy  of the documentation & just now it happened again. 
I wanted to find out what the lighting icon represents in detail & if i can do anything to fix allow or deny?..

---

### Post by John_Adams on 2010-12-08
Which app do you use to save pdfs?

---

### Post by heron7 on 2010-12-08
I have checked the permissions of the pdf in question as to firestarters documentation in pdf I think that too has been allowed. So why can't I save them? it reboots my whole system :(

---

### Post by heron7 on 2010-12-08
there you go I'm sharing ;) [http://media.techtarget.com/tss/static/books/wiley/masteringEJB3/downloads/MasteringEJB4thEd.pdf](http://media.techtarget.com/tss/static/books/wiley/masteringEJB3/downloads/MasteringEJB4thEd.pdf)  get your bean ahead ,

---

### Post by John_Adams on 2010-12-08
How exactly are you trying to save this pdf? Are you trying to save it from your browser?

---

### Post by heron7 on 2010-12-08
Yes on firefox.I had an idea to check if i could save it on google & it worked ,so it either is an add on,but i have save pdf's befor on firefox so i did change something but what . 
 thanks  Adams

---

### Post by heron7 on 2010-12-08
It's only fair to add to what i said up top about the Acer 5315 overheating with celeron cpu  a similar post on launchpad explains it .[http://www.computing.net/cgi-bin/relateds.cgi/celeron+cpu+overheats+linux/ALL](http://www.computing.net/cgi-bin/relateds.cgi/celeron+cpu+overheats+linux/ALL) 
* solved mine which is single core 1.7Ghz*[FONT=Arial] by ripping the bottom off & setting a cooling laptop fan under. Hence it being an off roader ;)

[/FONT]

---

### Post by John_Adams on 2010-12-08
Good. Either way, try 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install mozilla-acroread acroread-plugins

This should solve any plugin problems you're having with mozilla.

Don't forget to mark the thread as solved once your problem is.

---

