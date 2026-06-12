---
title: "Make Live CD - Would This Method Work?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by cat2005 on 2009-09-04
I want to make a Live CD based upon my current Ubuntu 904 hard drive installation.
 
I have been scratching my head. Do you think this approach would work? Do you know of easier ways? I am not very tech smart so it would have to be simple.
 
My idea:
 
1) make list of all installed packages via:
dpkg --get-selections > installed-packages
 
2) use reconstructor ([http://blogs.techrepublic.com.com/opensource/?p=623](http://blogs.techrepublic.com.com/opensource/?p=623)) and in reconstructor's own terminal window, re-install those packages listed from step 1 via:
sudo dpkg --set-selections < installed-packages
 
3) Proceed with reconstructor per its directions.
 
Could it be this simple? Or did I not think my cunning plan all the way through? Also, in step 2, how would I tell it where to find the list (i.e, how would I tell it the proper folder inside which it should look)?
 
 
Thanks.

---

### Post by ayenack on 2009-09-04
Take a look at remastersys. Here's a tutorial on using it.

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Also shows you how to install it.

---

