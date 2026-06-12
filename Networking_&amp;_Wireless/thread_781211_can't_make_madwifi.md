---
title: "can't make madwifi"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by takendal on 2008-05-04
I have an Acer Aspire 5520-5912 and am trying to build madwifi on it.  Problem is, when I do a "make" I get a bunch of compile errors because it can't open any of the normal .h files..  For example, stdio.h.  

What do I need to install to get these on there?  

I'm using the new 8.04, if it matters. 

Thanks

---

### Post by takendal on 2008-05-04
nm, got it..  sudo apt-get install build-essential

That got it all taken care of :)

---

### Post by WakkiTabakki on 2008-05-04
Have you installed the package build-essential? 

Otherwise, try posting the output from make.. Having the details makes it a lot easier to help.

/N

Edit: ahhh, just seconds late :P

---

