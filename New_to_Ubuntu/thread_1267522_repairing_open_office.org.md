---
title: "repairing open office.org"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by Thocrun on 2009-09-15
I just want some code so I can repair openoffice.org through the terminal, since my web page wizard doesn't work, I already reported it.

---

### Post by Geoff918 on 2009-09-15
I'll tell you to wait for other replies, but I'll give you one of the more extreme answers if someone else can't help you better.

From CLI (Terminal) enter the following:

sudo aptitude remove (program name--in this case OpenOffice.org; check to see all the parts are selected in the resulting removal screen)

then;

sudo aptitude purge (same as above)

This will remove all custom settings, etc. associated with your install.

Then you can enter:

sudo aptitude install (package name--OpenOffice.org or whatever).

This would get you back to the base install with the fewest hiccups. If you'd rather wait and see if someone may provide a more surgical answer, by all means, do. If that becomes frustrating go ahead and try the above.

---

### Post by Thocrun on 2009-09-15
Thanks for the input, I'll probably wait for now since I think that wizard was the only one affected.

---

### Post by Bölvaður on 2009-09-15
Would you consider repairing by upgrading to a newer version or do you just want to reinstall (less likely to work).

Upgrade
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")
Note that this is for 8.10 (intrepid) so if you have 9.04 you will have to change intrepid to jaunty in the code. (deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) _jaunty_ main) 


Reinstall:
open the terminal (applications &#8594; accessories &#8594; terminal)
```
sudo apt-get remove openoffice.org
sudo apt-get install openoffice.org 

```

---

### Post by Thocrun on 2009-09-15
I am going to try to repair it first, thanks for the help.

---

