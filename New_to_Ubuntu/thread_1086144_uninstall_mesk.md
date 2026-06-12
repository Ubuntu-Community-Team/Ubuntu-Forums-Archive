---
title: "uninstall mesk"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by omeriko on 2009-03-03
hi,

I installed Mesk. I don't really remember how. and now I want to remove it.
it doesn't show on the "add/remove" menu nor in synaptic.
it does however show on the "Applications Menu" for use.

anyone knows what to do?
I still don't really understand how the whole installation/removal thing works on linux.

thanks.

---

### Post by llamabr on 2009-03-03
How did you install it?  With synaptic?  It doesn't show up in my repositories.

In any case, you can open a terminal and type:

```
sudo apt-get remove mesk
```

---

### Post by erudite on 2009-03-03
I believe that you need to compile the same version that you have installed on your system already.

Then type make uninstall and this should hopefully remove the program.

As it does not appear in synaptic I am assuming you compiled it yourself.  If you need any further assistance feel free to ask.

---

### Post by omeriko on 2009-03-04
well, thanks guys, that was fast.

> **llamabr said:**
> 
```
sudo apt-get remove mesk
```

this didn't work.

> **erudite said:**
> I believe that you need to compile the same version that you have installed on your system already.

as for erudite's idea, I downloaded mesk-0.3.2 and I guess I found somewhere how to install it.

how do I compile it?

---

### Post by erudite on 2009-03-04
unzip it first then cd to the directory that you have it stored it.

Then type 
"./configure"
If there are any errors you may need to do something else.  Then type "make".

If all this goes without a hitch type "make uninstall".

---

### Post by omeriko on 2009-03-04
thanks man, this worked wonderfully.

by the way, is there any good website where I can learn how to do this myself without asking for help every time I need to install something that is not in the repositories?

---

### Post by erudite on 2009-03-04
You're welcome.  

I've never really used a website before to be honest.  

You already know how to install and how to uninstall now...you're half way there.

If for example the program is in package manager but you want to use an updated version and you get an error trying to compile you can use "build-dep".

sudo apt-get build-dep program-name

This will install all the dependencies and it should compile.

I don't think you should have a problem in future but feel free to scour the internet for a website.

Don't forget to mark this thread as solved under thread tools at the top.  Thanks

---

### Post by omeriko on 2009-03-04
> **erudite said:**
> 
Don't forget to mark this thread as solved under thread tools at the top.  Thanks

I don't have "mark as solved" under "thread tools"

---

### Post by erudite on 2009-03-04
My mistake it's been a while since I've been here.  They appear to have disabled it for a while.

---

