---
title: "Package dependencies cannot be resolved"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by ahmedshareef on 2011-05-31
I want to write from right to left language.. Arabic and Maldivian Language..
so I'm trying to install CTL from the Ubuntu  Software Center. I click "Install," and as soon as it starts loading, it  gives me this error message: [INDENT] 	Quote:
 	 	 		 			 				Package dependencies cannot be resolved

This error could be caused by required additional software packages  which are missing or not installable. Futhermore there could be a  conflict between software packages which are not allowed to be installed  at the same time. 			 		 	 	 
[/INDENT]How do I find out what software packages I am missing? 

I have Ubuntu 11.04 Sabily Badr.

Thanks for your help, 

-

---

### Post by scottstensland on 2011-05-31
open up a terminal window

    Ctrl-Alt-t

then issue

    sudo apt-get -f install

which will try to fix a broken package install
you may have lingering about

once squared away - then try your original package install

---

### Post by ahmedshareef on 2011-05-31
> **scottstensland said:**
> open up a terminal window

    Ctrl-Alt-t

then issue

    sudo apt-get -f install

which will try to fix a broken package install
you may have lingering about

once squared away - then try your original package install
thanks scottstensland,
but still am unable to enable CTL Support..
hope to see more assistance..
thanks again

---

