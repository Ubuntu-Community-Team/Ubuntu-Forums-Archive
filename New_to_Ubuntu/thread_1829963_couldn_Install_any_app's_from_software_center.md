---
title: "couldn Install any app's from software center"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by shibu_sawyer on 2011-08-21
Well this is my problem,when i try to install any applicaton from software center or if I try to Update Ubuntu, All it displays is this : "Waiting for apt-get to exit"..
What might be the problem..?
I got to restart my PC and when i open s/w center again ,  and if i click any app it starts to install,but i cant restart my pc everytime,pls some one help me with this..

Thank you....
-->Shibu Sawyer<--

---

### Post by realzippy on 2011-08-21
open terminal and check if
```
sudo apt-get update
```
runs without problems to get a hint...

---

### Post by shibu_sawyer on 2011-08-21
> **realzippy said:**
> open terminal and check if
```
sudo apt-get update
```runs without problems to get a hint...

i did what you said at the end it displayed this;

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by realzippy on 2011-08-21
Did you have software center or synaptic opened when running this command?

---

### Post by shibu_sawyer on 2011-08-21
now again i tried..now there is no error...

---

### Post by realzippy on 2011-08-21
..if you had not software center or synaptic opened,maybe
that the auto update-manager ran in the backround.
You can only run 1 instance of apt...
and software center is based on apt.

---

### Post by shibu_sawyer on 2011-08-21
ya i can understand.. but still that problem exists.. same apt-get exit prob..
but as far as i know there's no other instances of this is running.

---

### Post by realzippy on 2011-08-21
..maybe you have a look on synaptic when installing software and
having trouble with software center.
I have the idea that software center isn't as mature...

---

### Post by shibu_sawyer on 2011-08-21
I Don know whats going on with my ubuntu.. now all of a sudden,s/w center works.

---

### Post by realzippy on 2011-08-21
Disable the update-notifier,there is no need to check for daily updates,and if it decided to start other apt apps won't work.

---

### Post by shibu_sawyer on 2011-08-21
> **realzippy said:**
> Disable the update-notifier,there is no need to check for daily updates,and if it decided to start other apt apps won't work.
Thank you for your help.. really appreciated..

:-) thank you once again

---

### Post by realzippy on 2011-08-21
So,if problem solved,you might set thread as solved also. (threadtools)

---

