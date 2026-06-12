---
title: "Ubuntu Software Center HELP!!"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by The3irikr on 2009-12-18
Hi, I wanted to install a game on the software center (sometimes called the add/remove place). I keep getting this error.
E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch): 

and when i go to synaptic package manager, it says there's this broken package..???

i'm on an Ubutnu 9.10

---

### Post by skymera on 2009-12-18
try:

sudo apt-get update
sudo apt-get -f upgrade

( i think that's the right commands, i get mixed up! :P)

---

