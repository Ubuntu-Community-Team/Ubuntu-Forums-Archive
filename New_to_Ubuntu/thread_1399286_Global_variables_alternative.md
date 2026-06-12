---
title: "Global variables alternative"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by newport_j on 2010-02-05
I hope that it is okay to start this new thread. It seems that global variables are strongly rejected by the c programming community, then I ask what is the alternative?

When you have to keep track of time and it goes through many subprograms, how do you do it without global variables? 

There just seems no other way.

Newport_j

---

### Post by da burger on 2010-02-05
I'm not sure but I think the idea is to pass the info you want to use in the other function to it as an argument. Not sure if that makes sense but I hope it does.

---

### Post by tom4everitt on 2010-02-05
If you have a function X calling function Y and function Y need som input from X, it is much better to let Y have that input through an argument rather than through a global variable (which some other function might accidentally changed). 

This doesn't mean you should never use a global variable, in your case I think it's the thing to do. But don't do if its not necessary :)

---

