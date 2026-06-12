---
title: "USPS printing lables..."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Commander_Bob on 2009-01-12
I am trying to print labels using USPS click-N-ship but when it tries to load the label Firefox freaks out. It keeps loading something for like 1/4 of a second then stops for about 1/4 of a seconds and keeps doing this. It is using the Internet a lot but nothing ever happens. Has anyone had this before? I am on Ubuntu 8.10.

Thanks,
Justin

---

### Post by embeddedatom on 2009-02-15
These are the steps I used to print labels from the USPS Click-N-Ship website with Ubuntu.

1) Download and install the Adobe Reader for linux.

2) In the Firefox toolbar:
   Edit->Preferences->Applications
   Scroll to the PDF document field and click the dropdown menu.
   Select 'use other' and navigate to the location of the Adobe Reader acroread executable.
   Mine was located at:  /opt/Adobe/Reader8/bin/acroread


This allowed the USPS sample domestic form to call acroread from Firefox and print the label just like on my windows machine. 

Richard

---

### Post by Commander_Bob on 2009-02-15
Thank you! It works perfectly now. I had PDF files set to ask me but now it works. Also I just had to enter acroread not the full path.

Thanks again,
Justin

---

### Post by atrpunk on 2011-03-08
Thanks! I had this same problem using Ubuntu 10.10 w/ Adobe Reader 9.1. 

I am new to Ubuntu and was wondering why it kept reloading but never printed. The above steps worked :P

---

### Post by csmccarron on 2011-09-26
Thanks!  Works perfectly! ;)

---

