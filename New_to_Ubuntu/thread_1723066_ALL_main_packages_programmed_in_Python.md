---
title: "ALL main packages programmed in Python?"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by ironic.demise on 2011-04-06
I read somewhere on the Ubuntu page that all of the main packages were programmed in Python.

I used to think that Python was a limited programming language but honestly, it seems to be quite popular and powerful, would it be a good place to start programming?

---

### Post by TeoBigusGeekus on 2011-04-06
If you've never programmed before, it is a good place to start.
If you have previous programming experience, skip it and go to your final destination: C.

---

### Post by ironic.demise on 2011-04-06
> **TeoBigusGeekus said:**
> If you've never programmed before, it is a good place to start.
If you have previous programming experience, skip it and go to your final destination: C.

No, never programmed before.
Would you suggest skipping to C once I'm skilled in Python?
ARE all Natty packages written in Python?

---

### Post by TeoBigusGeekus on 2011-04-06
> **ironic.demise said:**
> No, never programmed before.
Would you suggest skipping to C once I'm skilled in Python?
Yes.

> **ironic.demise said:**
> ARE all Natty packages written in Python?
No idea - I'm not an ubuntu user.

---

### Post by rosencrantz on 2011-04-06
OK. I'd doubt all Natty packages are Python.
At least the Linux kernel is C and will probably stay C for a very long time.
The difference between C and Python is that C is a compiled and Python is an interpreted language, which makes Python much easier to begin with: you can execute scripts right away and don't need to worry about compilers, include directories etc.
The downside is that Python is slower as everything has to be run through the interpreter - you 'execute' a text file while compiled C is binary. 
Having limited programming experience with both C and Python, I have to say C is a pain in the posterior. I only use it for large-scale number crunching.
Learn Python. Have fun.
With a bit of programming experience you can still decide later whether you need another language.

---

### Post by Joe of loath on 2011-04-06
Nope, few Ubuntu packages are written in Python.

The reason being, it's a high level language, and just too damn slow for userspace stuff. C and C++ is mostly used instead.

---

### Post by tgm4883 on 2011-04-06
> **Joe of loath said:**
> Nope, few Ubuntu packages are written in Python.

The reason being, it's a high level language, and just too damn slow for userspace stuff. C and C++ is mostly used instead.

Do you mean kernelspace stuff? There are plenty of userspace applications written in Python (and likely perl, ruby, C, etc)

---

### Post by Paqman on 2011-04-06
> **ironic.demise said:**
> 
ARE all Natty packages written in Python?

Nope. Some are, some aren't.

---

### Post by rosencrantz on 2011-04-06
> **tgm4883 said:**
> There are plenty of userspace applications written in Python (and likely perl, ruby, C, etc)
Yep, at least for KDE it is a beautiful jumble. So it's easy to integrate your Python stuff into major DE's like Gnome and KDE as most KDE/gnome libraries have well-established Python front ends.

But that's probably still a long way off.
Let's do some
```
#!/usr/bin/python
print 'Hello, World!'
```
first ;-)

---

### Post by CoffeeRain on 2011-04-27
A great help to get to know Python is the Google python class. If you look on Youtube for Google python class, you should find it. It's a video of a class they did a while ago. If you go to code.google.com/edu/google-python-class, you should find the excersises that they worked on. You will get to know the basics of lists and strings and dictionaries plus writing scripts to do cool things!

---

