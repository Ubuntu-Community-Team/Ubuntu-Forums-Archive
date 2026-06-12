---
title: "Point to a file with terminal to run a .py python file"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Rob_Riethmuller on 2009-04-03
Hi all

How can I point to python file .py in a directory other than my home directory /home/rob/ in the Terminal and run the module

While the .py file is in my home directory, then at the terminal prompt python hw.py runs the module no problems.

Now if the same file is put in say /home/rob/Python/Python_Programs then I have a problem.If I type in 
python /home/rob/Python/Python_Programs -hw.py

the bash reply is "this is only a directory cannot continue"
What is the correct syntax?

Can you help please
Cheers
Rob R

---

### Post by WhiskyChris on 2009-04-03
Try using the full path to the file:

```
python /home/rob/Python/Python_Programs/hw.py
```

Does that work?

---

### Post by abrussak on 2009-04-03
It would be

python /home/rob/Python/Python_Programs/hw.py

as you need to point to the .py source code. Anything with a - will be read as a command line option/argument....so it only sees the folder and doesn't understand what to do

---

### Post by Rob_Riethmuller on 2009-04-03
Hi Guys,

That does the trick nicely. Thanks for the quick replies

Cheers
Rob R

---

