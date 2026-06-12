---
title: "[SOLVED] trouble remebering a simple command"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-01-01
Hello

Thanks for reading

Quite simply I am looking to install itunes - ( i know its rubbish 'ra ra ra') - but its for a friend who just bought an ipod and wants to connect it, but his computer broke.

I have downloaded it to my desktop, but nothing happens when i right click and run in wine, so my question is -

what command can i use to install itunes through wine via the terminal - to see is there are any errors (which im sure there will be).

Or on the other hand, if anyone knows of a way which works - installing itunes - that is, then i'll try that.

cheers again

---

### Post by taurus on 2009-01-01
Applications -> Accessories -> Terminal
```
cd ~/Desktop
wine *filename.exe*
```

---

### Post by phantomjoker on 2009-01-01
That worked, now i have the problem that the error reads
> 
Trying to load PE image for unsupported architecture (AMD-64)
Trying to load PE image for unsupported architecture (AMD-64)
wine: could not load L"Z:\\home\\mckenzie\\Desktop\\iTunes64Setup.exe": Bad EXE format for 


but i realized i am trying to install an odd version, so will download the xp verion an have another go...

---

### Post by phantomjoker on 2009-01-01
That worked, now i have the problem that the error reads
> 
Trying to load PE image for unsupported architecture (AMD-64)
Trying to load PE image for unsupported architecture (AMD-64)
wine: could not load L"Z:\\home\\mckenzie\\Desktop\\iTunes64Setup.exe": Bad EXE format for 


but i realized i am trying to install an odd version, so will download the xp verion an have another go...

---

### Post by phantomjoker on 2009-01-01
yes - it was the version! working...

---

### Post by phantomjoker on 2009-01-01
I take that back, it did not install, and my system began going mental - so that ideas out the window.

---

