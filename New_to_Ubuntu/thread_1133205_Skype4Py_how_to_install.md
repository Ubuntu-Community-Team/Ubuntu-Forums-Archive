---
title: "Skype4Py how to install"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by saskatchewan on 2009-04-22
Hi

I downloaded Skype4Py to my documents folder but can't  figure out how to install it.

Can anyone tell me how to do this?

---

### Post by flyingsliverfin on 2009-04-22
is skype4py the same as thr normal skype?

if it is just use synaptic package manager (system-> administration-> synaptic   enter your pass, then search skype)

if it is not then I can't help sorry

---

### Post by saskatchewan on 2009-04-27
Supposedly Skype4py allows Linux users to do thinks like Text messages etc via skype.

I have followed the install instructions I found on
[https://developer.skype.com/wiki/Skype4Py/installation](https://developer.skype.com/wiki/Skype4Py/installation)

But, nothing shows up in my Synaptic?

Can someone tell me what I should do?

---

### Post by pekka72 on 2012-08-22
sudo tar xvfz Skype4Py-1.0.32.0.tar.gz
sudo chmod a+rx Skype4Py-1.0.32.0/
sudo chmod a+rx Skype4Py-1.0.32.0/examples/
sudo chmod a+rx Skype4Py-1.0.32.0/Skype4Py/
sudo chmod a+rx Skype4Py-1.0.32.0/unittests/
cd Skype4Py-1.0.32.0/
setup.py --help
sudo python setup.py build
sudo python setup.py install

but Skype4py is known to be undtable on recent unbuntu versions (I have 12.04). It causes segmentation faults about half of the time.

---

