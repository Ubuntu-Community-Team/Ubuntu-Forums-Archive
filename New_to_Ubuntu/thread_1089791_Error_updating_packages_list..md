---
title: "Error updating packages list."
date: 2009-03-07
forum: New to Ubuntu
---

### Post by myolbug on 2009-03-07
Okay, I am starting to have a string of failures.  The next one up to bat is that now the Symantic Package Manager isn't working.  Error message:
E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

Now what?  I think my computer is dying!

---

### Post by myolbug on 2009-03-07
When I go into a te4rminal an run this command, it just goes down a line and gives me this: > and the cursor.
It appears to be waiting or looking for something.

---

### Post by simtaalo on 2009-03-07
so what happens when you run 

```
dpkg --configure -a
```

in a terminal?

for future reference please use a descriptive thread title, it will get you help much quicker. maybe something like "problem with synaptic" would have been better here than "wtf".

---

### Post by kellemes on 2009-03-07
from a terminal window, type..
```
sudo dpkg --configure -a
```

---

### Post by thtrgremlin on 2009-03-07
the '>' means there was something like a quote or tic that did not get closed. Are you typing in exactly:```
sudo dpkg --configure -a
```

---

### Post by hockeyhead019 on 2009-03-07
umm first off try and rename the thread so people will be able to help you easier because nobody has any idea the title wtf will refer to haha 

now to the important stuff... try to run the command
```
 sudo apt-get install -f
```

as this will repair any broken packages which could be causing the problem

also you can search the problem on google as i just did and found a couple threads dealing with similar problems just to see if they help

---

### Post by utnubuuser on 2009-03-07
Other threads this appeared in seemed to find a solution by re-installing synaptic

---

### Post by myolbug on 2009-03-07
First off, I agree that I should have titled it correctly.

Second, I got it working, though I don't know what it actually took to do it.  I first ran:  sudo apt-get install -f which told me that the synaptic wasn't working right, so I then ran: sudo dpkg --configure -a.  This is the weird part;  I cut and pasted it right from the terminal back into the terminal and it didn't work before, but now it does.

Oh well, it is working now.  Now I just need to figure out the rest of the problems...:(

SOLVED at least this one.

---

### Post by Kareeser on 2009-03-07
It didn't work before because you had a little apostrophe before :)

Congrats! We'll be here :)

---

### Post by kellemes on 2009-03-07
> **myolbug said:**
> First off, I agree that I should have titled it correctly.

Second, I got it working, though I don't know what it actually took to do it.  I first ran:  sudo apt-get install -f which told me that the synaptic wasn't working right, so I then ran: sudo dpkg --configure -a.  This is the weird part;  I cut and pasted it right from the terminal back into the terminal and it didn't work before, but now it does.

Oh well, it is working now.  Now I just need to figure out the rest of the problems...:(

SOLVED at least this one.

```
E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.
```

The error-message told you how to handle this..
Glad you did eventually.

---

### Post by bapoumba on 2009-03-07
Thread title edited and solved tag added.

---

### Post by myolbug on 2009-03-07
> **kellemes said:**
> ```
E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.
```

The error-message told you how to handle this..
Glad you did eventually.


kellemes,
I understand what you are saying and I am pretty sure you didn't mean to sound sarcastic.  However, in regards to what you said, I ran the command EXACTLY as written, as I just did a copy/paste from the error message and nothing happened, as I stated earlier.  Nonetheless, it is fixed.

---

### Post by myolbug on 2009-03-07
> **bapoumba said:**
> Thread title edited and solved tag added.

How do I add the solved tag.  I would like to know for the future.  DO I just go into Tags and type solved?  Sorry if I sound dumb.

---

