---
title: "can't open matlab figure file and .mat variables"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by aachen on 2010-01-30
Hi all,

I have installed matlab R2009b in ubuntu and when I try to double click .fig files it gives me error that 'There is no application installed for XFig image files'. I cant open it also from matlab open menu. Why is it ? Also I can't open .mat variables by directly double clicking it like I used to do it in Windows.

---

### Post by freak42 on 2010-01-30
try right-clicking the file -> properties -> open with

and locate & choose the matlab binary

---

### Post by aachen on 2010-01-31
Thanks for your reply but this doesn't help. I located the binary usr/local/matlab/bin/matlab. I think the .mat and .fig extensions are not associated with matlab yet. In windows double clicking .mat and .fig always opens matlab and loads the variable and figure automatically. But in ubuntu first I need to start matlab first and load the variables from matlab command line. Why is it ?

---

### Post by OpenMouth_os on 2011-05-30
I have the same problem. cant open fig files except from within matlab. tried linking the fig files to the matlab executable, but it just opens matlab without opening the actual figure.
don't know what to do.

---

### Post by aaigner on 2012-03-22
Hi all!

Try to right click the *.fig - file --> "Open with Other Application" --> Use a custom command --> matlab -desktop -r "open(%f)"

Cheers
Andreas

---

