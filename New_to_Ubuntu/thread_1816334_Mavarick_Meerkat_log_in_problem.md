---
title: "Mavarick Meerkat log in problem"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by TWYDALE on 2011-08-01
[SIZE=2]Hello everybody, Firstly many thanks for your warm welcome to the forum. I`m a silver surfer of many summers and have been happily using "Ubuntu" ( Maverick Meerkat ) for the past six months. On Saturday after much nagging from the update manager I decided to install the recommended downloads as per update managers advice. Now MISERY! the system refuses to let me login. It keeps returning me to the login screen and displays the following message " _The configuration defaults for Gnome manager have not been installed correctly. Please contact your computer administrator"_. What on earth does this mean? 
More to the point what can I do to correct it? Can anyone help me get back to sanity? 
One final request please keep the jargon in your replies to a minimum! Thanks![/SIZE]

---

### Post by jerrrys on 2011-08-02
did you by chance mean gnome **power** manager?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+configuration+defaults+for+Gnome+power+manager+have+not+been+installed+correctly.+Please+contact+your+computer+administrator&as_qdr=m6&sa=Google+Search&lang=en#1076](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+configuration+defaults+for+Gnome+power+manager+have+not+been+installed+correctly.+Please+contact+your+computer+administrator&as_qdr=m6&sa=Google+Search&lang=en#1076)

---

### Post by TWYDALE on 2011-08-03
> **jerrrys said:**
> did you by chance mean gnome **power** manager?

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+configuration+defaults+for+Gnome+power+manager+have+not+been+installed+correctly.+Please+contact+your+computer+administrator&as_qdr=m6&sa=Google+Search&lang=en#1076](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+configuration+defaults+for+Gnome+power+manager+have+not+been+installed+correctly.+Please+contact+your+computer+administrator&as_qdr=m6&sa=Google+Search&lang=en#1076)
Hello everybody, Many thanks to jerrys for pointing me in the right direction in solving my login problem with Maverick Meerkat. You were correct in suspecting it was a full up files problem. My next question is how can I free up some more space? So that this doesn`t keep happening. Thanks again!

---

### Post by jerrrys on 2011-08-03
**Remove all the packages** 	from /var/cache/apt/archives and /var/cache/apt/archives/partial 	folders:  	  
[LIST]
[*]sudo apt-get clean
[/LIST]
 
[LIST]
[*]**Remove 	all expired packages** from /var/cache/apt/archives and 	/var/cache/apt/archives/partial that are no longer available for 	download:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoclean
[/LIST]
 "*Not available for download*" does not mean the user should save them - normally these files have been replaced or are no longer needed.  
 
[LIST]
[*]**Remove unneeded dependencies** 	which are no longer needed:  	
[/LIST]
 
[LIST]
[*]sudo apt-get autoremove
[/LIST]

---

