---
title: "Illegal Instruction"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by sandman88 on 2011-03-05
I am running ubuntu 10.04 server edition, my flexget stopped working a few days ago. sitting down to check the problem I began by running flexget and got the following

# flexget
Illegal Instruction

I tried to re-install flexget and got the same thing

# easy_install flexget
Illegal Instruction

my python is up-to date, and I am not sure what else I should check to fix the problem, any Ideas?

---

### Post by rosencrantz on 2011-03-05
If this error shows up with two different python modules like flexget and setuptools, there might be something wrong with your basic python. 'Illegal instruction' sounds like a C related error (SIGILL). Try reinstalling python andd maybe build-essential, just in case. Can you post your python version (output of python --version)? Are you able to run python scripts or use the python console?

Cheers
rosencrantz

---

