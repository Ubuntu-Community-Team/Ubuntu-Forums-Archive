---
title: "Problem"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Hadso on 2009-01-29
I tired to install Open Office, but I couldn't 'cos my computer freeze. 
From this moment, I cant install nothing. 
For example, when I tried to update my Xubuntu a message says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I have paste the code in the Konsole, but I still having this. 

What can I do? This is my first time with Linux. 
Please, show some merci. 

Thank you very much!

---

### Post by sisco311 on 2009-01-29
run the command as root:
```
sudo dpkg --configure -a
```

---

### Post by avtolle on 2009-01-29
From the terminal```
sudo dpkg --configure -a
```

---

### Post by mrbiggbrain on 2009-01-29
FOr future refrence, to get better answers, and assist the fourums, more descriptive names would be better. 

thread names such as "problem" are verry undescriptive, and the person comes into the thread totaly blind, or for many people not at all. a better name would have been "dpkg --configure -a returns errors"

how this helps:

Those looking for answers can find them, instead of looking through thousands of threads named "problem".

those looking to answer threads can easily pick yours off of the list (some problems oyu know exactly what the person si doing wrong before even opening the thread should there title be good anough)

it keeps confusion low instead of 20-30 "problem" threads on every page, and in your list so when you check up on threads you know which your getting

---

### Post by Hadso on 2009-01-29
Thanks, but I still having the problem.

---

### Post by Hadso on 2009-01-29
I have been able to do that. 
Know it said that:

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

I think it 's the openoffice instalation that I couldn't finish. 
How can I use the "Broken"?

Thanks!

---

### Post by sisco311 on 2009-01-29
> **Hadso said:**
> I have been able to do that. 
Know it said that:

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

I think it 's the openoffice instalation that I couldn't finish. 
How can I use the "Broken"?

Thanks!

There should be a menu option in Synaptic for that. Something like "Fix Broken Packages".
Or use the terminal:
```
sudo apt-get install -f
```

---

### Post by Hadso on 2009-01-29
It's done. Thanks.

---

